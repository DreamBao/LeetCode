# 152. Maximum Product Subarray
Maximum Product Subarray

## Code
    public class Solution {
        public int MaxProduct(int[] nums) {
            // List<int> temp = new List<int>();
            // int result = int.MinValue;
            // for(int i = 0; i < nums.Length; i ++) {
            //     int tempNum = 1;
            //     for(int j = i; j < nums.Length; j ++) {
            //         tempNum = tempNum * nums[j];
            //         if(tempNum > result)
            //             result = tempNum;
            //     }
            // }
            // return result;
            
            if (nums.Length == 0) {
                return 0;
            }

            int maxherepre = nums[0];
            int minherepre = nums[0];
            int maxsofar = nums[0];
            int maxhere, minhere;

            for (int i = 1; i < nums.Length; i++) {
                maxhere = Math.Max(Math.Max(maxherepre * nums[i], minherepre * nums[i]), nums[i]);
                minhere = Math.Min(Math.Min(maxherepre * nums[i], minherepre * nums[i]), nums[i]);
                maxsofar = Math.Max(maxhere, maxsofar);
                maxherepre = maxhere;
                minherepre = minhere;
            }
            return maxsofar;
        }      
    }