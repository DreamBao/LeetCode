# 95. Unique Binary Search Trees II
Unique Binary Search Trees II


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
        public IList<TreeNode> GenerateTrees(int n) {
            if(n == 0)
                return new List<TreeNode>();
            
            return AddTrees(1, n);
        }
        
        public List<TreeNode> AddTrees(int s, int e) {
            List<TreeNode> res = new List<TreeNode>();
            if (s > e) {
                res.Add(null); // empty tree
                return res;
            }

            for (int i = s; i <= e; i ++) {
                List<TreeNode> leftSubtrees = AddTrees(s, i - 1);
                List<TreeNode> rightSubtrees = AddTrees(i + 1, e);

                foreach (TreeNode left in leftSubtrees) {
                    foreach (TreeNode right in rightSubtrees) {
                        TreeNode root = new TreeNode(i);
                        root.left = left;
                        root.right = right;
                        res.Add(root);
                    }
                }
            }
            return res;
        }
    }