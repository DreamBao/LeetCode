# 515. Find Largest Value in Each Tree Row
Find Largest Value in Each Tree Row

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
        public IList<int> LargestValues(TreeNode root) {
            Dictionary<int, int> dic = new Dictionary<int, int>();
            List<int> res = new List<int>();
            GetLargestValue(root, dic, 0);
            foreach(int val in dic.Values) {
                res.Add(val);
            }
            return res;
        }
        
        public void GetLargestValue(TreeNode node, Dictionary<int, int> dic, int level) {
            level ++;
            if(node == null)
                return;
            if(dic.ContainsKey(level)) {
                if(dic[level] < node.val) {
                    dic[level] = node.val;
                }
            }else {
                dic.Add(level, node.val);
            }
            GetLargestValue(node.left, dic, level);
            GetLargestValue(node.right, dic, level);
        }
    }