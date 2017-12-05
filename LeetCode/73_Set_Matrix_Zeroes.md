# 73. Set Matrix Zeroes
Set Matrix Zeroes


## Code
    public class Solution {
        public void SetZeroes(int[,] matrix) {
            
            bool res1 = false;
            bool res2 = false;
            for(int i = 0; i < matrix.GetLength(0); i ++) {
                for(int j = 0; j < matrix.GetLength(1); j ++) {
                    if(matrix[i,j] == 0) {
                        if(i == 0)
                            res1 = true;
                        if(j == 0)
                            res2 = true;
                        matrix[0,j] = 0;
                        matrix[i,0] = 0;
                    }    
                }
            }
            
            for(int i = 1; i < matrix.GetLength(0); i++) {
                for(int j = 1; j < matrix.GetLength(1); j++) {
                    if(matrix[i,0] == 0 || matrix[0,j] == 0) {
                        matrix[i,j] = 0;
                    }
                }
            }
            
            if(res1)
                for(int i = 0; i < matrix.GetLength(1); i++) {
                    matrix[0,i] = 0;
                }
            if(res2)
                for(int i = 0; i < matrix.GetLength(0); i++) {
                    matrix[i,0] = 0;
                }
        }
    }