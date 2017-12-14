# 92. Reverse Linked List II
Reverse Linked List II


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
        public ListNode ReverseBetween(ListNode head, int m, int n) {
            ListNode preHead = new ListNode(0);
            preHead.next = head;
            ListNode pre = preHead;
            for(int i = 0; i < m - 1; i ++) {
                pre = pre.next;
            }
            
            ListNode start = pre.next;
            ListNode next = start.next;
            
            for(int i = 0; i < n - m; i ++) {
                start.next = next.next;
                next.next = pre.next;
                pre.next = next;
                next = start.next;
            }
            return preHead.next;
        }
    }