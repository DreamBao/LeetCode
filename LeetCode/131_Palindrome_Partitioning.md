# 131. Palindrome Partitioning
Palindrome Partitioning

## Code
    public class Solution {
        public IList<IList<string>> Partition(string s) {
            IList<IList<string>> result = new List<IList<string>>();
            List<string> temp = new List<string>();
            DFSPartition(s, 0, result, temp);
            return result;
        }
        
        private void DFSPartition(String s, int l, IList<IList<string>> resultList, List<string> curList){
            if(curList.Count > 0 && l >= s.Length){
                    List<String> a = new List<string>(curList);
                    resultList.Add(a);
            }
            
            for(int i = l ;i < s.Length; i ++){
                string tempStr = s.Substring(l, i + 1 - l);
                if(IsPalindrome(tempStr)){
                    if(l == i)
                        curList.Add(s[i].ToString());
                    else
                        curList.Add(s.Substring(l, i + 1 - l));
                    DFSPartition(s, i + 1, resultList, curList);
                    curList.RemoveAt(curList.Count - 1);
                }
            }
        }
        
        private bool IsPalindrome(string str) {
            int i  = 0, j = str.Length - 1;
            bool isPalindrome = true;
            while(i < j) {
                if(str[i] != str[j]) {
                    isPalindrome = false;
                    break;
                }
                i ++;
                j --;
            }
            return isPalindrome;
        }
    }