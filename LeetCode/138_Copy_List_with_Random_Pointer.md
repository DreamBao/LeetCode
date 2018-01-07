# 138. Copy List with Random Pointer
Copy List with Random Pointer

## Code
    /**
    * Definition for singly-linked list with a random pointer.
    * public class RandomListNode {
    *     public int label;
    *     public RandomListNode next, random;
    *     public RandomListNode(int x) { this.label = x; }
    * };
    */
    public class Solution {
        public RandomListNode CopyRandomList(RandomListNode head) {
            RandomListNode result = null;
            Dictionary<int,RandomListNode> dic = new Dictionary<int, RandomListNode>();
            result = DeepCopyRandomList(head, dic);
            return result;
        }
        
        public RandomListNode DeepCopyRandomList(RandomListNode head, Dictionary<int, RandomListNode> contain) {
            if(head == null)
                return null;
            if(contain.ContainsKey(head.label))
                return contain[head.label];
            
            RandomListNode copy = new RandomListNode(head.label);
            contain.Add(copy.label, copy);
            
            if(head.next != null) {
                copy.next = DeepCopyRandomList(head.next, contain);
            }
            if(head.random != null) {
                copy.random = DeepCopyRandomList(head.random, contain);
            }
            return copy;      
        }
        
    }