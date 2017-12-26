# 114. Flatten Binary Tree to Linked List
Flatten Binary Tree to Linked List

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
        
        public static TreeNode tempNode = null;
        
        public void Flatten(TreeNode root) {
            if(root == null)
                return;
            TreeNode result = new TreeNode(1);
            GetFlatten(root);
        }
        
        public void GetFlatten(TreeNode root) {
            if(root == null)
                return;
            
            if(tempNode != null) {
                tempNode.left = null;
                tempNode.right = root;
            }
            TreeNode right = root.right;
            Solution.tempNode = root;
            GetFlatten(root.left);
            GetFlatten(right);
        }
    }