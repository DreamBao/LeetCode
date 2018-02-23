# 241. Different Ways to Add Parentheses
Different Ways to Add Parentheses

## Code
    public class Solution {
        public IList<int> DiffWaysToCompute(string input) {
            IList<int> res = new List<int>();
            for (int i = 0; i < input.Length; i++) {
                char c = input[i];
                if (c == '-' || c == '+' || c == '*') {
                    string a = input.Substring(0, i);
                    string b = input.Substring(i + 1);
                    IList<int> al = DiffWaysToCompute(a);
                    IList<int> bl = DiffWaysToCompute(b);
                    foreach (int x in al) {
                        foreach (int y in bl) {
                            if (c == '-') {
                                res.Add(x - y);
                            } else if (c == '+') {
                                res.Add(x + y);
                            } else if (c == '*') {
                                res.Add(x * y);
                            }
                        }
                    }
                }
            }
            if (res.Count == 0) res.Add(int.Parse(input));
            return res;
        }
    }