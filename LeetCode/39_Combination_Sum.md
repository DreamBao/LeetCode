# 39. Combination Sum I
Combination Sum I

## Code
    public class Solution {
        public IList<IList<int>> CombinationSum(int[] candidates, int target) {
            Array.Sort(candidates);
            IList<IList<int>> sumList = new List<IList<int>>();
            List<int> list = new List<int>();
            SearchDFS(candidates, 0, target, sumList, list);
            return sumList;
        }
        
        public void SearchDFS(int[] cand, int num, int target, IList<IList<int>> candidates, List<int> list) {
            if(target < 0)
                return;
            if(target == 0) {
                candidates.Add(new List<int>(list));
                return;
            }
            
            for(int i = num; i < cand.Length; i++) {
                list.Add(cand[i]);
                SearchDFS(cand, i, target - cand[i], candidates, list);
                list.RemoveAt(list.Count-1);
            }
        }
    }