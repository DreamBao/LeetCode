# 274. H-Index
H-Index2

## Code
    public class Solution {
        public int HIndex(int[] citations) {
            //Array.Sort(citations);  
            int level = 0;  
            for(int i = 0; i < citations.Length; i++)  
                level = Math.Max(level,Math.Min(citations.Length - i,citations[i]));  
            return level;  
        }
    }