# Contains Duplicate
>Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

## Example 1:
```
Input: nums = [1,2,3,1]
Output: true
```
## Example 2:
```
Input: nums = [1,2,3,4]
Output: false
```
## Example 3:
```
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

## Dart
#### Solution 1

*Time complexity: O(n)*

*Space complexity: O(n)*
```
class Solution {
  bool containsDuplicate(List<int> nums) {
    final nonDuplicate = nums.toSet();
    return nonDuplicate.length != nums.length;
  }
}
```

#### Solution 2

*Time complexity: O(n log n)*

*Space complexity: O(n) wors case*
```
class Solution {
  bool containsDuplicate(List<int> nums) {
    nums.sort();
    int length = nums.length - 1;
    while (length > 0) {
      if (nums[length] == nums[length - 1]) {
        return true;
      }
      length -= 1;
    }
    return false;
  }
}
```