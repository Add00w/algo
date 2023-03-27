# Invert Binary Tree
>Given the `root` of a binary tree, invert the tree, and return *its root*.
## Example 1:
```
Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]
```
## Example 2:
```
Input: root = [2,1,3]
Output: [2,3,1]
```
## Example 3:
```
Input: root = []
Output: []
```
## Dart
#### Solution
*Time complexity:O(n)*

*Space complexity:O(n)*
```
class Solution {
  TreeNode? invertTree(TreeNode? root) {
    if (root == null) return null;
    invertTree(root.left);
    invertTree(root.right);
    final left = root.left;
    root.left = root.right;
    root.right = left;
    return root;
  }
}
```
