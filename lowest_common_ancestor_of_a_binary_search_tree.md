# Lowest Common Ancestor of a Binary Search Tree
>Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

“The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow a node to be a descendant of itself).”

## Example 1:
```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
Output: 6
Explanation: The LCA of nodes 2 and 8 is 6.
```
## Example 2:
```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
Output: 2
Explanation: The LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
```
## Example 3:
```
Input: root = [2,1], p = 2, q = 1
Output: 2
```

## Dart
#### Solution
*Leetcode didn't support dart for this problem*


## Python
#### Solution
*Time complexity: O(h)*

*Space complexity: O(1)*
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        small = min(p.val, q.val)
        large = max(p.val, q.val)
        while root:
            # p, q belong to the left subtree
            if root.val > large:
                root = root.left
            # p, q belong to the right subtree
            elif root.val < small:
                root = root.right
            else:  # Now, small <= root.val <= large -> This is the LCA between p and q
                return root
        return None
```
