# 304. Range Sum Query 2D - Immutable
Range Sum Query 2D - Immutable

## Code
    public class NumMatrix {
        public int[,] dp;
        
        public NumMatrix(int[,] matrix) {
            if(matrix == null || matrix.GetLength(0) == 0 || matrix.GetLength(1) == 0){
                return;   
            }
        
            int m = matrix.GetLength(0);
            int n = matrix.GetLength(1);

            dp = new int[m + 1,n + 1];
            for(int i = 1; i <= m; i++){
                for(int j = 1; j <= n; j++){
                    dp[i,j] = dp[i - 1,j] + dp[i,j - 1] -dp[i - 1,j - 1] + matrix[i - 1,j - 1] ;
                }
            }
        }
        
        public int SumRegion(int row1, int col1, int row2, int col2) {
            int iMin = Math.Min(row1, row2);
            int iMax = Math.Max(row1, row2);

            int jMin = Math.Min(col1, col2);
            int jMax = Math.Max(col1, col2);

            return dp[iMax + 1,jMax + 1] - dp[iMax + 1,jMin] - dp[iMin,jMax + 1] + dp[iMin,jMin];    
        }
    }

    /**
    * Your NumMatrix object will be instantiated and called as such:
    * NumMatrix obj = new NumMatrix(matrix);
    * int param_1 = obj.SumRegion(row1,col1,row2,col2);
    */