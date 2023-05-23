# Insert Interval
>You are given an array of non-overlapping intervals `intervals` where `intervals[i] = [starti, endi]` represent the start and the end of the `i`<sup>`th`</sup> interval and `intervals` is sorted in ascending order by `starti`. You are also given an interval `newInterval = [start, end]` that represents the start and end of another interval.

>Insert `newInterval` into `intervals` such that `intervals` is still sorted in ascending order by `starti` and `intervals` still does not have any overlapping intervals (merge overlapping intervals if necessary).

>Return `intervals` after the insertion.

## Example 1:
```
Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]
```
## Example 2:
```
Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
Output: [[1,2],[3,10],[12,16]]
Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
```

## Dart
#### Solution

*Time complexity: O(n)*

*Space complexity: O(n)*
```
class Solution {
  List<List<int>> insert(List<List<int>> intervals, List<int> newInterval) {
    int i = 0;
    final List<List<int>> res = <List<int>>[];
    while (i < intervals.length) {
      if (newInterval[1] < intervals[i][0]) {
        return res..addAll([newInterval, ...intervals.sublist(i)]);
      } else if (newInterval[0] > intervals[i][1]) {
        res.add(intervals[i]);
      } else {
        newInterval = [
          min(newInterval[0], intervals[i][0]),
          max(newInterval[1], intervals[i][1])
        ];
      }
      i++;
    }
    res.add(newInterval);
    return res;
  }
}
```