# 93. Restore IP Addresses
Restore IP Addresses


## Code
    public class Solution {
        public IList<string> RestoreIpAddresses(string s) {
            IList<string> result = new List<string>();
            string str = "";
            for (int a=1; a<=3; a++)
            for (int b=1; b<=3; b++)
            for (int c=1; c<=3; c++)
            for (int d=1; d<=3; d++)
                if (a+b+c+d == s.Length) {
                    int num1 = int.Parse(s.Substring(0, a));
                    int num2 = int.Parse(s.Substring(a, b));
                    int num3 = int.Parse(s.Substring(a+b, c));
                    int num4 = int.Parse(s.Substring(a+b+c, d));
                    if (num1<=255 && num2<=255 && num3<=255 && num4<=255)
                        if ((str=num1+"."+num2+"."+num3+"."+num4).Length == s.Length+3)
                            result.Add(str);
                }    
            return result;
        }
    }