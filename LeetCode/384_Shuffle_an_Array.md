# 384. Shuffle an Array
Shuffle an Array

## Code
    public class Solution {
        int[] oriNums;
        int[] nums;
        Random ran = new Random();
        public Solution(int[] nums) {
            this.nums = nums;
            this.oriNums = nums;
        }
        
        /** Resets the array to its original configuration and return it. */
        public int[] Reset() {
            return oriNums;
        }
        
        /** Returns a random shuffling of the array. */
        public int[] Shuffle() {
            if(nums == null) return null;
            int[] a = (int[])nums.Clone();
            for(int j = 1; j < a.Length; j++) {
                int i = ran.Next(j + 1);
                swap(a, i, j);
            }
            return a;
        }
        
        public void swap(int[] a, int i, int j) {
            int t = a[i];
            a[i] = a[j];
            a[j] = t;
        }
    }

    /**
    * Your Solution object will be instantiated and called as such:
    * Solution obj = new Solution(nums);
    * int[] param_1 = obj.Reset();
    * int[] param_2 = obj.Shuffle();
    */