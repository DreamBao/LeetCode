# 309. Best Time to Buy and Sell Stock with Cooldown
Best Time to Buy and Sell Stock with Cooldown

## Code
    public class Solution {
        public int MaxProfit(int[] prices) {
            int profit1 = 0, profit2 = 0;   
            for(int i = 1; i < prices.Length; i++){
                int copy = profit1;
                profit1 = Math.Max(profit1 + prices[i] - prices[i-1], profit2);
                profit2 = Math.Max(copy, profit2);
            }
            return Math.Max(profit1, profit2);
        }
    }