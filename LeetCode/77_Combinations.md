# 77. Combinations
Combinations


## Code
    public class Solution {
        public IList<IList<int>> Combine(int n, int k) {
            IList<IList<int>> result = new List<IList<int>>();
            List<int> temp = new List<int>();
            GetCombine(result, temp, n, k, 1, 0);
            return result;
        }
        
        public void GetCombine(IList<IList<int>> result, List<int> temp, int n, int k, int num, int count) {
            if(count == k) {
                result.Add(new List<int>(temp));
                return;
            }
            for(int i = num; i <= n; i ++) {
                temp.Add(i);
                GetCombine(result, temp, n, k, i + 1, count + 1);
                temp.RemoveAt(temp.Count - 1);
            }
        }
    }