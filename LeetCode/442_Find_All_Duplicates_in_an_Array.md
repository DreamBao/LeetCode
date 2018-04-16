# 442. Find All Duplicates in an Array
Find All Duplicates in an Array

## Code
    public class Solution {
        public IList<int> FindDuplicates(int[] nums) {
            IList<int> res = new List<int>();
            Dictionary<int, int> dic = new Dictionary<int, int>();
            for(int i = 0; i < nums.Length; i ++) {
            if(dic.ContainsKey(nums[i])) {
                dic[nums[i]] ++;
            }else {
                dic.Add(nums[i], 1);
            }
            }
            
            foreach(var val in dic) {
                if(val.Value == 2) 
                    res.Add(val.Key);
            }
            
            return res;
        }
    }