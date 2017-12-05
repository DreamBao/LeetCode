# 71. Simplify Path
Simplify Path


## Code
    public class Solution {
        public string SimplifyPath(string path) {
            Stack<string> stack = new Stack<string>();
            List<string> skipStr = new List<string>(){"..",".",""};
            foreach (String str in path.Split('/')){
                if (str == ".." && !(stack.Count == 0)) stack.Pop();
                else if (!skipStr.Contains(str)) stack.Push(str);
            }
            String res = "";
            foreach (String str in stack) res = "/" + str + res;
            return string.IsNullOrEmpty(res) ? "/" : res;
        }
    }