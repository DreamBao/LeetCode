# 539. Minimum Time Difference
Minimum Time Difference

## Code
    public class Solution {
        public int FindMinDifference(IList<string> timePoints) {
            if(timePoints == null || timePoints.Count == 0) {
                return 0;
            }
            
            int min = 1441;
            int minutes = 0;
            int[] minutesArr = new int[1441];
            foreach(string s in timePoints) {
                string[] hrMin = s.Split(':');
                if(hrMin[0] == "00" && hrMin[1] == "00") {
                    minutes = 1440;
                } else {
                    minutes = int.Parse(hrMin[0]) * 60 + int.Parse(hrMin[1]);
                }
                if(minutesArr[minutes] != 0) {
                    return 0;
                }
                minutesArr[minutes] = minutes;
            }
            
            int lastPos = -1;
            for(int i = 1; i < 1441; i ++) {
                if(minutesArr[i] == 0) {
                    continue;
                }
                if(lastPos == -1) {
                    lastPos = i;
                    minutesArr[0] = minutesArr[i];
                    continue;
                }
                min = Math.Min(min, minutesArr[i] - minutesArr[lastPos]);
                lastPos = i;
            }
            
            min = Math.Min(min, minutesArr[0] + (1440 - minutesArr[lastPos]));
            
            return min;
        }
    }