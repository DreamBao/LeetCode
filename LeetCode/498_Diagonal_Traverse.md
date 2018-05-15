# 498. Diagonal Traverse
Diagonal Traverse

## Code
    public class Solution {
        public int[] FindDiagonalOrder(int[,] matrix) {
            if (matrix.Length == 0) return new int[0];
            int r = 0, c = 0, m = matrix.GetLength(0), n = matrix.GetLength(1);
            int[] arr = new int[m * n];
            for (int i = 0; i < arr.Length; i++) {
                arr[i] = matrix[r,c];
                if ((r + c) % 2 == 0) { // moving up
                    if      (c == n - 1) { r++; }
                    else if (r == 0)     { c++; }
                    else            { r--; c++; }
                } else {                // moving down
                    if      (r == m - 1) { c++; }
                    else if (c == 0)     { r++; }
                    else            { r++; c--; }
                }   
            }   
            return arr;
        }
    }