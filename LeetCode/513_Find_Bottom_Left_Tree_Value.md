# 513. Find Bottom Left Tree Value
Find Bottom Left Tree Value

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
        
        public int FindBottomLeftValue(TreeNode root) {
            return GetLeftMost(root, 1, new int[]{0,0});
        }

        public int GetLeftMost(TreeNode root, int depth, int[] res) {
            if (res[1] < depth) 
            {
                res[0] = root.val;
                res[1] = depth;
            }
            if (root.left != null) GetLeftMost(root.left, depth + 1, res);
            if (root.right != null) GetLeftMost(root.right, depth + 1, res);
            return res[0];
        }
    }