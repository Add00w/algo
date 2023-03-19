# Python
## Solution 1
### If the execution time is more important than the space
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
## Solution 2
### If the space is more important than execution time
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[j] == target - nums[i]:
                    return [i, j]
```
# Dart
## Solution 1
### If the execution time is more important than the space
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
## Solution 2
### If the space is more important than execution time
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