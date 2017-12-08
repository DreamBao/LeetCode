# 80. Remove Duplicates from Sorted Array II
Remove Duplicates from Sorted Array II


## Code
    public class Solution {
        public int RemoveDuplicates(int[] nums) {
            int count = 0;
            List<int> result = new List<int>();
            Dictionary<int, int> dic = new Dictionary<int, int>();
            for(int i = 0; i < nums.Length; i++) {
                if(dic.ContainsKey(nums[i])) {
                    if(dic[nums[i]] < 2) {
                        count ++;
                        result.Add(nums[i]);
                        dic[nums[i]] += 1;
                    }
                }
                else {
                    count++;
                    result.Add(nums[i]);
                    dic.Add(nums[i], 1);
                }
            }
        for(int i = 0; i < result.Count; i++) {
            nums[i] = result[i];
        }
        
            return count;
        }
    }