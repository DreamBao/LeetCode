# 106. Construct Binary Tree from Inorder and Postorder Traversal
Construct Binary Tree from Inorder and Postorder Traversal

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
        public TreeNode BuildTree(int[] inorder, int[] postorder) {
            return BuildBinTree(inorder, postorder, 0, inorder.Length - 1, 0, postorder.Length - 1);
        }
        
        public TreeNode BuildBinTree(int[] inorder, int[] postorder, int istart, int ie, int ps, int pe){
            if(ps > pe){
                return null;
            }
            TreeNode node = new TreeNode(postorder[pe]);
            int pos = 0;
            for(int i = istart; i <= ie; i++){
                if(inorder[i] == node.val){
                    pos = i;
                    break;
                }
            }
            node.left = BuildBinTree(inorder, postorder, istart, pos - 1, ps, ps + pos - istart - 1);
            node.right = BuildBinTree(inorder, postorder, pos + 1, ie, pe - ie + pos, pe - 1);
            return node;
        }
    }