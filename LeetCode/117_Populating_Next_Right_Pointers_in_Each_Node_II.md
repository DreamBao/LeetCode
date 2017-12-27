# 117. Populating Next Right Pointers in Each Node II
Populating Next Right Pointers in Each Node II

## Code
    /**
    * Definition for binary tree with next pointer.
    * public class TreeLinkNode {
    *     int val;
    *     TreeLinkNode left, right, next;
    *     TreeLinkNode(int x) { val = x; }
    * }
    */
    public class Solution {
        public void connect(TreeLinkNode root) {
            TreeLinkNode level_start=root;

            while(level_start != null){
                TreeLinkNode cur=level_start;
                level_start = null;
                TreeLinkNode child = null;
                while(cur!=null){             
    //                 if(child == null) {
    //                     if(cur.left != null) {
    //                         child = cur.left;
    //                         if(level_start == null)
    //                             level_start = cur.left;
    //                     }
    //                     if(cur.right != null) {
    //                         child = cur.right;
    //                         if(level_start == null)
    //                             level_start = cur.right;
    //                     }      
    //                 }
                    
    //                 if(child != null) {
    //                      if(cur.left != null) {
    //                         child.next = cur.left;
    //                         child = cur.left;
    //                      }

    //                      if(cur.right != null) {
    //                         child.next = cur.right;
    //                         child = cur.right;
    //                      }
    //                 }
                    
    //                 cur=cur.next;
                    
                    if (cur.left != null) {
                        if (child != null) {
                            child.next = cur.left;
                        } else {
                            level_start = cur.left;
                        }
                        child = cur.left;
                    }
                    //right child
                    if (cur.right != null) {
                        if (child != null) {
                            child.next = cur.right;
                        } else {
                            level_start = cur.right;
                        }
                        child = cur.right;
                    }
                    //move to next node
                    cur = cur.next;
                }

            }   
        }
    }