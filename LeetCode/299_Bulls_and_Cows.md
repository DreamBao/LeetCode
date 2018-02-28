# 299. Bulls and Cows
Bulls and Cows

## Code
    public class Solution {
        public string GetHint(string secret, string guess) {
            int secLen = secret.Length;
            int gueLen = guess.Length;
            int len = Math.Min(secLen, gueLen);
            
            int bulls = 0;
            int cows = 0;
            
            int[] bullArr = new int[10];
            int[] cowArr = new int[10];
            for(int i = 0; i < len; i ++) {
                if(secret[i] == guess[i]){
                    bulls ++;
                }
                else {
                    bullArr[secret[i] - '0'] ++;
                    cowArr[guess[i] - '0'] ++;
                }
            }
            
            for(int j = 0; j < 10; j ++){
                cows += Math.Min(bullArr[j], cowArr[j]);
            }
            
            return bulls + "A" + cows + "B";
        }
    }