# 417. Pacific Atlantic Water Flow
Pacific Atlantic Water Flow

## Code
    public class Solution {
        public IList<int[]> PacificAtlantic(int[,] matrix) {
            IList<int[]> res = new List<int[]>();
            for(int i = 0; i < matrix.GetLength(0); i ++) {
                for(int j = 0; j < matrix.GetLength(1); j ++) {
                    bool isCan = Bfs(matrix, i, j, matrix[i,j]);
                    if(isCan) {
                        res.Add(new int[2]{i, j});
                    }
                }
            }
            return res;
        }
        
        
        public bool Bfs(int[,] matrix, int i, int j, int ori) {
            if(i < 0 || j < 0 ||i >= matrix.GetLength(0) || j >= matrix.GetLength(1) || matrix[i,j] > ori) {
                return false;
            }
            
            ori = matrix[i,j];
            if(i == 0 && j == 0) {
                return true;
            }
            
            bool isCan = Bfs(matrix, i - 1, j, ori) || Bfs(matrix, i, j - 1, ori) || Bfs(matrix, i, j + 1, ori) || Bfs(matrix, i + 1, j, ori) || 
                        Bfs(matrix, i + 1, j + 1, ori) || Bfs(matrix, i - 1, j - 1, ori);
            return isCan;
                            
        }
    }