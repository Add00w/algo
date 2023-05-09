# Maximum Subarray
>Given an integer array `nums`, find the subarray with the largest sum, and *return its sum*.

## Example 1:
```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.
```
## Example 2:
```
Input: nums = [1]
Output: 1
Explanation: The subarray [1] has the largest sum 1.
```
## Example 3:
```
Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
```

## Dart
#### Solution (Kadane's Algorithm) DP

*Time complexity: O(n)*

*Space complexity: O(1)*
```
class Solution {
  int maxSubArray(List<int> nums) {
    int currentMax = nums[0];
    int maxTillNow = nums[0];
    for (int i=1;i<nums.length;i++) {
      currentMax = max(nums[i], currentMax + nums[i]);
      maxTillNow = max(maxTillNow, currentMax);
    }
    return maxTillNow;
  }
}
```
**Follow up**: If you have figured out the `O(n)` solution, try coding another solution using the **divide and conquer** approach, which is more subtle.


## Dart
#### Solution (divide and conquer)

*Time complexity: O(n)*

*Space complexity: O(n)*
```
class Solution {
  int maxSubArray(List<int> nums) {
    List<int> pre = List.from(nums);
    List<int> suf = List.from(nums);
    for (int i = 1; i < nums.length; i++) {
      pre[i] += max(0, pre[i - 1]); // update pre with previous element if positive
    }
    for (int i = nums.length - 2; i >= 0; i--) {
      suf[i] += max(0, suf[i + 1]); // update suf with next element if positive
    }
    int maxSubArray(List<int> A, int L, int R) {
      if (L == R) return A[L]; // base case: single element
      int mid = (L + R) ~/ 2; // integer division
      return max(
        max(
          maxSubArray(A, L, mid), // left subarray
          maxSubArray(A, mid + 1, R), // right subarray
        ),
        pre[mid] + suf[mid + 1], // cross subarray
      );
    }

    return maxSubArray(nums, 0, nums.length - 1);
  }
}
```