# 211. Add and Search Word - Data structure design
Add and Search Word - Data structure design

## Code
    public class TrieNode {
        public TrieNode[] children = new TrieNode[26];
        public string item = "";
    }

    public class WordDictionary {
        public static TrieNode root = null;
        
        /** Initialize your data structure here. */
        public WordDictionary() {
            root = new TrieNode();
        }
        
        /** Adds a word into the data structure. */
        public void AddWord(string word) {
            TrieNode node = WordDictionary.root;
            char[] chs = word.ToCharArray();
            for (int i = 0; i < chs.Length; i ++) {
                char c = chs[i];
                if (node.children[c - 'a'] == null) {
                    node.children[c - 'a'] = new TrieNode();
                }
                node = node.children[c - 'a'];
            }
            node.item = word;
        }
        
        /** Returns if the word is in the data structure. A word could contain the dot character '.' to represent any one letter. */
        public bool Search(string word) {
            return Match(word.ToCharArray(), 0, WordDictionary.root);
        }
        
        public bool Match(char[] chs, int k, TrieNode node) {
            if (k == chs.Length) return !string.IsNullOrEmpty(node.item);   
            if (chs[k] != '.') {
                return node.children[chs[k] - 'a'] != null && Match(chs, k + 1, node.children[chs[k] - 'a']);
            } else {
                for (int i = 0; i < node.children.Length; i++) {
                    if (node.children[i] != null) {
                        if (Match(chs, k + 1, node.children[i])) {
                            return true;
                        }
                    }
                }
            }
            return false;
        }
    }

    /**
    * Your WordDictionary object will be instantiated and called as such:
    * WordDictionary obj = new WordDictionary();
    * obj.AddWord(word);
    * bool param_2 = obj.Search(word);
    */