# 503. Next Greater Element II
Next Greater Element II

## Code
    public class Solution {
        public int[] NextGreaterElements(int[] nums) {
            int  n = nums.Length;
            int[] res = new int[n];
            for (int i = 0; i < n; i++) {
                res[i] = -1;
                for (int k = i + 1; k < i + n; k++) {
                    if (nums[k % n] > nums[i]){
                        res[i] = nums[k % n];
                        break;
                    }
                }
            }
            return res;
        }
    }