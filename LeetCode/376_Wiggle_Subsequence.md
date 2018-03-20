# 376. Wiggle Subsequence
Wiggle Subsequence

## Code
    public class Solution {
        public int WiggleMaxLength(int[] nums) {
            int len = nums.Length;
            
            if(len <= 1){
                return len;
            }

            int[] wiggle = new int[len-1];
            int wiggle_len = len ;
            int j = 0;
            for(int i = 1; i < len; i++){
                int num = nums[i] - nums[i - 1];
                if(num != 0){
                    wiggle[j] = num;
                    j++;
                }
                if(num == 0){
                    wiggle_len--;
                }
            }

            for(int k = 0; k < j-1; k++){
                if(wiggle[k] * wiggle[k+1] > 0 ){
                    wiggle_len--;
                }
            }

            return wiggle_len;
        }
    }