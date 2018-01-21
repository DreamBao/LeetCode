# 200. Number of Islands
Number of Islands

## Code
    public class Solution {
        public int NumIslands(char[,] grid) {
            int result = 0;
            if (grid.GetLength(0) == 0) 
                return 0;
            for (int i = 0; i < grid.GetLength(0); i++){
                for (int j = 0; j < grid.GetLength(1); j++)
                    if (grid[i,j] == '1') {
                        IsLand(i, j, grid);
                        result ++;
                    }
            }    
            return result;
        }
        
        
        public void IsLand(int i, int j, char[,] grid) {
            if (i < 0 || j < 0 || i >= grid.GetLength(0) || j >= grid.GetLength(1) || grid[i,j] != '1') 
                return;
            grid[i,j] = '0';
            IsLand(i + 1, j, grid);
            IsLand(i - 1, j, grid);
            IsLand(i, j + 1, grid);
            IsLand(i, j - 1, grid);
        }
    }