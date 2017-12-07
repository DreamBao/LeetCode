# 78. Subsets
Subsets


## Code
    public class Solution {
        public IList<IList<int>> Subsets(int[] nums) {
            IList<IList<int>> result = new List<IList<int>>();
            List<int> temp = new List<int>();
            for(int k = 0; k <= nums.Length; k ++)
                GetSubsets(result, temp, nums, k, 0, 0);
            return result;
        }
        
        
        public void GetSubsets(IList<IList<int>> result, List<int> temp, int[] n, int k, int num, int count) {
            if(count == k) {
                result.Add(new List<int>(temp));
                return;
            }
            for(int i = num; i < n.Length; i ++) {
                temp.Add(n[i]);
                GetSubsets(result, temp, n, k, i + 1, count + 1);
                temp.RemoveAt(temp.Count - 1);
            }
        }
    }