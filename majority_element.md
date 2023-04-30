# Majority Element
>Given an array `nums` of size `n`, return the majority element.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

## Example 1:
```
Input: nums = [3,2,3]
Output: 3
```
## Example 2:
```
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```
***
Follow-up: Could you solve the problem in linear time and in O(1) space?
***
## Dart
#### Solution

*Time complexity: O(n)*

*Space complexity: O(1)*
```
class Solution {
  int majorityElement(List<int> nums) {
    late int majorityElement;
    int count = 0;
    for (final element in nums) {
      // Since majority element should appear more than n/2 times
      // it is count will be greater than 1 at the end
      // let us say we have 7 nums ciel(7/2)=4
      // means the majority element should appear 4 times
      //which means 4(majority)-3(others)>0
      // at the end return the element with count>0
      if (count == 0) majorityElement = element;
      count += element == majorityElement ? 1 : -1;
    }
    return majorityElement;
  }
}
```
