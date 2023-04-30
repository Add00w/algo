# Add Binary
>Given two binary strings a and b, return their sum as a binary string.

## Example 1:
```
Input: a = "11", b = "1"
Output: "100"
```
## Example 2:
```
Input: a = "1010", b = "1011"
Output: "10101"
```
## Dart
#### Solution

*Time complexity: O(n)*

*Space complexity: O(1)*
```
class Solution {
  String addBinary(String a, String b) {
    int carry = 0;
    int aLength = a.length - 1;
    int bLength = b.length - 1;
    String result = '';
    while (aLength >= 0 || bLength >= 0) {
      int sum = carry;
      if (aLength >= 0) sum += int.parse(a[aLength--]);
      if (bLength >= 0) sum += int.parse(b[bLength--]);
      carry = sum > 1 ? 1 : 0;
      result = (sum % 2).toString() + result;
    }
    if (carry > 0) result = carry.toString() + result;
    return result;
  }
}
```
