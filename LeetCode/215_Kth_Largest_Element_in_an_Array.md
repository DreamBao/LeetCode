# 215. Kth Largest Element in an Array
Kth Largest Element in an Array

## Code
    public class Solution {
        public int FindKthLargest(int[] nums, int k) {
            Array.Sort(nums);
            return nums[nums.Length - k];
        }
    }