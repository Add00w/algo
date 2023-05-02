# Maximum Depth of Binary Tree
>Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

## Example 1:
```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```
## Example 2:
```
Input: root = [1,null,2]
Output: 2
```
## Dart
#### Solution

*Time complexity: O(n)*

*Space complexity: O(n)*
```
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *   int val;
 *   TreeNode? left;
 *   TreeNode? right;
 *   TreeNode([this.val = 0, this.left, this.right]);
 * }
 */
class Solution {
  int maxDepth(TreeNode? root) {
    if (root == null) return 0;
    final leftHeight = maxDepth(root.left);
    final rightHeight = maxDepth(root.right);
    return (leftHeight > rightHeight ? leftHeight : rightHeight)+1;
  }
}
```
