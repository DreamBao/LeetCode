# 153. Find Minimum in Rotated Sorted Array
Find Minimum in Rotated Sorted Array

## Code
    public class Solution {
        public int FindMin(int[] nums) {
            int start = 0, end = nums.Length - 1;
            while(start < end) {
                int mid = start + (end - start) / 2;
                if(nums[mid] < nums[end]) 
                    end = mid;
                else 
                    start = mid+1;
            }
            return nums[start];
        }
    }