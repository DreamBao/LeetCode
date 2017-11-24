# 47. Permutations II
Permutations II

## Code
    public class Solution {
        public IList<IList<int>> PermuteUnique(int[] nums) {
            Array.Sort(nums);
            IList<IList<int>> result = new List<IList<int>>();
            List<int> list = new List<int>();
            List<int> numList = new List<int>();
            GetPermuteUnique(nums, 0, list, result, numList);
            return result;
        }
        
        public void GetPermuteUnique(int[] nums, int num, List<int> list, IList<IList<int>> result, List<int> numList) {
            if(list.Count == nums.Length){
                result.Add(new List<int>(list));
                return;
            }
            for(int i = 0; i < nums.Length; i ++) {
                if(i > 0 && nums[i] == nums[i-1] && numList.Contains(i-1))
                    continue;
                
                if(!numList.Contains(i)) {
                    list.Add(nums[i]);
                    numList.Add(i);
                }
                else 
                    continue;
                GetPermuteUnique(nums, num + 1, list, result, numList);
                numList.RemoveAt(numList.Count - 1);
                list.RemoveAt(list.Count - 1);            
            }
        }
    }