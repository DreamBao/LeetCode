# 454. 4Sum II
4Sum II

## Code
    public class Solution {
        public int FourSumCount(int[] A, int[] B, int[] C, int[] D) {
            Dictionary<int, int> dic = new Dictionary<int, int>();
        
            for(int i=0; i<C.Length; i++) {
                for(int j=0; j<D.Length; j++) {
                    int sum = C[i] + D[j];
                    if(dic.ContainsKey(sum)) {
                        dic[sum] ++;
                    }else {
                        dic.Add(sum, 1);
                    }
                }
            }

            int res=0;
            for(int i=0; i<A.Length; i++) {
                for(int j=0; j<B.Length; j++) {
                    if(dic.ContainsKey(-1 * (A[i]+B[j]))) {
                        res += dic[-1 * (A[i]+B[j])];
                    }
                }
            }
            return res;
        }
    }