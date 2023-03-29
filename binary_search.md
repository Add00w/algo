# Binary Search
>Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.
## Example 1:
```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```
## Example 2:
```
Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
```

## Dart
#### Solution
*Time complexity: O(logn) worst*

*Space complexity: O(1)*
```
class Solution {
  int search(List<int> nums, int target) {
    int targetIndex = -1;
    int beginingIndex = 0;
    int endIndex = nums.length - 1;
    while (beginingIndex <= endIndex) {
      final middleIndex = ((beginingIndex + endIndex) / 2).floor();
      if (nums[middleIndex] == target) {
        targetIndex = middleIndex;
        break;
      } else if (nums[middleIndex] < target) {
        beginingIndex=middleIndex+1;
      } else if (nums[middleIndex] > target) {
        endIndex=middleIndex-1;
      }
    }
    return targetIndex;
  }
}
```
