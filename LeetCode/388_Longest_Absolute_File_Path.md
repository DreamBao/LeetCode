# 388. Longest Absolute File Path
Longest Absolute File Path

## Code
    public class Solution {
        public int LengthLongestPath(string input) {
            Stack<int> stack = new Stack<int>();
            stack.Push(0);
            int maxLen = 0;
            string[] str = input.Split('\n');
            foreach(string s in str){
                int lev = s.LastIndexOf("\t")+1;
                while(lev + 1 < stack.Count()) stack.Pop(); 
                int len = stack.Peek() + s.Length - lev + 1;
                stack.Push(len);
                // check if it is file
                if(s.Contains(".")) maxLen = Math.Max(maxLen, len - 1); 
            }
            return maxLen;
        }
    }