# 392. Is Subsequence
Is Subsequence

## Code
    public class Solution {
        public bool IsSubsequence(string s, string t) {
            bool res = true; 
            for(int i = 0; i < s.Length; i ++) {
                if(!t.Contains(s[i])) {
                    res = false;
                    return res;
                }else {
                    int index = t.IndexOf(s[i]) + 1;
                    t = t.Substring(index);
                }
                
            }
            return res;
        }
    }