# Valid Parentheses
>Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid. An input string is valid if:
- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.
- Every close bracket has a corresponding open bracket of the same type.
## Example 1:
```
Input: s = "()"
Output: true
```
## Example 2:
```
Input: s = "()[]{}"
Output: true
```
## Example 3:
```
Input: s = "(]"
Output: false
```
## Dart
#### Solution
*Time complexity:O(n)*

*Space complexity:O(n)*
```
class Solution {
  bool isValid(String s) {
    final closingParenthesesStack = <String>[];
    for (int i = 0; i < s.length; i++) {
      final c = s[i];
      if (c == '(') {
        closingParenthesesStack.add(')');
      } else if (c == '{') {
        closingParenthesesStack.add('}');
      } else if (c == '[') {
        closingParenthesesStack.add(']');
      } else if (closingParenthesesStack.isEmpty ||
          closingParenthesesStack.removeLast() != c) {
        return false;
      }
    }
    return closingParenthesesStack.isEmpty;
  }
}
```

## Python 3

```
```