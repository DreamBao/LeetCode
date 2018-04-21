# 462. Minimum Moves to Equal Array Elements II
Minimum Moves to Equal Array Elements II

## Code
    public class Solution {
        public int MinMoves2(int[] nums) {
            Array.Sort(nums);
            int res = 0;
            int mid = nums[nums.Length / 2];
            foreach (int num in nums) {
                res += Math.Abs(num - mid);
            }
            return res;
        }
    }