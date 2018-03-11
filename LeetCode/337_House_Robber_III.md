# 337. House Robber III
House Robber III

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
        public int Rob(TreeNode root) {
            int[] num = Dfs(root);
            return Math.Max(num[0], num[1]);
        }
        private int[] Dfs(TreeNode x) {
            if (x == null) return new int[2];
            int[] left = Dfs(x.left);
            int[] right = Dfs(x.right);
            int[] res = new int[2];
            res[0] = left[1] + right[1] + x.val;
            res[1] = Math.Max(left[0], left[1]) + Math.Max(right[0], right[1]);
            return res;
        }
    }