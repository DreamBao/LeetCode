# 64. Unique Paths II
Unique Paths II

## Code
    public class Solution {
        public int UniquePathsWithObstacles(int[,] obstacleGrid) {
            int width = obstacleGrid.GetLength(1);
            int[] dp = new int[width];
            dp[0] = 1;
            for (int i = 0 ; i < obstacleGrid.GetLength(0); i++) {
                for (int j = 0; j < width; j++) {
                    if (obstacleGrid[i,j] == 1)
                        dp[j] = 0;
                    else if (j > 0)
                        dp[j] += dp[j - 1];
                }
            }
            return dp[width - 1];
        }
    }
