# 416. Partition Equal Subset Sum
Partition Equal Subset Sum

## Code
    public class Solution {
        public bool CanPartition(int[] nums) {
            if (nums == null || nums.Length == 0) {
                return true;
            }
            
            int volumn = 0;
            for (int i = 0; i < nums.Length; i ++) {
                int num = nums[i];
                volumn += num;
            }
            if (volumn % 2 != 0) {
                return false;
            }
            volumn /= 2;
            bool[] dp = new bool[volumn + 1];
            dp[0] = true;
            for (int i = 1; i <= nums.Length; i++) {
                for (int j = volumn; j >= nums[i-1]; j--) {
                    dp[j] = dp[j] || dp[j - nums[i-1]];
                }
            }
            return dp[volumn];
        }
    }