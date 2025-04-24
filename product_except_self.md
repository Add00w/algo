# Product of Array Except Self
>Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

## Example 1:
```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```
## Example 2:
```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```
## Dart
#### Solutions

*Time complexity: O(n^2)* *Not acceptable since it is not in the time limit.*

*Space complexity: O(n)*

```
class Solution {
  List<int> productExceptSelf(List<int> nums) {
    final answer = List.filled(nums.length, 1, growable: false);
    for (int i = 0; i < nums.length; i++) {
      int product = 1;
      // calculate prefix product of i
      for (int prev = 0; prev < i; prev++) {
        product *= nums[prev];
      }
      // calculate suffix product of i
      for (int j = i + 1; j < nums.length; j++) {
        product *= nums[j];
      }
      answer[i] = product;
    }
    return answer;
  }
}
```

*Time complexity: O(n)*

*Space complexity: O(n)*
```
class Solution {
  List<int> productExceptSelf(List<int> nums) {
    final answer = List.filled(nums.length, 1, growable: false);
    final prefix = List.filled(nums.length, 1, growable: false);
    final suffix = List.filled(nums.length, 1, growable: false);
    final n = nums.length;

    for (int i = 1; i < n; i++) {
      prefix[i] = prefix[i - 1] * nums[i - 1];
    }
    for (int i = n - 2; i >= 0; i--) {
      suffix[i] = suffix[i + 1] * nums[i + 1];
    }

    for (int i = 0; i < n; i++) {
      answer[i] = prefix[i] * suffix[i];
    }
    return answer;
  }
}
```
*Time complexity: O(n)*

*Space complexity: O(n)*

*But better space and time handling:*
```
class Solution {
  List<int> productExceptSelf(List<int> nums) {
    final answer = List.filled(nums.length, 1, growable: false);
    final n = nums.length;
    // compute prefix product
    int prefixProduct = 1;
    for (int i = 0; i < n; i++) {
      answer[i] *= prefixProduct;
      prefixProduct *= nums[i];
    }
    // compute suffix product
    int suffixProduct = 1;
    for (int i = n - 1; i >= 0; i--) {
      answer[i] *= suffixProduct;
      suffixProduct *= nums[i];
    }
    return answer;
  }
}
```