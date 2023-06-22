# Encode decode strings
>Given strings, return one string or viceversa.


## Dart
#### Solution

```
class Solution {
  // The time complexity is o(n^2) but to make
  // o(n) use list and then join
  String encode(List<String> strings) {
    String result = '';
    for (final string in strings) {
      result += '${string.length}#$string';
    }
    return result;
  }

  List<String> decode(String string) {
    final result = <String>[];
    int i = 0;
    while (i < string.length) {
      int j = i;
      while (string[j] != '#') {
        j++;
      }
      //bcause the string length can be more than 9 means 2 digits
      // we need to use substring
      final length = int.parse(string.substring(i, j));
      result.add(string.substring(j + 1, j + 1 + length));
      i = j + 1 + length;
    }
    return result;
  }
}
```
