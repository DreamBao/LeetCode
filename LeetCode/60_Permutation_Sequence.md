# 60. Permutation Sequence
Permutation Sequence

## Code
    public class Solution {
        public string GetPermutation(int n, int k) {
            int t = 1;
            string result = "";
            List<int> allNum = new List<int>();
            for(int l = 1; l <= n; l++) {
                allNum.Add(l);
            }
            int tempSum = k - 1;
            for(int j = n; j > 0; j--) {
                t = 1;
                for(int i = 1; i < j; i++) {
                    t *= i;
                }
                int num = tempSum / t;
                result += allNum[num];
                allNum.RemoveAt(num);
                tempSum = tempSum % t;
            }
            return result;
        }
    }