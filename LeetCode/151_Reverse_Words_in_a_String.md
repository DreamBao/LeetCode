# 151. Reverse Words in a String
Reverse Words in a String

## Code
    public class Solution {
        public string ReverseWords(string s) {
            string result = "";
            string[] temp = s.Split(' ');
            List<string> tempList = new List<string>();
            
            for(int i = 0; i < temp.Length; i++) {
                if(string.IsNullOrEmpty(temp[i]) || temp[i] == " ")
                continue;
                tempList.Add(temp[i]);
            }
            
            if(tempList.Count == 0) {
                return "";
            }

            for(int i = tempList.Count - 1; i >= 0; i --) {
                result += tempList[i];
                if(i != 0)
                    result += " ";
            }
            return result;
        }
    }