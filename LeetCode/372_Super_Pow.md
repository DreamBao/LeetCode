# 372. Super Pow
Super Pow

## Code
    public class Solution {
        
        public int M = 1337;
            
        public int SuperPow(int a, int[] b) {
            a %= M;
            int result = 1;
            for (int i = b.Length - 1; i >= 0; i--) {
                result = result * NewPow(a, b[i]) % M;
                a = NewPow(a, 10);
            }
            return result;
        }

        public int NewPow(int a, int b) {
        int result = 1;
            while (b != 0) {
                if (b % 2 != 0)
                    result = result * a % M;
                a = a * a % M;
                b /= 2;
            }
            return result;
        }
    }