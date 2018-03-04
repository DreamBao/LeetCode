# 313. Super Ugly Number
Super Ugly Number

## Code
    public class Solution {
        public int NthSuperUglyNumber(int n, int[] primes) {
            int[] pointer = new int[primes.Length];
            int[] ugly = new int[n];
            ugly[0] = 1;
            for(int i = 1; i < n; i ++){
            int min = int.MaxValue;
            int minIndex = 0;
            for(int j = 0; j < primes.Length; j++){
                if(ugly[pointer[j]] * primes[j] < min){
                    min = ugly[pointer[j]] * primes[j];
                    minIndex = j;
                }else if(ugly[pointer[j]] * primes[j] == min){
                    pointer[j]++;
                }
            }
            ugly[i] = min;
            pointer[minIndex]++;
            }
            return ugly[n - 1];
        }
    }