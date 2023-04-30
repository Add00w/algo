# Longest Palindrome
>Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.

Letters are case sensitive, for example, "Aa" is not considered a palindrome here.

## Example 1:
```
Input: s = "abccccdd"
Output: 7
Explanation: One longest palindrome that can be built is "dccaccd", whose length is 7.
```
## Example 2:
```
Input: s = "a"
Output: 1
Explanation: The longest palindrome that can be built is "a", whose length is 1.
```
## Dart
#### Solution

*Time complexity: O(n)*

*Space complexity: O(1)*
```
class Solution {
  int longestPalindrome(String s) {
     int oddOccurrences=0;
     final charOccurrenceCount={};
     for(int i=0;i<s.length;i++){
        charOccurrenceCount[s.codeUnitAt(i)]
            =(charOccurrenceCount[s.codeUnitAt(i)]??0)+1;
        if(charOccurrenceCount[s.codeUnitAt(i)]%2==1)
          oddOccurrences++;
        else
         oddOccurrences--;
     }
     if(oddOccurrences>1) return s.length-oddOccurrences+1;
     return s.length;
  }
}
```
