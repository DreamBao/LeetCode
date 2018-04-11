# 424. Longest Repeating Character Replacement
Longest Repeating Character Replacement

## Code
    public class Solution {
        public int CharacterReplacement(string s, int k) {
            int len = s.Length;
            int[] count = new int[26];
            int start = 0, maxCount = 0, maxLength = 0;
            for (int end = 0; end < len; end++) {
                maxCount = Math.Max(maxCount, ++count[s[end] - 'A']);
                while (end - start + 1 - maxCount > k) {
                    count[s[start] - 'A']--;
                    start++;
                }
                maxLength = Math.Max(maxLength, end - start + 1);
            }
            return maxLength;
        }
    }