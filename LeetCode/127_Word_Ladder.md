# 127. Word Ladder
Word Ladder

## Code
    public class Solution {
        public int LadderLength(string beginWord, string endWord, IList<string> wordList) {
    //         if(!wordList.Contains(endWord))
    //             return 0;
    //         List<string> list = new List<string>(); 
    //         int length = beginWord.Length;
    //         int result = 1;
    //         string temp = beginWord;
    //         int equalLetter = 0;
    //         while(temp != endWord) {
    //             equalLetter = 0;
    //             for (int k = 0; k < length; k ++)
    //             {
    //                 if (temp[k] == endWord[k])
    //                     equalLetter++;
    //             }
    //             if(equalLetter >= length - 1)
    //             {
    //                 result++;
    //                 break;
    //             }
    //             equalLetter = 0;

    //             for(int i = 0; i < wordList.Count; i++) { 
    //                 equalLetter = 0;
    //                 for(int j = 0; j < length; j ++) {
    //                     if(temp[j] == wordList[i][j])
    //                         equalLetter++;
    //                 }
                    
    //                 if(equalLetter == length - 1) {
    //                     temp = wordList[i];
    //                     wordList.Remove(wordList[i]);
    //                     result++;
    //                     break;
    //                 }
                    
    //                 if(i == wordList.Count - 1)
    //                     return 0;
    //             }
    //         }
    //         return result;
            List<string> dict = new List<string>(wordList);
            List<string> qs = new List<string>();
            List<string> qe = new List<string>();
            List<string> vis = new List<string>();
            qs.Add(beginWord);
            if (dict.Contains(endWord)) qe.Add(endWord); // all transformed words must be in dict (including endWord)
            for (int len = 2; !(qs.Count == 0); len++) {
                List<String> nq = new List<string>();
                foreach (string w in qs) {
                    for (int j = 0; j < w.Length; j++) {
                        char[] ch = w.ToCharArray();
                        for (char c = 'a'; c <= 'z'; c++) {
                            if (c == w[j]) continue; // beginWord and endWord not the same, so bypass itself
                            ch[j] = c;
                            string nb = ch.ToString();
                            if (qe.Contains(nb)) return len; // meet from two ends
                            if (dict.Contains(nb) && !vis.Contains(nb))  {
                                vis.Add(nb);
                                nq.Add(nb); // not meet yet, vis is safe to use
                            }
                        }
                    }
                }
                qs = (nq.Count < qe.Count) ? nq : qe; // switch to small one to traverse from other end
                qe = (qs == nq) ? qe : nq;
            }
            return 0;
        }
    }