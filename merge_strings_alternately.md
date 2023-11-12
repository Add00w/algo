# 1768. Merge Strings Alternately

>You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.

## Example 1:
```
Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
Explanation: The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
```
Note that the cargo must be shipped in the order given, so using a ship of capacity 14 and splitting the packages into parts like (2, 3, 4, 5), (1, 6, 7), (8), (9), (10) is not allowed.

## Example 2:
```
Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
Explanation: Notice that as word2 is longer, "rs" is appended to the end.
word1:  a   b
word2:    p   q   r   s
merged: a p b q   r   s
```
## Example 3:
```
Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
Explanation: Notice that as word1 is longer, "cd" is appended to the end.
word1:  a   b   c   d
word2:    p   q
merged: a p b q c   d
```

## Dart
#### Solution
*Leetcode didn't support dart for this problem*


## Python
#### Solution
*Time complexity: O(n)* where n is the longest string length

*Space complexity: O(m+n)*
```
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        length1=len(word1);length2=len(word2)
        i=0
        result=""
        while i<length1 or i<length2:
            if i<length1:
               result+=word1[i]
            if i<length2:
                result+=word2[i]
            i=i+1

        return result

```