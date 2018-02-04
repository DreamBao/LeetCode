# 223. Rectangle Area
Rectangle Area

## Code
    public class Solution {
        public int ComputeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
            int left = Math.Max(A,E), right = Math.Max(Math.Min(C,G), left);
            int bottom = Math.Max(B,F), top = Math.Max(Math.Min(D,H), bottom);
            return (C-A) * (D-B) - (right-left) * (top-bottom) + (G-E) * (H-F);
        }
    }