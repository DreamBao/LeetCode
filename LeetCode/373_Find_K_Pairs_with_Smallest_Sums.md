# 373. Find K Pairs with Smallest Sums
Find K Pairs with Smallest Sums

## Code
    public class Solution {
        public IList<int[]> KSmallestPairs(int[] nums1, int[] nums2, int k) {
            IList<int[]> res = new List<int[]>();
            Dictionary<int, List<int[]>> dic = new Dictionary<int, List<int[]>>();
            int len1 = nums1.Length;
            int len2 =  nums2.Length;
            for(int i = 0; i < len1; i++) {
                for(int j = 0; j < len2; j++) {
                    int[] nums = new int[2];
                    nums[0] = nums1[i];
                    nums[1] = nums2[j];
                    int sum = nums[0] + nums[1];
                    if(dic.ContainsKey(sum)) {
                        dic[sum].Add(nums);
                    }else {
                        List<int[]> list = new List<int[]>(){nums};
                        dic.Add(sum, list);
                    }
                }
            }
            
            dic = dic.OrderBy(i => i.Key).ToDictionary(j => j.Key, j => j.Value);
            int t = 0;
            foreach(var val in dic) {
                for(int i = 0; i < val.Value.Count; i ++) {
                    res.Add(val.Value[i]);
                    t ++;
                    if(res.Count >= k)
                        return res;
                }
                
            }
            return res;
        }
    }