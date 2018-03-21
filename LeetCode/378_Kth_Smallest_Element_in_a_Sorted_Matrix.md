# 378. Kth Smallest Element in a Sorted Matrix
Kth Smallest Element in a Sorted Matrix

## Code
    public class Solution {
        public int KthSmallest(int[,] matrix, int k) {
            int t = 0;
            int[] temp = new int[matrix.Length];
            
            if(k == 0)
                return matrix[0,0];
            for(int i = 0; i < matrix.GetLength(0); i ++) {
                for(int j = 0; j < matrix.GetLength(1); j ++) {
                    temp[t] = matrix[i,j];
                    t ++;
                }
            }
            Array.Sort(temp);
            
            for(int i = 0; i < temp.Length; i ++) {
                k--;
                if(k <= 0)
                    return temp[i];
            }
            
            return 0;
        }
    }