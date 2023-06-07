# 01 Matrix

>Given an m x n binary matrix mat, return the distance of the nearest 0 for each cell.

The distance between two adjacent cells is 1.

[on leetcode](https://leetcode.com/problems/01-matrix/submissions/965854799)

## Example 1:
```
Input: mat = [[0,0,0],[0,1,0],[0,0,0]]
Output: [[0,0,0],[0,1,0],[0,0,0]]
```
## Example 2:
```
Input: mat = [[0,0,0],[0,1,0],[1,1,1]]
Output: [[0,0,0],[0,1,0],[1,2,1]]
```

## Dart
#### Solution 1

*Time complexity: O(m.n)*

*Space complexity: O(m.n)*

where m is the number of rows and n is the number of columns in the input matrix
```
import 'dart:collection';

class Solution {
  List<List<int>> updateMatrix(List<List<int>> mat) {
    final ListQueue<List<int>> zerosIndices = ListQueue<List<int>>();
    final rows = mat.length;
    final cols = mat.first.length;
    for (int r = 0; r < rows; r++) {
      for (int c = 0; c < cols; c++) {
        if (mat[r][c] == 0) {
          zerosIndices.add([r, c]);
          continue;
        }
        mat[r][c] = -1;
      }
    }

    final directions = [
      [1, 0],   // down
      [-1, 0],  // up
      [0, 1],   // right
      [0, -1],  // left
    ];

    while (zerosIndices.isNotEmpty) {
      final cell = zerosIndices.removeFirst();
      final row = cell[0];
      final col = cell[1];

      for (final direction in directions) {
        final newRow = row + direction[0];
        final newCol = col + direction[1];

        if (newRow >= 0 &&
            newRow < rows &&
            newCol >= 0 &&
            newCol < cols &&
            mat[newRow][newCol] == -1) {
          mat[newRow][newCol] = mat[row][col] + 1;
          zerosIndices.add([newRow, newCol]);
        }
      }
    }

    return mat;
  }
}
```

#### Solution 2

*Time complexity: O(m.n)*

*Space complexity: O(1)*

where m is the number of rows and n is the number of columns in the input matrix
```
import 'dart:collection';

class Solution {
   List<List<int>> updateMatrix(List<List<int>> mat) {
    final int rows = mat.length;
    final int cols = mat[0].length;
    final int maxDistance = rows + cols; // Maximum possible distance in the matrix

    // First pass: Top-left to bottom-right
    for (int r = 0; r < rows; r++) {
      for (int c = 0; c < cols; c++) {
        if (mat[r][c] != 0) {
          int topCell = (r > 0) ? mat[r - 1][c] : maxDistance;
          int leftCell = (c > 0) ? mat[r][c - 1] : maxDistance;
          mat[r][c] = 1 + (topCell < leftCell ? topCell : leftCell);
        }
      }
    }

    // Second pass: Bottom-right to top-left
    for (int r = rows - 1; r >= 0; r--) {
      for (int c = cols - 1; c >= 0; c--) {
        if (mat[r][c] != 0) {
          int bottomCell = (r < rows - 1) ? mat[r + 1][c] : maxDistance;
          int rightCell = (c < cols - 1) ? mat[r][c + 1] : maxDistance;
          int currentCell = mat[r][c];
          mat[r][c] = (currentCell < bottomCell + 1) ? currentCell : bottomCell + 1;
          mat[r][c] = (mat[r][c] < rightCell + 1) ? mat[r][c] : rightCell + 1;
        }
      }
    }

    return mat;
  }
}
```