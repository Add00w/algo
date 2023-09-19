# 189. Rotate Array
Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

## Example 1:
```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```
## Example 2:
```
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation:
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```

## Dart
#### Solution

https://leetcode.com/problems/rotate-array/solutions/4063495/solved-rotate-array-with-dart-lang/

*Time complexity: O(n)*
*Space complexity: O(n)*
```
class Solution {
  void rotate(List<int> nums, int k) {
      final n = nums.length;
      k = k % n;
      final leftNums = nums.getRange(0, n - k);
      final tempNums = nums.getRange(n - k, n).toList();
      tempNums.add(double.maxFinite.toInt());
      tempNums.replaceRange(tempNums.length-1,tempNums.length,leftNums);
      nums.clear();
      nums.addAll(tempNums);
  }
}
```
