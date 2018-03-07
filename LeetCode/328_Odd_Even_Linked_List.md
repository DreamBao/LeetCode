# 328. Odd Even Linked List
Odd Even Linked List

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
        public ListNode OddEvenList(ListNode head) {
            if (head != null) {
                ListNode odd = head, even = head.next, evenHead = even; 
                while (even != null && even.next != null) {
                    odd.next = odd.next.next; 
                    even.next = even.next.next; 
                    odd = odd.next;
                    even = even.next;
                }
                odd.next = evenHead; 
            }
            return head;
        }
    }