# 300. Longest Increasing Subsequence
Longest Increasing Subsequence

## Code
    public class Solution {
        public int LengthOfLIS(int[] nums) {
            int[] dp = new int[nums.Length];
            int len = 0;

            for(int i = 0; i < nums.Length; i ++) {
                int num = Array.BinarySearch(dp, 0, len, nums[i]);
                if(num < 0) num = -(num + 1);
                dp[num] = nums[i];
                if(num == len) len++;
            }

            return len;
        }
    }