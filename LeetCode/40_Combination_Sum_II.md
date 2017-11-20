# 40. Combination Sum II
Combination Sum II

## Code
    public class Solution {
        public IList<IList<int>> CombinationSum2(int[] candidates, int target) {
            Array.Sort(candidates);
            IList<IList<int>> sumList = new List<IList<int>>();
            List<int> list = new List<int>();
            SearchDFS(candidates, 0, target, sumList, list);
            return sumList;
        }
        
        public void SearchDFS(int[] cand, int num, int target, IList<IList<int>> candidates, List<int> list) {
            if (target == 0) {
                candidates.Add(new List<int>(list));
                return ;
            }
            if (target < 0) return;
            for (int i = num; i < cand.Length; i++){
                if (i > num && cand[i] == cand[i-1]) continue;
                list.Add(cand[i]);
                SearchDFS(cand, i+1, target - cand[i], candidates, list);
                list.RemoveAt(list.Count-1);
            }
        }
        
    }