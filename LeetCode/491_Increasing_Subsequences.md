# 491. Increasing Subsequences
Increasing Subsequences

## Code
    public class Solution {
        public IList<IList<int>> FindSubsequences(int[] nums) {
            var dict = new Dictionary<int, List<IList<int>>>();
            var result = new List<IList<int>>();
            for (var i = nums.Length - 1; i >= 0; i--)
            {
                List<IList<int>> subResult;
                if (!dict.TryGetValue(nums[i], out subResult))
                {
                    subResult = new List<IList<int>>();
                    dict[nums[i]] = subResult;
                }
                var list = new HashSet<int>();
                for (var j = i + 1; j< nums.Length; j++)
                {
                    if (nums[j] >= nums[i])
                        list.Add(nums[j]);
                }
                
                var originalSize = dict[nums[i]].Count;
                foreach(var item in list)
                {
                    var itemResult = dict[item];
                    var size = itemResult.Count;
                    if (item == nums[i])
                        size = originalSize;
                    var solution = new List<int>();
                    solution.Add(nums[i]);
                    solution.Add(item);
                    subResult.Add(solution);

                    for(var k = 0; k<size; k++)
                    {
                        solution = new List<int>();
                        solution.Add(nums[i]);
                        solution.AddRange(itemResult[k]);
                        subResult.Add(solution);
                    }
                    
                    if (item == nums[i])
                        subResult.RemoveRange(0, originalSize);
                }
            }
            
            foreach(var res in dict.Values)
                result.AddRange(res);
            
            return result;
            
        }

    }