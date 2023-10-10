# Valid Anagram
>Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` *otherwise*. An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
## Example 1:
```
Input: s = "anagram", t = "nagaram"
Output: true
```
## Example 2:
```
Input: s = "rat", t = "car"
Output: false
```
**Follow up**: What if the inputs contain Unicode characters? How would you adapt your solution to such a case?

## Dart
#### Solution
*Time complexity:O(n)*

*Space complexity:O(n)*
```
class Solution {
bool isAnagram(String s, String t) {
  if (s.length != t.length) return false;
  // Count of each char occurrence in s
  final sCount = <String, int>{};
  // Count of each char occurrence in t
  final tCount = <String, int>{};
  for (int i = 0; i < s.length; i++) {
    sCount[s[i]] = (sCount[s[i]] ?? 0) + 1;
    tCount[t[i]] = (tCount[t[i]] ?? 0) + 1;
  }
  // Check if the two maps are equal
  for (final key in sCount.keys) {
    // If there is 'char' in s and not in t or the 'char' count is
    // not equal return false
    if (!tCount.containsKey(key) || tCount[key] != sCount[key]) {
      return false;
    }
  }
  // If reached here the two strings are equal
  return true;
}
}
```
