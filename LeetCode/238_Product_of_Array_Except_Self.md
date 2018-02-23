# 238. Product of Array Except Self
Product of Array Except Self

## Code
    public class Solution {
        public int[] ProductExceptSelf(int[] nums) {
            int len = nums.Length;
            int[] res = new int[len];
            if(len == 0)
                return res;
            
            int max = 1;
            int havZero = 0;
            for(int i = 0;i < len; i++) {
                if(nums[i] != 0)
                    max *= nums[i];
                else 
                havZero ++; 
            }
            if(havZero > 1)
                return res;
            
            for(int i = 0; i < len; i++) {
                if(havZero > 0) {
                    if(havZero == 1) {
                        if(nums[i] == 0)
                            res[i] = max;
                        else 
                            res[i] = 0;
                    }
                }
                else 
                    res[i] = max / nums[i];
            }
            return res;
        }
    }