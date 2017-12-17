# 94. Binary Tree Inorder Traversal
Binary Tree Inorder Traversal


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
        public IList<int> InorderTraversal(TreeNode root) {
            IList<int> result = new List<int>();
            TraversalTree(result, root);
            return result;
        }
        
        public void TraversalTree(IList<int> temp, TreeNode root) {
            if(root == null)
                return;

            TraversalTree(temp,root.left);
            temp.Add(root.val);
            TraversalTree(temp,root.right);
        }
        
    }