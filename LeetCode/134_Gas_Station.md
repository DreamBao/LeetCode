# 134. Gas Station
Gas Station

## Code
    public class Solution {
        public int CanCompleteCircuit(int[] gas, int[] cost) {
            int length = gas.Length;
            int sumGas = 0;
            int res = 0;
            int total = 0;
            for(int i = 0; i < length; i ++) {
                sumGas += (gas[i] - cost[i]);
                if(sumGas < 0) {
                    total += sumGas;
                    sumGas = 0;
                    res = i + 1;
                }
            }
            total += sumGas;
            return total < 0 ? -1 : res;
        }
    }