# 150. Evaluate Reverse Polish Notation
Evaluate Reverse Polish Notation

## Code
    public class Solution {
        public int EvalRPN(string[] tokens) {
            int result = 0;
            int i;
            Stack<int> opd = new Stack<int>();         
            int length = tokens.Length;
            for(i = 0; i < length; i ++)
            {
                if(tokens[i] == "*")
                {
                    int rOpd = opd.Peek();   
                    opd.Pop();
                    int lOpd = opd.Peek();  
                    opd.Pop();
                    result = lOpd * rOpd;
                    opd.Push(result);
                }
                else if(tokens[i] == "/")
                {
                    int rOpd = opd.Peek();
                    opd.Pop();
                    int lOpd = opd.Peek();
                    opd.Pop();
                    result = lOpd / rOpd;
                    opd.Push(result);
                }
                else if(tokens[i] == "+")
                {
                    int rOpd = opd.Peek();
                    opd.Pop();
                    int lOpd = opd.Peek();
                    opd.Pop();
                    result = lOpd + rOpd;
                    opd.Push(result);
                }
                else if(tokens[i] == "-")
                {
                    int rOpd = opd.Peek();
                    opd.Pop();
                    int lOpd = opd.Peek();
                    opd.Pop();
                    result = lOpd - rOpd;
                    opd.Push(result);
                }
                else
                {
                    opd.Push(int.Parse(tokens[i].ToString()));
                }
            }
            return opd.Peek();
        }
    }