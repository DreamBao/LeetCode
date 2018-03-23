# 386. Lexicographical Numbers
Lexicographical Numbers

## Code
    public class Solution {
        public IList<int> LexicalOrder(int n) {
            List<int> res = new List<int>();
            int cur = 1;
            for (int i = 1; i <= n; i++) {
                res.Add(cur);
                if (cur * 10 <= n) {
                    cur = cur * 10;
                } else if (cur % 10 != 9 && cur + 1 <= n) {
                    cur++;
                } else {
                    while ((cur / 10) % 10 == 9) {
                        cur = cur / 10;
                    }
                    cur = cur / 10 + 1;
                }
            }
            return res;
        }
    }