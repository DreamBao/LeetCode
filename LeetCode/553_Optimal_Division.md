# 553. Optimal Division
Optimal Division

## Code
    public class Solution {
        public string OptimalDivision(int[] nums) {
            if (nums == null || nums.Length == 0) return "";
            if (nums.Length == 1) return nums[0] + "";
            if (nums.Length == 2) return nums[0] + "/" + nums[1];
            StringBuilder s = new StringBuilder();
            s.Append(nums[0] + "/(" + nums[1]);
            for (int i = 2; i < nums.Length; i++) {
                s.Append("/");
                s.Append(nums[i]);
            }
            s.Append(")");
            return s.ToString();      
        }
    }