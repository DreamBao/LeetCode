# 287. Find the Duplicate Number
Find the Duplicate Number

## Code
    public class Solution {
        public int FindDuplicate(int[] nums) {
            int len = nums.Length;
            Dictionary<int, int> dic = new Dictionary<int, int>();
            for(int i = 0; i < len; i ++) {
                if(dic.ContainsKey(nums[i])) {
                    //dic[nums[i]] ++;
                    return nums[i];
                }else {
                    dic.Add(nums[i], 1);
                }
            }
            return 0;
        }
    }