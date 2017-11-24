# 49. Group Anagrams
Group Anagrams

## Code
    public class Solution {
        public IList<IList<string>> GroupAnagrams(string[] strs) {
            Dictionary<string, List<string>> dic = new Dictionary<string, List<string>>();
            IList<IList<string>> result = new List<IList<string>>();
            
            for(int i = 0; i < strs.Length; i ++) {
                string str = strs[i];
                char[] cs = str.ToCharArray();
                Array.Sort(cs);
                str = new string(cs);
                if(!dic.ContainsKey(str))
                    dic.Add(str, new List<string>(){strs[i]});
                else 
                    dic[str].Add(strs[i]);
            }
            foreach(List<string> list in dic.Values)
                result.Add(list);
            return result;
        }
    }