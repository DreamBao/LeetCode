# 260. Single Number III
Single Number III

## Code
    public class Solution {
        public int[] SingleNumber(int[] nums) {
            int v = 0;

            Dictionary<int, int> dic = new Dictionary<int, int>(); 
            for(int i = 0; i < nums.Length; i ++) {
                if(dic.ContainsKey(nums[i])) {
                    dic[nums[i]] ++;
                }
                else {
                    dic.Add(nums[i], 1);
                }
            }
            
            List<int> res = new List<int>();
            
            int k = 0;
            foreach(var val in dic) {
                if(val.Value == 1) {
                    res.Add(val.Key);
                }
            }
            
            return res.ToArray();
        }
    }