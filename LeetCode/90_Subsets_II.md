# 90. Subsets II
Subsets II


## Code
    public class Solution {
        public IList<IList<int>> SubsetsWithDup(int[] nums) {
            Array.Sort(nums);
            IList<IList<int>> result = new List<IList<int>>();
            List<int> temp = new List<int>();      
            AddSubset(result, temp ,nums, 0);
            return result;
            
        }
        
        public void AddSubset(IList<IList<int>> result, List<int> temp, int[] nums, int n) {
            result.Add(new List<int>(temp));
            for(int i = n; i < nums.Length; i++) {
                if(i == n || nums[i] != nums[i - 1]) {
                    temp.Add(nums[i]);
                    AddSubset(result, temp, nums, i + 1);
                    temp.RemoveAt(temp.Count - 1);
                }
            }
        }
    }