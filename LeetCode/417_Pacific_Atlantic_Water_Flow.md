# 417. Pacific Atlantic Water Flow
Pacific Atlantic Water Flow

## Code
    public class Solution {
        public int[] dx = {-1,0,0,1};
        public int[] dy = {0,1,-1,0};
        public IList<int[]> PacificAtlantic(int[,] matrix) {
            
            IList<int[]> res = new List<int[]>();
            if (matrix == null || matrix.GetLength(0) == 0 || matrix.GetLength(1) == 0) return res;
            bool[,] pacific = new bool[matrix.GetLength(0),matrix.GetLength(1)];
            bool[,] atlantic = new bool[matrix.GetLength(0),matrix.GetLength(1)];
            for (int i = 0; i < matrix.GetLength(0); i++){
                pacific[i,0] = true;
                atlantic[i,matrix.GetLength(1) - 1] = true;
            }
            for (int j = 0; j < matrix.GetLength(1); j++){
                pacific[0,j] = true;
                atlantic[matrix.GetLength(0)-1,j] = true;
            }
            for (int i = 0; i < matrix.GetLength(0); i++){
                explore(pacific, matrix, i, 0);
                explore(atlantic, matrix, i, matrix.GetLength(1)-1);
            }
            for (int j = 0; j < matrix.GetLength(1); j++){
                explore(pacific, matrix, 0, j);
                explore(atlantic, matrix, matrix.GetLength(0)-1, j);
            }
            for (int i = 0; i < matrix.GetLength(0); i++){
                for (int j = 0; j < matrix.GetLength(1); j++){
                    if (pacific[i,j] && atlantic[i,j] == true)
                        res.Add(new int[]{i,j});
                }
            }
            return res;
        }
        
        
        public void explore(bool[,] grid, int[,] matrix, int i, int j){
            grid[i,j] = true;
            for (int d = 0; d < dx.Length; d++){
                if (i + dy[d] < grid.GetLength(0) && i + dy[d] >= 0 && 
                    j + dx[d] < grid.GetLength(1) && j + dx[d] >= 0 && 
                    grid[i+dy[d],j+dx[d]] == false && matrix[i+dy[d],j+dx[d]] >= matrix[i,j])
                        explore(grid, matrix, i+dy[d], j+dx[d]);
            }
        }
    }