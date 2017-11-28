# 56. Merge Intervals
Merge Intervals

## Code
    public class Solution {
        public IList<Interval> Merge(IList<Interval> intervals) {
            IList<Interval> result = new List<Interval>();
            List<Interval> tempIntervals = intervals.ToList();
            if(tempIntervals.Count == 0)
                return result;
            tempIntervals.Sort((i1, i2) => {
                if(i1.start < i2.start)
                    return -1;
                else 
                    return 1;
            });
            
            int Start = tempIntervals[0].start;
            int End = tempIntervals[0].end;
            
            for(int i = 0; i < tempIntervals.Count; i++) {
                if(tempIntervals[i].start <= End) {
                    End = Math.Max(End, tempIntervals[i].end);
                }
                else {
                    result.Add(new Interval(Start, End));
                    Start = tempIntervals[i].start;
                    End = tempIntervals[i].end;
                }
            }

            result.Add(new Interval(Start, End));
            return result;
        }
    }