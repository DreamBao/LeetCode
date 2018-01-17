# 165. Compare Version Numbers
Compare Version Numbers

## Code
    public class Solution {
        public int CompareVersion(string version1, string version2) {        
            string[] ve1 = version1.Split('.');
            string[] ve2 = version2.Split('.');
            
            int length = Math.Min(ve1.Length, ve2.Length);
            
            for(int i = 0; i < length; i ++) {
                int v1 = int.Parse(ve1[i]);
                int v2 = int.Parse(ve2[i]);
                if(v1 > v2) {
                    return 1;
                } else if(v1 < v2) {
                    return -1;
                } else {
                    continue;
                }
            }
            
            if(ve1.Length > ve2.Length) {
                for(int j = length; j < ve1.Length; j ++) {
                    if(int.Parse(ve1[j]) > 0)
                        return 1;
                }
                return 0;
            } else if(ve1.Length < ve2.Length) {
                for(int j = length; j < ve2.Length; j ++) {
                    if(int.Parse(ve2[j]) > 0)
                        return -1;
                }
                return 0;
            } else {
                return 0;
            }
            
            return 0;
        }
    }