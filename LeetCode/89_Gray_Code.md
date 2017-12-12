# 89. Gray Code
Gray Code


## Code
    public class Solution {
        public IList<int> GrayCode(int n) {
            IList<int> rs=new List<int>();
            rs.Add(0);
            for(int i=0;i<n;i++){
                int size=rs.Count;
                for(int k=size-1;k>=0;k--)
                    rs.Add(rs[k] | 1<<i);
            }
            return rs;
        }
    }