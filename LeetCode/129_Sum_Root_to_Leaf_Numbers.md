# 129. Sum Root to Leaf Numbers
Sum Root to Leaf Numbers

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
        public static int result = 0;
        
        public int SumNumbers(TreeNode root) {
            if(root == null)
                return 0;
            if(root.left == null && root.right == null)
                return root.val;
            Solution.result = 0;
            GetSum(root, "");
            return Solution.result;
        }
        
        public void GetSum(TreeNode root, string str) {
            if(root == null)
                return;
            if(root.left == null && root.right == null) {
                str += root.val;
                if(!string.IsNullOrEmpty(str))
                    Solution.result += int.Parse(str);
                return;
            }

            str += root.val;
            GetSum(root.left, str);
            GetSum(root.right, str);
        }
    }