# 433. Minimum Genetic Mutation
Minimum Genetic Mutation

## Code
    public class Solution {
        public int MinMutation(string start, string end, string[] bank) {
            if(start == end) return 0;
            
            HashSet<string> bankSet = new HashSet<string>();
            foreach(string b in bank) bankSet.Add(b);
            
            char[] charSet = new char[]{'A', 'C', 'G', 'T'};
            
            int level = 0;
            HashSet<string> visited = new HashSet<string>();
            Queue<string> queue = new Queue<string>();
            queue.Enqueue(start);
            visited.Add(start);
            
            while(!(queue.Count == 0)) {
                int size = queue.Count;
                while(size > 0) {
                    size = size - 1;
                    string curr = queue.Dequeue();
                    if(curr == end) return level;
                    
                    char[] currArray = curr.ToCharArray();
                    for(int i = 0; i < currArray.Length; i++) {
                        char old = currArray[i];
                        foreach(char c in charSet) {
                            currArray[i] = c;
                            string next = new string(currArray);
                            if(!visited.Contains(next) && bankSet.Contains(next)) {
                                visited.Add(next);
                                queue.Enqueue(next);
                            }
                        }
                        currArray[i] = old;
                    }
                }
                level++;
            }
            
            return -1;
        }
    }