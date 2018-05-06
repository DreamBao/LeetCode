# 481. Magical String
Magical String

## Code
    public class Solution {
        public int MagicalString(int n) {
            if (n <= 0) return 0;
            if (n <= 3) return 1;
            int res = 1, head = 2, tail = 3, num = 1;
            List<int> v = new List<int>(){1, 2, 2};
            while (tail < n) {
                for (int i = 0; i < v[head]; ++i) {
                    v.Add(num);
                    if (num == 1 && tail < n) ++ res;
                    ++ tail;
                }
                num ^= 3;
                ++ head;
            }
            return res;
        }
    }