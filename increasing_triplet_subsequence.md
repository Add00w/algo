# Increasing Triplet Subsequence
>Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exists, return false.

**Follow up:** Could you implement a solution that runs in O(n) time complexity and O(1) space complexity?

## Example 1:
```
Input: nums = [1,2,3,4,5]
Output: true
Explanation: Any triplet where i < j < k is valid.
```
## Example 2:
```
Input: nums = [5,4,3,2,1]
Output: false
Explanation: No triplet exists.
```
## Dart
#### Solutions

*Time complexity: O(n)* 

*Space complexity: O(1)*

```dart []
class Solution {
  bool increasingTriplet(List<int> nums) {
    if (nums.length < 3) return false;
    int min1 = 0xFFFFFFFF;
    int min2 = 0xFFFFFFFF;
    for (final n in nums) {
      if (n <= min1) {
        min1 = n;
      } else if (n <= min2) {
        min2 = n;
      } else {
        return true;
      }
    }
    return false;
  }
}
```