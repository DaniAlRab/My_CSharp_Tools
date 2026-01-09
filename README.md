Personalized ID Generator WITH 5 Characters

Class: 

        public static class SecureIdGenerator
        {
            private const string Chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";

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





call it as string

 string IDTest = SecureIdGenerator.GenerateId();

