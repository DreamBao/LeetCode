# 142. Linked List Cycle II
Linked List Cycle II

## Code
    /**
    * Definition for singly-linked list.
    * public class ListNode {
    *     public int val;
    *     public ListNode next;
    *     public ListNode(int x) {
    *         val = x;
    *         next = null;
    *     }
    * }
    */
    public class Solution {
        public ListNode DetectCycle(ListNode head) {
            // //List<int> list = new List<ListNode>();
            // Dictionary<int, ListNode> dic = new Dictionary<int, ListNode>();
            // Dictionary<int, int> preDic = new Dictionary<int, int>();
            // ListNode temp = head;
            // ListNode result = null;
            // while(temp != null) {
            //     if(dic.ContainsKey(temp.val)) {
            //         result = dic[preDic[temp.val]];
            //         return result;
            //     }
            //     dic.Add(temp.val, temp);
            //     if(temp.next != null && !preDic.ContainsKey(temp.next.val))
            //         preDic.Add(temp.next.val, temp.val);
            //     temp = temp.next;
            // }
            // return null;
            
            ListNode slow = head;
            ListNode fast = head;

            while (fast!=null && fast.next!=null){
                fast = fast.next.next;
                slow = slow.next;

                if (fast == slow){
                    ListNode slow2 = head; 
                    while (slow2 != slow){
                        slow = slow.next;
                        slow2 = slow2.next;
                    }
                    return slow;
                }
            }
            return null;
        }
    }