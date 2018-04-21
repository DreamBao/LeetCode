# 456. 132 Pattern
132 Pattern

## Code
    public class Solution {
        public bool Find132pattern(int[] nums) {
            int n = nums.Length;
            int top = n;
            int third = int.MinValue;
            for (int i = n - 1; i >= 0; i--) {
                if (nums[i] < third) return true;
                while (top < n && nums[i] > nums[top])
                    third = nums[top++];
                nums[--top] = nums[i];
            }

            return false;
        }
    }