### Personalized ID Generator WITH 5 Characters

 - Create a Class

```C#

        public static class SecureIdGenerator
        {
            private const string Chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"; //characters used for generate ID 

            public static string GenerateId(int length = 5)
            {
                var data = RandomNumberGenerator.GetBytes(length);
                var sb = new StringBuilder(length);

                foreach (byte b in data)
                {
                    sb.Append(Chars[b % Chars.Length]);
                }

                return sb.ToString();
            }
    }
```



 - Call it as a string
```C#
 string IDTest = SecureIdGenerator.GenerateId();
````


### Timer with personalized refresh time.

 - Declare System Timer

```C#

using System.Timers; 

private System.Timers.Timer timer3; //declaration of timer

private double time3; //variable to control elapsed time

// Timer for real-time update
timer3 = new System.Timers.Timer(50); // 20Hz = 50ms
timer3.Elapsed += Void_example; //this line calls this void every 50ms
timer3.Start(); // Start Timer


	private void Void_example(object sender, ElapsedEventArgs e)
	{
		// Simulate getting new force values
		double newForce1 = 10 * Math.Sin(time3); 
		double newForce2 = 8 * Math.Cos(time3 * 0.8);
	
		this.BeginInvoke((Action)(() =>
	{                     
	 //put here something to execute at high speed
	   
	}));
	
	 time3 += 0.05; // Increase time (50 ms)
	 //this variable increase value could be used to simulate a chronometer inside the code to make simple math operations based on elapsed time;
	 
	
	 }
```

### Rotated Label

 - Create a Class 

``` C#
public class RotatedLabel: System.Windows.Forms.Label
{
	public int RotateAngle { get; set; } = 0; // Default to no rotation
	public string NewText { get; set; } = "";

	protected override void OnPaint(PaintEventArgs e)
	{
		// Set AutoSize to False and adjust the control size to prevent clipping
		this.AutoSize = false;

		Brush b = new SolidBrush(this.ForeColor);
		e.Graphics.TranslateTransform(this.Width / 2, this.Height / 2); // Move origin to center
		e.Graphics.RotateTransform(this.RotateAngle); // Apply rotation
		e.Graphics.DrawString(this.NewText, this.Font, b, 0f, 0f); // Draw the string at the new origin
		base.OnPaint(e);
		e.Graphics.ResetTransform(); // Reset transformation matrix for other controls
	}
}

```

 - Put it in the constructor
```C#
RotatedLabel myRotatedLabel = new RotatedLabel();
myRotatedLabel.Font = new Font("Arial", 16, System.Drawing.FontStyle.Bold);
myRotatedLabel.NewText = "Hello World";
myRotatedLabel.ForeColor = System.Drawing.Color.Green;
myRotatedLabel.RotateAngle = -90; // Rotate 90 degrees counter-clockwise
myRotatedLabel.Size = new System.Drawing.Size(1200, 900); // Adjust size to accommodate rotated text
this.Controls.Add(myRotatedLabel);
```


 
## Delay without freeze system - Task Delay

Declare a function with "async" Option, use the Task.Delay(); inside of it 


``` C#
        public async void Test_ClickAsync(object sender, EventArgs e)
        {

            await Task.Delay(TimeSpan.FromMilliseconds(100)); 

            await Task.Delay(TimeSpan.FromMicroseconds(1000));

         	await Task.Delay(TimeSpan.FromSeconds(1)); //using with seconds

            await Task.Delay(TimeSpan.FromMinutes(1));  // using with minutes

            await Task.Delay(TimeSpan.FromHours(1)); //

        }




 

