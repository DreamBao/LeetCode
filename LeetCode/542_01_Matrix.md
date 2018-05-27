# 542. 01 Matrix
01 Matrix

## Code
    public class Solution {
        public int[,] UpdateMatrix(int[,] matrix) {
            bool updated;
            int nrow = matrix.GetLength(0);
            int ncol = matrix.GetLength(1);
            do {
                updated = false;
                for (int i = 0; i < nrow; i++) {
                    for (int j = 0; j < ncol; j++) {
                        if (matrix[i, j] != 0) {
                            int n = GetDistance(nrow, ncol, matrix, i, j);
                            if (n + 1 > matrix[i, j]) {
                                updated = true;
                                matrix[i, j] = n + 1;
                            }
                        }
                    }
                }
            } while (updated);
            return matrix;
        }
        
        public int GetDistance(int nrow, int ncol, int[,] matrix, int i, int j) {
            int n1 = (0 <= i - 1) ? matrix[i - 1, j] : int.MaxValue;
            int n2 = (i + 1 < nrow) ? matrix[i + 1, j] : int.MaxValue;
            int n3 = (0 <= j - 1) ? matrix[i, j - 1] : int.MaxValue;
            int n4 = (j + 1 < ncol) ? matrix[i, j + 1] : int.MaxValue;
            return Math.Min(Math.Min(n1, n2), Math.Min(n3, n4));
        }
    }