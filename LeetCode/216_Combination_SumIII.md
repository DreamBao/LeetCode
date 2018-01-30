# 216. Combination Sum III
Combination Sum III

## Code
    public class Solution {
        public IList<IList<int>> CombinationSum3(int k, int n) {
            IList<IList<int>> res = new List<IList<int>>();
            Combination(res, new List<int>(), k, 1, n);
            return res;
        }
        
        public void Combination(IList<IList<int>> res, List<int> comb, int k,  int start, int n) {
            if (comb.Count == k && n == 0) {
                List<int> li = new List<int>(comb);
                res.Add(li);
                return;
            }
            for (int i = start; i <= 9; i++) {
                comb.Add(i);
                Combination(res, comb, k, i + 1, n - i);
                comb.RemoveAt(comb.Count - 1);
            }
        }
    }