
# Group Anagrams
>Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Example 1:
```
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```
## Example 2:
```
Input: strs = [""]
Output: [[""]]
```
## Example 2:
```
Input: strs = ["a"]
Output: [["a"]]
```

## Dart
#### Solution 1

*Time complexity: O(mnlogn)*

*Space complexity: O(mn)*

```
class Solution {
  List<List<String>> groupAnagrams(List<String> strgs) {
  var groups = <String, List<String>>{};
  for (final s in strgs) {
    final keyStrings = s.split('');
    keyStrings.sort();
    final key = keyStrings.join();
    if (groups.containsKey(key)) {
      groups[key]!.add(s);
    } else {
      groups[key] = [s];
    }
  }
  return groups.values.toList();
}
}
```