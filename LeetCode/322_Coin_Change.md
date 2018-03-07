# 322. Coin Change
Coin Change

## Code
    public class Solution {
        public int CoinChange(int[] coins, int amount) {
            if (coins == null || coins.Length == 0 || amount <= 0)
                return 0;
            int[] minNumber = new int[amount + 1];
            for (int i = 1; i <= amount; i++) {
                minNumber[i] = int.MaxValue;
                for (int j = 0; j < coins.Length; j++) {
                    if (coins[j] <= i && minNumber[i - coins[j]] != int.MaxValue)
                        minNumber[i] = Math.Min(minNumber[i], 1 + minNumber[i - coins[j]]);
                }
            }
            if (minNumber[amount] == int.MaxValue)
                return -1;
            else
                return minNumber[amount];
        }
    }