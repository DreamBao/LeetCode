# 467. Unique Substrings in Wraparound String
Unique Substrings in Wraparound String

## Code
    public class Solution {
        public int FindSubstringInWraproundString(string p) {
            int[] dpArr = new int[p.Length];
            int[] ch = new int[26];
            for(int i = 0; i < p.Length; i++){
                dpArr[i] = p[i] - 'a';
            }
            int res = 0;
            int maxLen = 0;
            for(int i = 0;i < p.Length; i ++){
                if(i > 0 && (dpArr[i-1] + 1) % 26 == dpArr[i] % 26){
                    maxLen ++ ;
                } else{
                    maxLen = 1;
                }
                ch[dpArr[i]] = Math.Max(ch[dpArr[i]],maxLen);
            }
            for(int i = 0; i < 26; i ++)
                res += ch[i];
            return res;
            
        }
    }