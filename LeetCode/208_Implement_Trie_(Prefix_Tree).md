# 208. Implement Trie (Prefix Tree)
Implement Trie (Prefix Tree)

## Code
    public class TrieNode {
        public char val;
        public bool isWord; 
        public TrieNode[] children = new TrieNode[26];
        public TrieNode() {}
        public TrieNode(char c){
            TrieNode node = new TrieNode();
            node.val = c;
        }
    }

    public class Trie {
        private TrieNode root;
        /** Initialize your data structure here. */
        public Trie() {
            root = new TrieNode();
            root.val = ' ';
        }
        
        /** Inserts a word into the trie. */
        public void Insert(string word) {
            TrieNode tn = root;
            for(int i = 0; i < word.Length; i++){
                char c = word[i];
                if(tn.children[c - 'a'] == null){
                    tn.children[c - 'a'] = new TrieNode(c);
                }
                tn = tn.children[c - 'a'];
            }
            tn.isWord = true;
        }
        
        /** Returns if the word is in the trie. */
        public bool Search(string word) {
            TrieNode tn = root; 
            for(int i = 0; i < word.Length; i++){
                char c = word[i];
                if(tn.children[c - 'a'] == null) return false;
                tn = tn.children[c - 'a'];
            }
            return tn.isWord;
        }
        
        /** Returns if there is any word in the trie that starts with the given prefix. */
        public bool StartsWith(string prefix) {
            TrieNode tn = root; 
            for(int i = 0; i < prefix.Length; i++){
                char c = prefix[i];
                if(tn.children[c - 'a'] == null) return false;
                tn = tn.children[c - 'a'];
            }
            return true;
        }
    }

    /**
    * Your Trie object will be instantiated and called as such:
    * Trie obj = new Trie();
    * obj.Insert(word);
    * bool param_2 = obj.Search(word);
    * bool param_3 = obj.StartsWith(prefix);
    */