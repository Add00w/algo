# Diameter of Binary Tree
>Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.

## Example 1:
```
Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
```
## Example 2:
```
Input: root = [1,2]
Output: 1
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
  late int diameter = 0;
  int diameterOfBinaryTree(TreeNode? root) {
    maxDepth(root);
    return diameter;
  }

  int maxDepth(TreeNode? node) {
    if (node == null) return 0;
    // Get the left nodes height
    final left = maxDepth(node.left);
    // Get the right nodes height
    final right = maxDepth(node.right);
    // Calculate the diameter
    if ((left + right) > diameter) diameter = left + right;
    // Take each node's max depth
    return 1 + (left > right ? left : right);
  }
}
```
