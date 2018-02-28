# 289. Game of Life
Game of Life

## Code
    public class Solution {
        public void GameOfLife(int[,] board) {
            if (board == null || board.GetLength(0) == 0) return;
            int m = board.GetLength(0), n = board.GetLength(1);

            for (int i = 0; i < m; i++) {
                for (int j = 0; j < n; j++) {
                    int lives = LiveNeighbors(board, m, n, i, j);
                    if (board[i,j] == 1 && lives >= 2 && lives <= 3) {  
                        board[i,j] = 3; 
                    }
                    if (board[i,j] == 0 && lives == 3) {
                        board[i,j] = 2; 
                    }
                }
            }

            for (int i = 0; i < m; i++) {
                for (int j = 0; j < n; j++) {
                    board[i,j] >>= 1;  
                }
            }
        }
        
        public int LiveNeighbors(int[,] board, int m, int n, int i, int j) {
            int lives = 0;
            for (int x = Math.Max(i - 1, 0); x <= Math.Min(i + 1, m - 1); x++) {
                for (int y = Math.Max(j - 1, 0); y <= Math.Min(j + 1, n - 1); y++) {
                    lives += board[x,y] & 1;
                }
            }
            lives -= board[i,j] & 1;
            return lives;
        }
    }