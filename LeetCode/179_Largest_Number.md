# 179. Largest Number
Largest Number

## Code
    public class CusCompare : IComparer<string>
    {
        public int Compare(string i, string j)
        {
            string s1 = i + j;
            string s2 = j + i;
            return s1.CompareTo(s2);
        }
    }

    public class Solution {
        public string LargestNumber(int[] nums) {
            if (nums == null || nums.Length == 0) return "";
            string[] strs = new string[nums.Length];
            for (int i = 0; i < nums.Length; i++) {
                strs[i] = nums[i]+"";
            }
            CusCompare cc = new CusCompare();
            Array.Sort(strs, cc);
            if (strs[strs.Length-1][0] == '0') return "0";
            string res = "";
            for (int i = 0; i < strs.Length; i++) {
                res = strs[i]+res;
            }
            return res;
        }
    }