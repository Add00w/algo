# Dart
## Solution
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

# Python 3

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