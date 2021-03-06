# 464. Can I Win
Can I Win

## Code
    public class Solution {
        public bool CanIWin(int maxChoosableInteger, int desiredTotal) {
            int[] mem = new int [(int)Math.Pow(2, maxChoosableInteger)];
            if ((maxChoosableInteger * (maxChoosableInteger + 1) / 2) < desiredTotal) return false;
            return CanWin(mem, 0, maxChoosableInteger, desiredTotal);
        }
        
        public bool CanWin(int[] mem, int state, int max, int target) {
            if (mem[state] != 0) return mem[state] == 1 ? true : false;
            
            bool win = false;
            for(int i = 1, b = 1 << (i - 1); i <= max; i++, b = 1 << (i - 1)) {
                if ((state & b) != 0) continue;
                if (i >= target || !CanWin(mem, state | b, max, target - i)) { win = true; break; }
            }
            
            mem[state] = win ? 1 : -1;
            
            return win;
        }
    }