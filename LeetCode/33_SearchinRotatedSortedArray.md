# 33. Search in Rotated Sorted Array
Search in Rotated Sorted Array

## Code
public class Solution {
    public int Search(int[] nums, int target) {
        if(nums==null || nums.Length==0)  
            return -1;  
        int l = 0;  
        int r = nums.Length-1;  
        while(l<=r)  
        {  
            int m = (l+r)/2;  
            if(target == nums[m])  
                return m;  
            if(nums[m]<nums[r])  
            {  
                if(target>nums[m] && target<=nums[r])  
                    l = m+1;  
                else  
                    r = m-1;  
            }  
            else  
            {  
                if(target>=nums[l] && target<nums[m])  
                    r = m-1;  
                else  
                    l = m+1;                      
            }  
        }  
        return -1;  
    }
}