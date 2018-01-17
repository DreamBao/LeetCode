# 166. Fraction to Recurring Decimal
Fraction to Recurring Decimal

## Code
    public class Solution {
        public string FractionToDecimal(int numerator, int denominator) {
            //need repeat
            string result = "";
            string sign = (numerator < 0 == denominator < 0 || numerator == 0) ? "" : "-";
            long num = Math.Abs((long) numerator);
            long den = Math.Abs((long) denominator);
            result += sign;
            result += (num / den);
            long remainder = num % den;
            if (remainder == 0)
                return result;
            result += ".";
            Dictionary<long, int> hashMap = new Dictionary<long, int>();
            while (!hashMap.ContainsKey(remainder)) {
                hashMap.Add(remainder, result.Length);
                result += (10 * remainder / den);
                remainder = 10 * remainder % den;
            }
            int index = hashMap[remainder];
            result = result.Insert(index, "(");
            result += ")";
            return result.Replace("(0)", "");
        }
    }