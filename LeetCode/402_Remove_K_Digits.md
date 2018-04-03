# 402. Remove K Digits
Remove K Digits

## Code
    public class Solution {
        public string RemoveKdigits(string num, int k) {
            int digits = num.Length - k;
            char[] stk = new char[num.Length];
            int top = 0;
            for (int i = 0; i < num.Length; ++i) {
                char c = num[i];
                while (top > 0 && stk[top-1] > c && k > 0) {
                    top -= 1;
                    k -= 1;
                }
                stk[top++] = c;
            }
            int idx = 0;
            while (idx < digits && stk[idx] == '0') idx++;
            return idx == digits? "0": new string(stk, idx, digits - idx);
        }
    }