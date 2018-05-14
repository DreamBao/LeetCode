# 495. Teemo Attacking
Teemo Attacking

## Code
    public class Solution {
        public int FindPoisonedDuration(int[] timeSeries, int duration) {
            int max = 0;
            int temp = 0;
            
            for(int i = 0; i < timeSeries.Length; i ++) {
            int diff = temp - timeSeries[i];
                max += duration - ( diff > 0 ? diff : 0);
                temp = timeSeries[i] + duration;
            }
            
            return max;
            
        }
    }