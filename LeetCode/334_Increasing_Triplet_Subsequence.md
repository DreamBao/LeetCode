# 334. Increasing Triplet Subsequence
Increasing Triplet Subsequence

## Code
    public class Solution {
        public bool IncreasingTriplet(int[] nums) {
            int min = int.MaxValue, secondMin = int.MaxValue;
            foreach(int num in nums){
                if(num <= min) min = num;
                else if(num < secondMin) secondMin = num;
                else if(num > secondMin) return true;
            }
            return false;
        }
    }