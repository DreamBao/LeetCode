# 75. Sort Colors
Sort Colors


## Code
    public class Solution {
        public void SortColors(int[] nums) {
            Array.Sort(nums);
            int red = 0;
            List<int> temp = new List<int>();
            for(int i = 0; i < nums.Length; i++) {
                if(nums[i] == 0) {
                    temp.Insert(0,nums[i]);
                    red ++;
                }
                
                if(nums[i] == 1) {
                    temp.Insert(red,nums[i]);
                }
                
                if(nums[i] == 2) {
                    temp.Add(nums[i]);
                }
            }
            nums = temp.ToArray();
        }
    }