# 213. House Robber II
House Robber II

## Code
    public class Solution {
        public int Rob(int[] nums) {
            int length = nums.Length;  
            if(length == 0)  
                return 0;  
            if(length == 1)  
                return nums[0];  
                
            return Math.Max(RobDP(nums,0,length - 2), RobDP(nums,1,length - 1));  
        }
        
        
        int RobDP(int[] nums,int first,int last)  
        {  
            int pLast = 0, ppLast = 0;  
            for(int i=first;i<=last;i++)  
            {  
                int temp = pLast;  
                pLast = Math.Max(ppLast + nums[i], pLast);  
                ppLast = temp;  
            }  
            return pLast;  
        }  
    }