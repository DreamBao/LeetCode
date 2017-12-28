# 120. Triangle
Triangle

## Code
    public class Solution {
        public static int result = int.MaxValue;
        
        public int MinimumTotal(IList<IList<int>> triangle) {
            // result = int.MaxValue;
            // GetSum(triangle, 0, 0, 0);
            //return Solution.result;
            int [] dp = new int[triangle.Count + 1];
            for (int i = triangle.Count - 1; i >= 0; i --){
                for (int j = 0; j < triangle[i].Count; j ++){
                    dp[j] = triangle[i][j] + Math.Min(dp[j], dp[j + 1]);
                }
            }
            return dp[0];


        }
        
        public void GetSum(IList<IList<int>> triangle, int preIndex, int sum, int level) {
            if(level > triangle.Count - 1) {
                if(sum < Solution.result)
                    Solution.result = sum;
                return;
            }
            IList<int> list = triangle[level];
            if(preIndex < 0 || preIndex > list.Count - 1)
                return;
            sum += list[preIndex];
            GetSum(triangle, preIndex, sum, level + 1);
            GetSum(triangle, preIndex - 1, sum, level + 1);
            GetSum(triangle, preIndex + 1, sum, level + 1);
        }
    }