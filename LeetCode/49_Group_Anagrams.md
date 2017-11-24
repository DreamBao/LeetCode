# 49. Group Anagrams
Group Anagrams

## Code
I:
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

II(Stupid):
    public class Solution {
        public IList<IList<string>> GroupAnagrams(string[] strs) {
            IList<IList<string>> result = new List<IList<string>>();
            List<string> list = new List<string>();
            List<int> nums = new List<int>();
            List<string> nullList = new List<string>();
            
            for(int i = 0; i < strs.Length; i ++) {
                string str = strs[i];
                if(str == "0")
                    continue;
                
                if(strs[i] == "") {
                    nullList.Add(strs[i]);
                    strs[i] = "0";
                    //nums.Add(i);
                    continue;
                }
                
                list.Add(str);
                strs[i] = "0";
                //nums.Add(i);
                    
                for(int j = 0; j < strs.Length; j ++) {
                    if(strs[j] == "0")
                        continue;
                    bool t = true;
                    string s = str;
                    for(int k = 0; k < strs[j].Length; k ++) {
                        if(!s.Contains(strs[j][k]))
                            t = false;
                        else 
                            s = s.Remove(s.IndexOf(strs[j][k]), 1);
                    }
                    if(t && str.Length == strs[j].Length) {
                        list.Add(strs[j]);
                        strs[j] = "0";
                        //nums.Add(j);
                    }
                }
                result.Add(new List<string>(list));
                list.Clear();
            }
            if(nullList.Count != 0)
                result.Add(nullList);
            return result;
        }
    }