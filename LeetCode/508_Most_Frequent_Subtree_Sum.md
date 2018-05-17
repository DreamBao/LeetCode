# 508. Most Frequent Subtree Sum
Most Frequent Subtree Sum

## Code
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
        Dictionary<int, int> counts;
        // reset this whenever we get a new highest
        List<int> highests;
        int highest;
        
        public int[] FindFrequentTreeSum(TreeNode root) {
            counts = new Dictionary<int, int>();
            highests = new List<int>();    
            Sum(root);
            int[] tr = new int[highests.Count];
            for(int i = 0; i < tr.Length; i++) tr[i] = highests[i];
            return tr;
        }
        
        int Sum(TreeNode node){
            if(node == null) return 0;
            int sum = node.val + Sum(node.left) + Sum(node.right);
            int n = 1;
            if(counts.ContainsKey(sum)){
                n = counts[sum];
                counts[sum] = ++n;
            }else{
                counts.Add(sum, n);
            }
            if(n > highest){
                highests = new List<int>();
                highest = n;  
            }

            if(highest == n) highests.Add(sum);
            return sum;
            
        }
    }