# 130. Surrounded Regions
Surrounded Regions

## Code
    public class Solution {
        public void Solve(char[,] board) {
            if (board.GetLength(0) == 0 || board.GetLength(1) == 0)
                return;
            if (board.GetLength(0) < 2 || board.GetLength(1) < 2)
                return;
            int m = board.GetLength(0), n = board.GetLength(1);
            //Any 'O' connected to a boundary can't be turned to 'X', so ...
            //Start from first and last column, turn 'O' to '*'.
            for (int i = 0; i < m; i++) {
                if (board[i,0] == 'O')
                    boundaryDFS(board, i, 0);
                if (board[i,n-1] == 'O')
                    boundaryDFS(board, i, n-1);	
            }
            //Start from first and last row, turn '0' to '*'
            for (int j = 0; j < n; j++) {
                if (board[0,j] == 'O')
                    boundaryDFS(board, 0, j);
                if (board[m-1,j] == 'O')
                    boundaryDFS(board, m-1, j);	
            }
            //post-prcessing, turn 'O' to 'X', '*' back to 'O', keep 'X' intact.
            for (int i = 0; i < m; i++) {
                for (int j = 0; j < n; j++) {
                    if (board[i,j] == 'O')
                        board[i,j] = 'X';
                    else if (board[i,j] == '*')
                        board[i,j] = 'O';
                }
            }
        }
        
        private void boundaryDFS(char[,] board, int i, int j) {
            if (i < 0 || i > board.GetLength(0) - 1 || j <0 || j > board.GetLength(1) - 1)
                return;
            if (board[i,j] == 'O')
                board[i,j] = '*';
            if (i > 1 && board[i-1,j] == 'O')
                boundaryDFS(board, i-1, j);
            if (i < board.GetLength(0) - 2 && board[i+1,j] == 'O')
                boundaryDFS(board, i+1, j);
            if (j > 1 && board[i,j-1] == 'O')
                boundaryDFS(board, i, j-1);
            if (j < board.GetLength(1) - 2 && board[i,j+1] == 'O' )
                boundaryDFS(board, i, j+1);
        }
    }