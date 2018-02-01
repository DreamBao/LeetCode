# 222. Count Complete Tree Nodes
Count Complete Tree Nodes

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
        public int CountNodes(TreeNode root) {
            int h = GetHeight(root);
            return h < 0 ? 0 :
                GetHeight(root.right) == h - 1 ? (1 << h) + CountNodes(root.right)
                                            : (1 << h-1) + CountNodes(root.left);
        }
        
        
        public int GetHeight(TreeNode root) {
            return root == null ? -1 : 1 + GetHeight(root.left);
        }
    }