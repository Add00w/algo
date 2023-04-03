# Balanced Binary Tree
>Given a binary tree, determine if it is height-balanced

## Example 1:
```
Input: root = [3,9,20,null,null,15,7]
Output: true
```
## Example 2:
```
Input: root = [1,2,2,3,3,null,null,4,4]
Output: false
```
## Example 2:
```
Input: root = []
Output: true
```

## Dart
#### Solution
*Time complexity: O(n)*

*Space complexity: O(n)*
```
class TreeNode {
  int val;
  TreeNode? left;
  TreeNode? right;
  TreeNode([this.val = 0, this.left, this.right]);
}

class Solution {
  int dfsHeight(TreeNode? root) {
    if (root == null) return 0;

    final leftHeight = dfsHeight(root.left);
    if (leftHeight == -1) return -1;
    final rightHeight = dfsHeight(root.right);
    if (rightHeight == -1) return -1;

    if ((leftHeight - rightHeight).abs() > 1) return -1;
    return max(leftHeight, rightHeight) + 1;
  }

  bool isBalanced(TreeNode? root) {
    return dfsHeight(root) != -1;
  }
}
```
