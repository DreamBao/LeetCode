# 144. Binary Tree Preorder Traversal
Binary Tree Preorder Traversal

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
        public IList<int> PreorderTraversal(TreeNode root) {
            IList<int> result = new List<int>();
            GetPreorderTraversal(root, result);
            return result;
        }
        
        private void GetPreorderTraversal(TreeNode root, IList<int> result) {
            if(root != null)
                result.Add(root.val);
            else 
                return;
            GetPreorderTraversal(root.left, result);
            GetPreorderTraversal(root.right, result);
        }
        
    }