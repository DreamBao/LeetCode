# 227. Basic Calculator II
Basic Calculator II

## Code
    public class Solution {
        public int Calculate(string s) {
            int pre = 0, curr = 0, sign = 1, op = 0, num = 0;
        
            for (int i = 0; i < s.Length; i++) {
                if (char.IsDigit(s[i])) {
                    num = num * 10 + (s[i] - '0');
                    if (i == s.Length - 1 || !char.IsDigit(s[i + 1])) {
                        curr = (op == 0 ? num : (op == 1 ? curr * num : curr / num));
                    }

                } else if (s[i] == '*' || s[i] == '/') {
                    op = (s[i] == '*' ? 1 : -1);
                    num = 0;

                } else if (s[i] == '+' || s[i] == '-') {
                    pre += sign * curr;
                    sign = (s[i] == '+' ? 1 : -1);
                    op = 0;
                    num = 0;
                }
            }

            return pre + sign * curr;
        }
    }