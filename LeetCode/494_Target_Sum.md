# 494. Target Sum
Target Sum

## Code
    public class Solution {
        public int FindTargetSumWays(int[] nums, int S) {
            int n = nums.Length;
            int sum = 0;
            foreach (int num in nums){
                sum += num;
            }
            if (Math.Abs(S) > sum || (S + sum) % 2 == 1){
                return 0;
            }
            int target = (S + sum) / 2;
            int[] f = new int[target + 1];
            f[0] = 1;
            int max = 0;
            for (int i = 0; i < n; i++){
                int cur = nums[i];
                for (int j = Math.Min(max, target - cur); j >= 0; j--){
                    f[j + cur] += f[j];
                }
                max = max + cur;
            }
            return f[target];
        }
    }