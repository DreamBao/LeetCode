# 477. Total Hamming Distance
Total Hamming Distance

## Code
    public class Solution {
        public int TotalHammingDistance(int[] nums) {
            int len = nums.Length, total_hamming = 0;

            for(int i=0;i<32;i++)
            {
                int count = 0;
                for(int j=0;j<len;j++)
                {
                    count += (nums[j]>>i)&1;
                }
                total_hamming += count* (len-count);
            }
            
            return total_hamming;
        }
    }