# 103. Binary Tree Zigzag Level Order Traversal
Binary Tree Zigzag Level Order Traversal


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
        public IList<IList<int>> ZigzagLevelOrder(TreeNode root) {
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
            
            if(n % 2 == 0)
                result[n].Add(root.val);
            else 
                result[n].Insert(0, root.val);

            AddLevelOrder(result, root.left, n + 1);
            AddLevelOrder(result, root.right, n + 1);
        }
    }