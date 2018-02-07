# 229. Majority Element II
Majority Element II

## Code
    public class Solution {
        public IList<int> MajorityElement(int[] nums) {
            int times = nums.Length / 3 + 1;
            IList<int> result = new List<int>();
            Dictionary<int, int> temp = new Dictionary<int, int>();
            for(int i = 0; i < nums.Length; i++) {
                if(temp.ContainsKey(nums[i])) {
                    temp[nums[i]] ++;
                } else {
                    temp.Add(nums[i], 1);   
                }
                if(!result.Contains(nums[i]) && temp[nums[i]] >= times) {
                    result.Add(nums[i]);
                }

            }
            
            return result;
        }
    }