# 435. Non-overlapping Intervals
Non-overlapping Intervals

## Code
    /**
    * Definition for an interval.
    * public class Interval {
    *     public int start;
    *     public int end;
    *     public Interval() { start = 0; end = 0; }
    *     public Interval(int s, int e) { start = s; end = e; }
    * }
    */
    public class Solution {
        public int EraseOverlapIntervals(Interval[] intervals) {
            
            List<Interval> list = intervals.ToList();
            list.Sort(Compare);
            int end = int.MinValue;
            int count = 0;
            foreach (Interval interval in list) {
                if (interval.start >= end) end = interval.end;
                else count++;
            }
            return count;
            
        }
        
        public int Compare(Interval i1, Interval i2) {
            if (i1.end != i2.end) return i1.end - i2.end;
            return i2.start - i1.start;
        }
    }