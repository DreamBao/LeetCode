# 48. Rotate Image
Rotate Image

## Code
    public class Solution {
        public void Rotate(int[,] matrix) {
            int row = matrix.GetLength(0);
            int col = matrix.GetLength(1);
            for(int i = 0; i<row; i++){
                for(int j = i; j<col; j++){
                    int temp = 0;
                    temp = matrix[i,j];
                    matrix[i,j] = matrix[j,i];
                    matrix[j,i] = temp;
                }
            }
            for(int i =0 ; i<row; i++){
                for(int j = 0; j<row/2; j++){
                    int temp = 0;
                    temp = matrix[i,j];
                    matrix[i,j] = matrix[i,row-1-j];
                    matrix[i,row-1-j] = temp;
                }
            }
        }
    }