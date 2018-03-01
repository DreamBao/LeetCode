# 306. Additive Number
Additive Number

## Code
    public class Solution {
        public bool IsAdditiveNumber(string num) {
            int n = num.Length;
            for (int i = 1; i < n; i ++) {
                for (int j = i + 1; j < n; j ++) {
                    long a = ParseLong(num.Substring(0, i));
                    long b = ParseLong(num.Substring(i, j - i));
                    if (a == -1 || b == -1) continue;
                    if (Dfs(num.Substring(j), a, b))   return true;
                }
            }
            return false;
        }  
        
        public bool Dfs(string s, long a, long b) {
            if (s.Length == 0)    return true;
            
            for (int i = 1; i <= s.Length; i ++) {
                long c = ParseLong(s.Substring(0, i));
                if (c == -1)
                    continue;
                if (c - a == b && Dfs(s.Substring(i), b, c)) {
                    return true;
                }
            }
            return false;
        }
        
        public long ParseLong(string s) {
            if (!(s =="0") && s.StartsWith("0"))    return -1;
            long result = -1;
            long.TryParse(s, out result);
            return result;
        }
    }