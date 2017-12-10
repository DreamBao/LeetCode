# 82. Remove Duplicates from Sorted List II
Remove Duplicates from Sorted List II


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
        public ListNode DeleteDuplicates(ListNode head) {
            if(head==null) return null;
            ListNode FakeHead=new ListNode(0);
            FakeHead.next=head;
            ListNode pre=FakeHead;
            ListNode cur=head;
            while(cur!=null){
                while(cur.next!=null&&cur.val==cur.next.val){
                    cur=cur.next;
                }
                if(pre.next==cur){
                    pre=pre.next;
                }
                else{
                    pre.next=cur.next;
                }
                cur=cur.next;
            }
            return FakeHead.next;
        }
    }