# 133. Clone Graph
Clone Graph

## Code
    /**
    * Definition for undirected graph.
    * public class UndirectedGraphNode {
    *     public int label;
    *     public IList<UndirectedGraphNode> neighbors;
    *     public UndirectedGraphNode(int x) { label = x; neighbors = new List<UndirectedGraphNode>(); }
    * };
    */
    public class Solution {
        public UndirectedGraphNode CloneGraph(UndirectedGraphNode node) {
            UndirectedGraphNode result = null;
            Dictionary<int, UndirectedGraphNode> containDic = new Dictionary<int, UndirectedGraphNode>();
            result = DFSCloneGraph(node, result, containDic);
            return result;
        }
        
        
        public UndirectedGraphNode DFSCloneGraph(UndirectedGraphNode node, UndirectedGraphNode copyNode, Dictionary<int, UndirectedGraphNode> containDic) 
        {
            if(node == null)
                return null;
            
            if(containDic.ContainsKey(node.label))
                return containDic[node.label];
            
            copyNode = new UndirectedGraphNode(node.label);
            containDic.Add(copyNode.label, copyNode);
            if(node.neighbors != null) {
                copyNode.neighbors = new List<UndirectedGraphNode>();
                for(int i = 0; i < node.neighbors.Count; i ++) {
                    UndirectedGraphNode neigborNode = null;
                    neigborNode = DFSCloneGraph(node.neighbors[i], neigborNode, containDic);
                    if(neigborNode != null)
                        copyNode.neighbors.Add(neigborNode);
                }
            }
            return copyNode;
        }
    }