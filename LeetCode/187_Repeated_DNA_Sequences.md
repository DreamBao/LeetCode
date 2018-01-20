# 187. Repeated DNA Sequences
Repeated DNA Sequences

## Code
    public class Solution {
        public IList<string> FindRepeatedDnaSequences(string s) {
            Dictionary<string, int> dic = new Dictionary<string, int>();
            IList<string> result = new List<string>();
            //List<string> clist = new List<string>();
            int len = s.Length;
            for(int i = 0; i + 9 < len; i ++) {
                string temp = s.Substring(i, 10);
                if(dic.ContainsKey(temp)) {
                    if(!result.Contains(temp))
                        result.Add(temp);
                }
                else {
                    dic.Add(temp, 1);
                }
            }
            return result;
        }
    }