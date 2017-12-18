# 98. Validate Binary Search Tree
Validate Binary Search Tree


## Code
    //Simple
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
        public bool IsValidBST(TreeNode root) {
            return ValidBST(root, long.MinValue , long.MaxValue);
        }
        
        public bool ValidBST(TreeNode root, long left, long right) {
            if (root == null) return true;
            if (root.val >= right || root.val <= left) return false;
            return ValidBST(root.left, left, root.val) && ValidBST(root.right, root.val, right);   
        }
    }

    /** Error!!!!!!!!!!!!
    * Definition for a binary tree node.
    * public class TreeNode {
    *     public int val;
    *     public TreeNode left;
    *     public TreeNode right;
    *     public TreeNode(int x) { val = x; }
    * }
    */
    public class Solution {
        public bool IsValidBST(TreeNode root) {
            if(root == null)
                return true;
            return ValidBST(root, root.val , 0);
        }
        
        public bool ValidBST(TreeNode root, int rootVal, int n, bool isLeft = true) {
            bool result = true;
            if(n != 0)
                if(isLeft) {
                    if(root.val >= rootVal)
                        return false;
                }
                else {
                if(root.val <= rootVal)
                        return false;
                }
            
            if(root.left != null) {
                if(n == 0 || root.val < rootVal) {
                    isLeft = true;
                    rootVal = root.val;
                }
                
                
                result = result && ValidBST(root.left, rootVal, n+1, isLeft);
                if(root.left.val < root.val)
                    result = result && true;
                else 
                    result = result && false;
            }
            else 
                result = result && true;
            
            if(root.right != null) {
                if(n == 0 || root.val > rootVal) {
                    isLeft = false;
                    rootVal = root.val;
                }
        

                result = result && ValidBST(root.right, rootVal, n+1, isLeft);
                if(root.right.val > root.val)
                    result = result && true;
                else 
                    result = result && false;
            }
            else 
                result = result && true;
            
            return result;
                
        }
    }