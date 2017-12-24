# 109. Convert Sorted List to Binary Search Tree
Convert Sorted List to Binary Search Tree

## Code
    /**
    * Definition for singly-linked list.
    * public class ListNode {
    *     public int val;
    *     public ListNode next;
    *     public ListNode(int x) { val = x; }
    * }
    */
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
        
        public static ListNode node;
        
        public TreeNode SortedListToBST(ListNode head) {
            if(head == null){
                return null;
            }
            int size = 0;
            ListNode runner = head;
            Solution.node = head;

            while(runner != null){
                runner = runner.next;
                size ++;
            }

            return inorderHelper(0, size - 1);
        }
        
        
        public TreeNode inorderHelper(int start, int end){
            if(start > end){
                return null;
            }
            int mid = start + (end - start) / 2;
            TreeNode left = inorderHelper(start, mid - 1);

            TreeNode treenode = new TreeNode(Solution.node.val);
            treenode.left = left;
            Solution.node = Solution.node.next;

            TreeNode right = inorderHelper(mid + 1, end);
            treenode.right = right;

            return treenode;
        }
    }