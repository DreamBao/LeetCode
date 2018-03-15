# 365. Water and Jug Problem
Water and Jug Problem

## Code
    public class Solution {
        public bool CanMeasureWater(int x, int y, int z) {
            return z == 0 || (long)x + y >= z && z % Gcd(x, y) == 0;
        }
        public int Gcd(int x, int y) {
            return y == 0 ? x : Gcd(y, x % y);
        }
    }