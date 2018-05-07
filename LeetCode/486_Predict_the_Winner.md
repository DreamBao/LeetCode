# 486. Predict the Winner
Predict the Winner

## Code
    public class Solution {
        public bool PredictTheWinner(int[] nums) {
            int[,] dp = new int[nums.Length,nums.Length];
            for(int j = 0; j < nums.Length; j ++)
                for(int i = j; i >= 0; i --)  dp[i,j] = (i==j)? nums[i] : Math.Max(nums[i]-dp[i+1,j], nums[j]-dp[i,j-1]);
            return dp[0,nums.Length-1] >= 0;
        }
    }