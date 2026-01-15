Personalized ID Generator WITH 5 Characters

```C#
Class: 

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



Call it as string
```C#
 string IDTest = SecureIdGenerator.GenerateId();
````

Timer with personalized refresh time.

```C#
using System.Timers;

private System.Timers.Timer timer3; //declaration of timer

private double time3;

// Timer for real-time update
timer3 = new System.Timers.Timer(50); // 20Hz = 50ms
timer3.Elapsed += Void_example; //this line calls this void every 50ms
timer3.Start(); 


	private void Void_example(object sender, ElapsedEventArgs e)
	{
		// Simulate getting new force values
		double newForce1 = 10 * Math.Sin(time3); 
		double newForce2 = 8 * Math.Cos(time3 * 0.8);
	
		this.BeginInvoke((Action)(() =>
	{                     
	 //put here something to execute in high speed
	   
	}));
	
	 time3 += 0.05; // Increase time (50 ms)
	 //this variable increase value could be used to simulate a chronometer inside of code to make simple math operations based on elapsed time;
	 
	
	 }
```


 





 

