# 102. Binary Tree Level Order Traversal
Binary Tree Level Order Traversal


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
        public IList<IList<int>> LevelOrder(TreeNode root) {
            IList<IList<int>> result = new List<IList<int>>();
            AddLevelOrder(result, root, 0);
            return result;
        }
        
        public void AddLevelOrder(IList<IList<int>> result, TreeNode root, int n) {
            if(root == null)
                return;
            if(n > result.Count - 1) {
                result.Add(new List<int>());
            }
            
            result[n].Add(root.val);
            AddLevelOrder(result, root.left, n + 1);
            AddLevelOrder(result, root.right, n + 1);
            
        }
        
    }