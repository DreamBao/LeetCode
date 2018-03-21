# 382. Linked List Random Node
Linked List Random Node

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

        public List<ListNode> list;
        int count = 0;
        Random ran = new Random();
        /** @param head The linked list's head.
            Note that the head is guaranteed to be not null, so it contains at least one node. */
        public Solution(ListNode head) {
            ListNode temp = head;
            list = new List<ListNode>();
            while(temp != null) {
                
                list.Add(temp);
                temp = temp.next;
            }
        }
        
        /** Returns a random node's value. */
        public int GetRandom() {
            return list[ran.Next(0, list.Count)].val;
        }
    }

    /**
    * Your Solution object will be instantiated and called as such:
    * Solution obj = new Solution(head);
    * int param_1 = obj.GetRandom();
    */