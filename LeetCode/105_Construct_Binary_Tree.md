# 105. Construct Binary Tree from Preorder and Inorder Traversal
Construct Binary Tree from Preorder and Inorder Traversal


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
        public TreeNode BuildTree(int[] preorder, int[] inorder) {
            return BuildeBinTree(0, 0, inorder.Length - 1, preorder, inorder);
        }
        
        public TreeNode BuildeBinTree(int preStart, int inStart, int inEnd, int[] preorder, int[] inorder) {
            if (preStart > preorder.Length - 1 || inStart > inEnd) {
                return null;
            }
            TreeNode root = new TreeNode(preorder[preStart]);
            int inIndex = 0; // Index of current root in inorder
            for (int i = inStart; i <= inEnd; i++) {
                if (inorder[i] == root.val) {
                    inIndex = i;
                }
            }
            root.left = BuildeBinTree(preStart + 1, inStart, inIndex - 1, preorder, inorder);
            root.right = BuildeBinTree(preStart + inIndex - inStart + 1, inIndex + 1, inEnd, preorder, inorder);
            return root;
        }
    }