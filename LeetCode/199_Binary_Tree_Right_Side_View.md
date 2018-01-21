# 199. Binary Tree Right Side View
Binary Tree Right Side View

## Code
    /**
    * Definition for a binary tree node.
    * public class TreeNode {
    *     public int val;
    *     public TreeNode left;
    *     public TreeNode right;
    *     public TreeNode(int x) { val = x; }
    * }
    */
    public class Solution {
        public IList<int> RightSideView(TreeNode root) {
            IList<int> result = new List<int>();
            Dictionary<int, List<int>> dic = new Dictionary<int, List<int>>();
            SearchLevelTree(root, dic, 1);
            foreach(var d in dic) {
                List<int> temp = d.Value;
                result.Add(temp[temp.Count - 1]);
            }
            return result;
        }
        
        
        public void SearchLevelTree(TreeNode root, Dictionary<int, List<int>> dic, int level) {
            if(root == null)
                return;
            
            if(dic.ContainsKey(level)) {
                dic[level].Add(root.val);
            } else {
                List<int> temp = new List<int>();
                temp.Add(root.val);
                dic.Add(level, temp);
            }
            
            SearchLevelTree(root.left, dic, level + 1);
            SearchLevelTree(root.right, dic, level + 1);
        }
    }