# Reverse Vowels of a String
>Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

## Example 1:
```
Input: s = "IceCreAm"

Output: "AceCreIm"

Explanation:

The vowels in s are ['I', 'e', 'e', 'A']. On reversing the vowels, s becomes "AceCreIm".
```
## Example 2:
```
Input: s = "leetcode"

Output: "leotcede"
```
## Dart
#### Solution

*Time complexity: O(n)*

*Space complexity: O(n)*
```
class Solution {
  String reverseVowels(String s) {
    const vowels = {'a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'};
    int i = 0, j = s.length - 1;
    final sChars = s.split('');
    while (i < j) {
      if (!vowels.contains(sChars[i])) {
        i++;
      } else if (!vowels.contains(sChars[j])) {
        j--;
      } else {
        // both i and j are pointing to vowels
        final tmp = sChars[i];
        sChars[i] = sChars[j];
        sChars[j] = tmp;
        i++;
        j--;
      }
    }
    return sChars.join('');
  }
}
```
