# Two Sum

> Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

## Example 1:
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```
## Example 2:
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```
## Example 3:
```
Input: nums = [3,3], target = 6
Output: [0,1]
```
## Dart
### Solution 1
#### If the execution time is more important than the space
*Time complexity:O(n)*

*Space complexity:O(n)*
```
class Solution {
  List<int> twoSum(List<int> nums, int target) {
    final visited = <int, int>{};
    for (int i = 0; i < nums.length; i++) {
      final remaining = target - nums[i];
      if (visited.containsKey(remaining)) {
        return [visited[remaining]!,i];
      }
      visited[nums[i]] = i;
    }
    return [];
  }
}
```
### Solution 2
#### If the space is more important than execution time
*Time complexity:O(n^2)*

*Space complexity:O(1)*
```
class Solution {
  List<int> twoSum(List<int> nums, int target) {
    for (int outerIdx = 0; outerIdx < nums.length-1; outerIdx++) {
      for (int innerIdx = outerIdx+1; innerIdx < nums.length; innerIdx++) {
        if (nums[outerIdx]+nums[innerIdx]==target) {
          return [outerIdx,innerIdx];
      }
    }
    return [];
  }
}
```

## Python
### Solution 1
#### If the execution time is more important than the space
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashmap = {}
        for i in range(len(nums)):
            complement = target - nums[i]
            if complement in hashmap:
                return [i, hashmap[complement]]
            hashmap[nums[i]] = i
```
### Solution 2
#### If the space is more important than execution time
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[j] == target - nums[i]:
                    return [i, j]
```