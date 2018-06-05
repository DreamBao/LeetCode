# 518. Coin Change 2
Coin Change 2

## Code
    public class Solution {
        public int Change(int amount, int[] coins) {
            int[] dp = new int [amount + 1];
            dp[0] = 1;
            for(int i = 0; i < coins.Length; i++) {
                for(int j = 0; j < amount && j + coins[i] <= amount; j++) dp[j + coins[i]] += dp[j];
            }
            return dp[amount];
        }
    }