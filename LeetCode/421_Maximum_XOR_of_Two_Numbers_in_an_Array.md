# 421. Maximum XOR of Two Numbers in an Array
Maximum XOR of Two Numbers in an Array

## Code
    public class Solution {
        public int FindMaximumXOR(int[] nums) {
            int res = 0, mask = 0;
            for(int i = 31; i >= 0; i--){
                mask = mask | (1 << i);
                HashSet<int> set = new HashSet<int>();
                for(int j = 0; j < nums.Length; j ++){
                    int num = nums[j];                
                    set.Add(num & mask);
                }
                int tmp = res | (1 << i);
                foreach(int prefix in set){
                    if(set.Contains(tmp ^ prefix)) {
                        res = tmp;
                        break;
                    }
                }
            }
            return res;
        }
    }