# 137. Single Number II
Single Number II

## Code
    public class Solution {
        public int SingleNumber(int[] nums) {
            Dictionary<int, int> dic = new Dictionary<int, int>();
            for(int i = 0; i < nums.Length; i ++) {
                if(!dic.ContainsKey(nums[i])) {
                    dic.Add(nums[i], 1);
                }
                else {
                    dic[nums[i]] ++;
                }
            }
            foreach(var val in dic) {
                if(val.Value == 1)
                    return val.Key;
            }
            return 0;
        }
    }