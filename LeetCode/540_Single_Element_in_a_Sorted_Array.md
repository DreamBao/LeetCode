# 540. Single Element in a Sorted Array
Single Element in a Sorted Array

## Code
    public class Solution {
        public int SingleNonDuplicate(int[] nums) {
            Dictionary<int, int> dic = new Dictionary<int, int>();
            for(int i = 0; i < nums.Length; i ++) {
                if(dic.ContainsKey(nums[i]))
                    dic[nums[i]] ++;
                else 
                    dic.Add(nums[i], 1);
            }
            foreach(var val in dic) {
                if(val.Value == 1)
                    return val.Key;
            }
            return 0;
        }
    }