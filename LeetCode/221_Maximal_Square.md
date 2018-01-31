# 221. Maximal Square
Maximal Square

## Code
    public class Solution {
        public int MaximalSquare(char[,] matrix) {
            if(matrix.GetLength(0) == 0) return 0;
            int m = matrix.GetLength(0), n = matrix.GetLength(1), result = 0;
            int[,] b = new int[m+1,n+1];
            for (int i = 1 ; i <= m; i++) {
                for (int j = 1; j <= n; j++) {
                    if(matrix[i-1,j-1] == '1') {
                        b[i,j] = Math.Min(Math.Min(b[i,j-1] , b[i-1,j-1]), b[i-1,j]) + 1;
                        result = Math.Max(b[i,j], result);
                    }
                }
            }
            return result * result;
        }
    }