# 395. Longest Substring with At Least K Repeating Characters
Longest Substring with At Least K Repeating Characters

## Code
    public class Solution {
        public int LongestSubstring(string s, int k) {
            if (s == null || s.Length == 0 || k == 0) return 0;
            int max = 0;
            int[] count = new int[26];
            int res = 0;
            for (int i = 0; i < s.Length; i++) {
            count[s[i] - 'a']++;
            }
            List<int> pos = new List<int>();
            for (int i = 0; i < s.Length; i++) {
            if (count[s[i] - 'a'] < k) pos.Add(i);
            }
            if (pos.Count == 0) return s.Length;
            pos.Insert(0, -1);
            pos.Add(s.Length);
            for (int i = 1; i < pos.Count; i++) {
            int start = pos[i-1] + 1;
            int end = pos[i];
            int next = LongestSubstring(s.Substring(start, end - start), k);
            res = Math.Max(res, next);
            }
            return res;
        }
    }