# 81. Search in Rotated Sorted Array II
Search in Rotated Sorted Array II


## Code
    public class Solution {
        public bool Search(int[] nums, int target) {
            if(nums.Length == 0)
                return false;
            int left =0, right = nums.Length-1;
            int mid = 0;
            while(left<right){
                mid=(left+right)/2;
                if(nums[mid]==target) return true;
                if(nums[mid]>nums[right]){
                    if(nums[mid]>target && nums[left] <= target) right = mid;
                    else left = mid + 1;
                }else if(nums[mid] < nums[right]){
                    if(nums[mid]<target && nums[right] >= target) left = mid + 1;
                    else right = mid;
                }else{
                    right--;
                }
            }
            return nums[left] == target ? true : false;
        }
    }