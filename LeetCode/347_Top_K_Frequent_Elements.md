# 347. Top K Frequent Elements
Top K Frequent Elements

## Code
    public class Solution {
        public IList<int> TopKFrequent(int[] nums, int k) {
            Dictionary<int, int> dic = new Dictionary<int, int>();
            int num = 0;
            IList<int> res = new List<int>();
            for(int i = 0; i < nums.Length; i++) {
                if(!dic.ContainsKey(nums[i])) {
                    dic.Add(nums[i], 1);
                }else {
                    dic[nums[i]] ++;
                    
                }
            }
            dic = dic.OrderByDescending(i => i.Value).ToDictionary(i => i.Key, i => i.Value);
            for(int j = 0; j < dic.Count; j ++) {
                var val = dic.ElementAt(j);
                if(num < k) {
                    res.Add(val.Key);
                }else {
                    return res;
                }
                num ++;
            }
            
            return res;
        }
    }