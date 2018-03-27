# 394. Decode String
Decode String

## Code
    public class Solution {
        public string DecodeString(string s) {
            Stack<int> count = new Stack<int>();
            Stack<string> result = new Stack<string>();
            int i = 0;
            result.Push("");
            while (i < s.Length) {
                char ch = s[i];
                if (ch >= '0' && ch <= '9') {
                    int start = i;
                    while (s[i + 1] >= '0' && s[i + 1] <= '9') i++;
                    count.Push(int.Parse(s.Substring(start, i + 1 - start)));
                } else if (ch == '[') {
                    result.Push("");
                } else if (ch == ']') {
                    string str = result.Pop();
                    string sb = "";
                    int times = count.Pop();
                    for (int j = 0; j < times; j += 1) {
                        sb += str;
                    }
                    result.Push(result.Pop() + sb.ToString());
                } else {
                    result.Push(result.Pop() + ch);
                }
                i += 1;
            }
            return result.Pop();
        }
    }