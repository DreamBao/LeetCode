# 209. Minimum Size Subarray Sum
Minimum Size Subarray Sum

## Code
    public class Solution {
        public int MinSubArrayLen(int s, int[] nums) {
            int result = int.MaxValue;
            
            if(nums.Length == 0)
                return 0;
            
            int temp = 0;
            int j = 0;
            for(int i = 0; i < nums.Length; i++) {
                temp += nums[i];

                while(temp >= s) {
                    result = Math.Min(result, i - j + 1);
                    temp -= nums[j];
                    j++;
                }
            }
            
            if(result == int.MaxValue)
                return 0;
            
            return result;
        }
    }