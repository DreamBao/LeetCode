# 173. Binary Search Tree Iterator
Binary Search Tree Iterator

## Code
    /**
    * Definition for binary tree
    * public class TreeNode {
    *     public int val;
    *     public TreeNode left;
    *     public TreeNode right;
    *     public TreeNode(int x) { val = x; }
    * }
    */

    public class BSTIterator {
        
        public static Stack<TreeNode> stack = new Stack<TreeNode>();
        
        public BSTIterator(TreeNode root) {
            while(root != null) {
                BSTIterator.stack.Push(root);
                root = root.left;
            }
        }

        /** @return whether we have a next smallest number */
        public bool HasNext() {
            return (BSTIterator.stack.Count != 0);
        }

        /** @return the next smallest number */
        public int Next() {
            TreeNode node = stack.Pop();
            if(node.right != null) {
                TreeNode rightNode = node.right;
                while(rightNode != null) {
                    BSTIterator.stack.Push(rightNode);
                    rightNode = rightNode.left;
                }
            }
            
            return node.val;
        }
    }

    /**
    * Your BSTIterator will be called like this:
    * BSTIterator i = new BSTIterator(root);
    * while (i.HasNext()) v[f()] = i.Next();
    */