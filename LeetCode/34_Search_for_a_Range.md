34. Search for a Range
Search for a Range

## Code
        public class Solution {
            public int[] SearchRange(int[] nums, int target) {
                List<int> list = new List<int>();
                int l = -1;
                int r = -1;
                for(int i = 0; i < nums.Length; i++) {
                    if(nums[i] == target) {
                        if(l == -1) {
                            l = i;
                            r = i;
                        }
                        else {
                            r = i;
                        }
                    }
                }
                list.Add(l);
                list.Add(r);

                return list.ToArray();
            }
        }