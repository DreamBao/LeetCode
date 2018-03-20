# 377. Combination Sum IV
Combination Sum IV

## Code
    public class Solution {
        public Dictionary<int, int> tempDic = new Dictionary<int, int>();
        public int CombinationSum4(int[] nums, int target) {
            int res = 0;
            if (nums == null || nums.Length ==0 || target < 0 ) return 0;
            if ( target ==0 ) return 1;
            if (tempDic.ContainsKey(target)) return tempDic[target];
            for (int i = 0; i < nums.Length; i++){
                res += CombinationSum4(nums, target - nums[i]);
            }
            tempDic.Add(target, res);
            return res;
        }
    }