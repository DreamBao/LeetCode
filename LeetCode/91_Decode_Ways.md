# 91. Decode Ways
Decode Ways


## Code
    public class Solution {
        public int NumDecodings(string s) {
            if(s.Length == 0 || s[0] == '0')
                return 0;
            int d1 = 1, d2 = 1;
        
            for (int i = 1; i < s.Length; i++) {
                if (s[i] == '0') d1 = 0;
                if (s[i - 1] == '1' || s[i - 1] == '2' && s[i] <= '6') {
                    d1 = d2 + d1;
                    d2 = d1 - d2;
                }
                else {
                    d2 = d1;
                }
            }
            return d1;
        }
    }