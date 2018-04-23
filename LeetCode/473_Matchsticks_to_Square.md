# 473. Matchsticks to Square
Matchsticks to Square

## Code
    public class Solution {
        public bool Makesquare(int[] nums) {
            if (nums == null || nums.Length < 4) return false;
            int sum = 0;
            foreach (int num in nums) sum += num;
            if (sum % 4 != 0) return false;
            Array.Sort(nums);
            
            return Dfs(nums, sum / 4, new int[4], nums.Length - 1);
        }
        
        public bool Dfs(int[] nums, int target, int[] sum, int index) {
            if (sum[0] == target && sum[1] == target && sum[2] == target) {
                return true;
            }
            if (index >= 0){
                for (int i = 0; i < 4; i++) {
                    if (sum[i] + nums[index] > target) {
                        continue;
                    }
                    sum[i] += nums[index];
                    if (Dfs(nums, target, sum, index - 1)) {
                        return true;
                    }
                    sum[i] -= nums[index];
                } 
            }
            return false;
        }
        
    }