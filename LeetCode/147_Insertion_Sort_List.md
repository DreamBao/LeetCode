# 147. Insertion Sort List
Insertion Sort List

## Code
    /**
    * Definition for singly-linked list.
    * public class ListNode {
    *     public int val;
    *     public ListNode next;
    *     public ListNode(int x) { val = x; }
    * }
    */
    public class Solution {
        public ListNode InsertionSortList(ListNode head) {
            if( head == null ){
                return head;
            }
            
            ListNode helper = new ListNode(0);
            ListNode cur = head; 
            ListNode pre = helper;
            ListNode next = null; 
            
            while( cur != null ){
                next = cur.next;
                while( pre.next != null && pre.next.val < cur.val ){
                    pre = pre.next;
                }
                cur.next = pre.next;
                pre.next = cur;
                pre = helper;
                cur = next;
            }
            
            return helper.next;
        }
    }