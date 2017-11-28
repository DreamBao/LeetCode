# 55. Jump Game
Jump Game

## Code
    public class Solution {
        public bool CanJump(int[] nums) {
            int reach=0;
            int i=0;
            while(i<nums.Length && i<=reach){
                reach=Math.Max(reach,i+nums[i]);
                i++;
            }
            return reach>=nums.Length-1;
        }
    }