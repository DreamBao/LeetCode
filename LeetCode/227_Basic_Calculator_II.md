# 227. Basic Calculator II
Basic Calculator II

## Code
    public class Solution {
        public int Calculate(string s) {
            int len;
            if(s == null || (len = s.Length)==0) return 0;
            Stack<int> stack = new Stack<int>();
            int num = 0;
            char sign = '+';
            for(int i=0;i<len;i++){
                if(char.IsDigit(s[i])){
                    num = num*10+s[i]-'0';
                }
                if((!char.IsDigit(s[i]) &&' '!=s[i]) || i==len-1){
                    if(sign=='-'){
                        stack.Push(-num);
                    }
                    if(sign=='+'){
                        stack.Push(num);
                    }
                    if(sign=='*'){
                        stack.Push(stack.Pop()*num);
                    }
                    if(sign=='/'){
                        stack.Push(stack.Pop()/num);
                    }
                    sign = s[i];
                    num = 0;
                }
            }

            int re = 0;
            for(int i = 0; i < stack.Count; i ++){
                re += stack.ElementAt(i);
            }
            return re;
        }
    }