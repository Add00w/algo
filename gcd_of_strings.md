# 1071. Greatest Common Divisor of Strings

>For two strings s and t, we say "t divides s" if and only if s = t + ... + t (i.e., t is concatenated with itself one or more times).

Given two strings str1 and str2, return the largest string x such that x divides both str1 and str2.

## Example 1:
```
Input: str1 = "ABCABC", str2 = "ABC"
Output: "ABC"
```

## Example 2:
```
Input: str1 = "ABABAB", str2 = "ABAB"
Output: "AB"
```
## Example 3:
```
Input: str1 = "LEET", str2 = "CODE"
Output: ""
```
Constraints:
1 <= str1.length, str2.length <= 1000
str1 and str2 consist of English uppercase letters.

## Dart
#### Solution

*Time complexity: O(logn)* which is worst gcd time complexity

*Space complexity: O(m+n)* where m and n are the lengths of str1,str2 alternatively,

```
class Solution {
  String gcdOfStrings(String str1, String str2) {
    if ('$str1$str2' != '$str2$str1') {
      return "";
    }
    return str1.substring(0, str1.length.gcd(str2.length));
  }
}
```

## Python
#### Solution
*Time complexity: O(logn)* which is worst gcd time complexity

*Space complexity: O(m+n)* where m and n are the lengths of str1,str2 alternatively,
```
class Solution:
    def gcd(a,b):
      while(a):
        a,b=b%a,a
      return b
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        return "" if str1+str2!=str2+str1 else str1[:gcd(len(str1),len(str2))]
```