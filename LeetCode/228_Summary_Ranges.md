# 228. Summary Ranges
Summary Ranges

## Code
    public class Solution {
        public IList<string> SummaryRanges(int[] nums) {
            string temp = "";
            IList<string> result = new List<string>();
            
            for(int i = 0; i < nums.Length; i ++) {
                if(temp == "") {
                    temp += nums[i];
                    continue;
                }    
                
                if((nums[i] - 1) == nums[i - 1]) {
                    if(i == nums.Length - 1) {
                        temp =temp + "->" + nums[i];
                    }   
                    continue;
                }
                else {
                    if(temp != (nums[i - 1] + ""))
                        temp = temp + "->" + nums[i - 1];
                    result.Add(temp);
                    temp = "" + nums[i];
                }
            }
            
            if(temp != "") {
                result.Add(temp);
                temp = "";
            }
            
            return result;
        }
    }