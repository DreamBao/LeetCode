# 390. Elimination Game
Elimination Game

## Code
    public class Solution {
        public int LastRemaining(int n) {
            return n==1 ? 1 : 2 * (n/2 + 1 - LastRemaining(n/2));
        }
    }