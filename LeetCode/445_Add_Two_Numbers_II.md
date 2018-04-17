# 445. Add Two Numbers II
Add Two Numbers II

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
        public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
            Stack<int> s1 = new Stack<int>();
            Stack<int> s2 = new Stack<int>();
            
            while(l1 != null) {
                s1.Push(l1.val);
                l1 = l1.next;
            };
            while(l2 != null) {
                s2.Push(l2.val);
                l2 = l2.next;
            }
            
            int sum = 0;
            ListNode list = new ListNode(0);
            while (!(s1.Count == 0) || !(s2.Count == 0)) {
                if (!(s1.Count == 0)) sum += s1.Pop();
                if (!(s2.Count == 0)) sum += s2.Pop();
                list.val = sum % 10;
                ListNode head = new ListNode(sum / 10);
                head.next = list;
                list = head;
                sum /= 10;
            }
            
            return list.val == 0 ? list.next : list;
            
        }
    }