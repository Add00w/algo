# Climbing Stairs
>You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## Example 1:
```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```
## Example 2:
```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```
## Dart
#### Solution

*Time complexity: O(n)*

*Space complexity: O(1)*
```
class Solution {
  // Solved using Fibonacci
  int climbStairs(int n) {
    if (n < 4) return n;//1,2,3
    int climbs=0;
    int prevPrevious = 0;
    int previous = 1;
    while (n>0) {
      climbs = previous + prevPrevious;
      prevPrevious=previous;
      previous=climbs;
      n--;
    }
    return climbs;
  }
}
```
