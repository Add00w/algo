# Can Place Flowers
>You have a long ```flowerbed``` in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots.Given an integer array ```flowerbed``` containing `0`'s and `1`'s, where `0` means empty and `1` means not empty, and an integer `n`, return *if* `n` new flowers can be planted in the `flowerbed` without violating the *no-adjacent-flowers* rule.
## Example 1:
```
Input: flowerbed = [1,0,0,0,1], n = 1
Output: true
```
## Example 2:
```
Input: flowerbed = [1,0,0,0,1], n = 2
Output: false
```
## Dart
#### Solution
*Time complexity:O(n)*

*Space complexity:O(1)*
```
class Solution {
  bool canPlaceFlowers(List<int> flowerbed, int n) {
    int count = 0;
    for (int i = 0; i < flowerbed.length; i++) {
      if (flowerbed[i] == 0) {
        final leftPlotEmpty = i == 0 || flowerbed[i - 1] == 0;
        final rightPlotEmpty =
            i == flowerbed.length - 1 || flowerbed[i + 1] == 0;
        if (leftPlotEmpty && rightPlotEmpty) {
          flowerbed[i]=1;
          count++;
          if (count >= n) return true;
        }
      }
    }
    return count >= n;
  }
}
```

## Python 3

```
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        for i in range(len(flowerbed)):
           if flowerbed[i]==0:
               # check left plot is empty and right plot too
              if (i==0 or flowerbed[i-1]==0) and (i==len(flowerbed)-1 or flowerbed[i+1]==0):
                 flowerbed[i]=1
                 n=n-1
                 if n<=0: return True
        return n<=0
```