# Reverse Words in a String
>Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

**Note** that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

## Example 1:
```
Input: s = "the sky is blue"
Output: "blue is sky the"
```
## Example 2:
```
Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.
```
## Example 3:
```
Input: s = "a good   example"
Output: "example good a"
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.
```
## Dart
#### Solutions

*Time complexity: O(n)*

*Space complexity: O(n)*

```dart
class Solution {
  String reverseWords(String s) {
    final sWords = s.split(' ');
    int i = 0, j = sWords.length - 1;
    while (i < j) {
      if (sWords[i].isEmpty) {
        i++;
      } else if (sWords[j].isEmpty) {
        j--;
      } else {
        final tmp = sWords[i];
        sWords[i] = sWords[j];
        sWords[j] = tmp;
        i++;
        j--;
      }
    }
    return sWords.where((word) => word.isNotEmpty).join(' ');
  }
}
```

```dart
class Solution {
  String reverseWords(String s) {
    final sWords = s.trim().split(RegExp(r'\s+'));
    int i = 0, j = sWords.length - 1;
    while (i < j) {
      final tmp = sWords[i];
      sWords[i] = sWords[j];
      sWords[j] = tmp;
      i++;
      j--;
    }
    return sWords.join(' ');
  }
}
```

```dart
class Solution {
  String reverseWords(String s) =>
      s.trim().split(RegExp(r'\s+')).reversed.join(' ');
}
```
