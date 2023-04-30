# Ransom Note
>Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.

Each letter in magazine can only be used once in ransomNote.

## Example 1:
```
Input: ransomNote = "a", magazine = "b"
Output: false
```
## Example 2:
```
Input: ransomNote = "aa", magazine = "ab"
Output: false
```
## Example 3:
```
Input: ransomNote = "aa", magazine = "aab"
Output: true
```
## Dart
#### Solution

*Time complexity: O(n)*

*Space complexity: O(1)*
```
class Solution {
  bool canConstruct(String ransomNote, String magazine) {
    if (ransomNote.length > magazine.length) return false;
    final alphabetsCount = List.filled(26, 0);
    const a = 'a';
    for (int i = 0; i < magazine.length; i++) {
      final alphabetIndex = magazine.codeUnitAt(i) - a.codeUnitAt(0);
      alphabetsCount[alphabetIndex]++;
    }
    for (int i = 0; i < ransomNote.length; i++) {
      final alphabetIndex = ransomNote.codeUnitAt(i) - a.codeUnitAt(0);
      if (alphabetsCount[alphabetIndex] == 0) return false;
      alphabetsCount[alphabetIndex]--;
    }
    return true;
  }
}
```
