# 201. Bitwise AND of Numbers Range
Bitwise AND of Numbers Range

## Code
    public class Solution {
        public int RangeBitwiseAnd(int m, int n) {
            int d = int.MaxValue;
            while ((m & d) != (n & d)) {
                d <<= 1;
            }
            return m & d;
        }
    }