# 240. Search a 2D Matrix II
Search a 2D Matrix II

## Code
    public class Solution {
        public bool SearchMatrix(int[,] matrix, int target) {
            if(matrix == null || matrix.GetLength(0) < 1 || matrix.GetLength(1) < 1) {
                return false;
            }
            int col = matrix.GetLength(1) - 1;
            int row = 0;
            while(col >= 0 && row <= matrix.GetLength(0) - 1) {
                if(target == matrix[row, col]) {
                    return true;
                } else if(target < matrix[row, col]) {
                    col --;
                } else if(target > matrix[row, col]) {
                    row ++;
                }
            }
            return false;
        }
    }