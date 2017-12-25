# 113. Path Sum II
Path Sum II

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
        public IList<IList<int>> PathSum(TreeNode root, int sum) {
            int tempSum = 0;
            IList<IList<int>> result = new List<IList<int>>();
            List<int> temp = new List<int>();
            if(root == null) {
                //result.Add();
                return result;
            }
            
            if(root.left == null && root.right == null) {
                if(root.val == sum) {
                    temp.Add(root.val);
                    result.Add(temp);
                    return result;
                }
            }
            
            GetPathSum(result, temp, root, sum, tempSum, 0);
            return result;
        }
        
        public void GetPathSum(IList<IList<int>> result, List<int> temp, TreeNode root, int sum, int tempSum, int count) {
            if(root == null) {
                if(tempSum == sum && count > 1) {
                    result.Add(new List<int>(temp));
                }
                return;
            }
            count ++;
            tempSum += root.val;
            temp.Add(root.val);
            
            if(root.left == null && root.right == null) {
                GetPathSum(result, new List<int>(temp), root.left, sum, tempSum,count);
            }
            else {
                if(root.left != null)
                    GetPathSum(result, new List<int>(temp), root.left, sum, tempSum,count);
                if(root.right != null)
                    GetPathSum(result, new List<int>(temp), root.right, sum, tempSum,count);
            }
        }
    }