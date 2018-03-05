# 318. Maximum Product of Word Lengths
Maximum Product of Word Lengths

## Code
    public class Solution {
        public int MaxProduct(string[] words) {
            int[] mask = new int[words.Length];
            for(int i = 0; i < words.Length; i++) {
                for(int j = 0; j < words[i].Length; j++) {
                    mask[i] |= 1 << (words[i][j] - 'a');
                }
            }
            int max = 0;
            for(int i = 0; i < words.Length; i++) {
                for(int j = i + 1; j < words.Length; j++) {
                    if((mask[i] & mask[j]) == 0) {
                        max = Math.Max(words[i].Length * words[j].Length, max);
                    }
                }
            }
            return max;
        }
    }

    //Time Limit Exceeded 
    public class Solution {
        public int MaxProduct(string[] words) {
            int max = 0;
            string temp = "";
            for(int i = 0; i < words.Length; i ++) {

                for(int j = i + 1; j < words.Length; j ++) {
                    temp =  words[i];
                    while(temp.Length != 0) {
                        if(words[j].Contains(temp[0])) {
                            break;
                        }
                        temp = temp.Replace(temp[0].ToString(), "");
                    }
                    if(temp.Length == 0) {
                        int len = words[i].Length;
                        if(max < len * words[j].Length) {
                            max = len * words[j].Length;
                        }
                    }
                }
            }
            return max;
        }
    }
