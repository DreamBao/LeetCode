# 59. Spiral Matrix II
Spiral Matrix II

## Code
    public class Solution {
        public int[,] GenerateMatrix(int n) {
            int[,] matrix = new int[n,n];
            List<int> res = new List<int>();
            for(int i = 1; i <= n*n; i++) {
                res.Add(i);
            }
            int num = 0;
            int rowBegin = 0;
            int rowEnd = matrix.GetLength(0)-1;
            int colBegin = 0;
            int colEnd = matrix.GetLength(1) - 1;
            
            while (rowBegin <= rowEnd && colBegin <= colEnd) {
                for (int j = colBegin; j <= colEnd; j ++) {
                    matrix[rowBegin,j] = res[num];
                    num++;
                }
                rowBegin++;
                
                for (int j = rowBegin; j <= rowEnd; j ++) {
                    matrix[j,colEnd] = res[num];
                    num++;
                }
                colEnd--;
                
                if (rowBegin <= rowEnd) {
                    for (int j = colEnd; j >= colBegin; j --) {
                        matrix[rowEnd,j] = res[num];
                        num++;
                    }
                }
                rowEnd--;
                
                if (colBegin <= colEnd) {
                    for (int j = rowEnd; j >= rowBegin; j --) {
                        matrix[j,colBegin] = res[num];
                        num++;
                    }
                }
                colBegin ++;
            }
            
            return matrix;
            
        }
    }