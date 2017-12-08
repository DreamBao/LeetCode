# 79. Word Search
Word Search


## Code
    public class Solution {
        public bool Exist(char[,] board, string word) {
            if(board == null || word == null || board.Length == 0 || word.Length == 0)
                return false;
            
            for(int i = 0; i < board.GetLength(0); i++) {
                for(int j = 0; j < board.GetLength(1); j++) {
                    if(SearchWord(board, word, i, j, 0))
                        return true;
                }
            }
            
            return false;
        }
        
        public bool SearchWord(char[,] board, string word, int i, int j, int pos) {
            if(pos == word.Length)
                return true;
            if(i >= board.GetLength(0) || i < 0 ||  j < 0 || j >= board.GetLength(1))    
                return false;
            if(board[i,j] == '*')
                return false;
            if(board[i,j] != word[pos])
                return false;
            char temp = board[i,j];
            board[i,j] = '*';
            bool res = SearchWord(board, word, i - 1, j, pos + 1)
                    || SearchWord(board, word, i + 1, j, pos + 1)
                    || SearchWord(board, word, i, j - 1, pos + 1)
                    || SearchWord(board, word, i, j + 1, pos + 1);
            board[i,j] = temp;
            return res;  
        }
    }