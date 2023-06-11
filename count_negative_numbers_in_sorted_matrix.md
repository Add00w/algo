# Count Negative Numbers in a Sorted Matrix
>Given a m x n matrix grid which is sorted in non-increasing order both row-wise and column-wise, return the number of negative numbers in grid.

## Example 1:
```
Input: grid = [[4,3,2,-1],[3,2,1,-1],[1,1,-1,-2],[-1,-1,-2,-3]]
Output: 8
Explanation: There are 8 negatives number in the matrix.
```
## Example 2:
```
Input: grid = [[3,2],[1,0]]
Output: 0
```
>Follow up: Could you find an O(n + m) solution?
## Dart
#### Solution

*Time complexity: O(m+n)*
where m is the number of rows in the matrix and n is the number of columns.
*Space complexity: O(1)*
```
class Solution {
  int countNegatives(List<List<int>> grid) {
    int count = 0;
        final int rows = grid.length;
        final int cols = grid[0].length;

        int r = 0;
        int c = cols - 1;

        while (r < rows && c >= 0) {
        if (grid[r][c] < 0) {
            count += rows - r; // Increment count by the number of negative numbers in the current column
            c--; // Move to the previous column
        } else {
            r++; // Move to the next row
        }
        }

        return count;
  }
}
```
