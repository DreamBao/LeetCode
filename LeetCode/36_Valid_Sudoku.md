36. Valid Sudoku
Valid Sudoku

## Code
    public class Solution {
        public bool IsValidSudoku(char[,] board) {
            if(board.Length == 0)
                return false;
            char[] array = new char[9];
            for(int i = 0; i < 9; i++) {
                for(int k = 0; k < 9; k ++)
                    array[k] = '0';
                for(int j = 0; j < 9; j++) {
                    if(board[i,j] == '.')
                        continue;
                    if(array.Contains(board[i,j]))
                       return false;
                    else 
                        array[j] = board[i,j];
                }
            }

            for(int i = 0; i < 9; i++) {
                for(int k = 0; k < 9; k ++)
                    array[k] = '0';
                for(int j = 0; j < 9; j++) {
                    if(board[j,i] == '.')
                        continue;
                    if(array.Contains(board[j,i]))
                       return false;
                    else 
                        array[j] = board[j,i];
                }
            }

            int temp = 0;
            for(int i = 0; i < 3; i ++) {
                for(int j = 0; j < 9; j ++) {
                    if(j % 3 == 0)
                         for(int k = 0; k < 9; k ++) {
                            array[k] = '0';
                            temp = 0;    
                         }
                    for(int l = 0; l < 3; l ++) {
                        int col = l + 3*i;
                        if(board[j,col] == '.')
                            continue;

                        if(array.Contains(board[j,col]))
                            return false;
                        else 
                            array[temp] = board[j,col];
                        temp ++;

                    }
                }
            }

            return true;
        }
    }

