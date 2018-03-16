# 368. Largest Divisible Subset
Largest Divisible Subset

## Code
    public class Solution {
        public IList<int> LargestDivisibleSubset(int[] nums) {
            IList<int> res = new List<int>();
            int n = nums.Length;
            int[] count = new int[n];
            int[] pre = new int[n];
            Array.Sort(nums);
            int max = 0, index = -1;
            for (int i = 0; i < n; i++) {
                count[i] = 1;
                pre[i] = -1;
                for (int j = i - 1; j >= 0; j--) {
                    if (nums[i] % nums[j] == 0) {
                        if (1 + count[j] > count[i]) {
                            count[i] = count[j] + 1;
                            pre[i] = j;
                        }
                    }
                }
                if (count[i] > max) {
                    max = count[i];
                    index = i;
                }
            }
            while (index != -1) {
                res.Add(nums[index]);
                index = pre[index];
            }
            return res;
            
        }
    }