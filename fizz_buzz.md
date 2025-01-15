# First Bad Version
>Given an integer `n`, return a string array `answer`(1-indexed) where: 

- `answer[i] == "FizzBuzz"` if `i` is divisible by `3` and `5`.

- `answer[i] == "Fizz"` if `i` is divisible by `3`.

- `answer[i] == "i"` (as a string) if none of the above conditions are true.


## Example 1:
```
Input: n = 3
Output: ["1","2","Fizz"]
```
## Example 2:
```
Input: n = 5
Output: ["1","2","Fizz","4","Buzz"]
```
## Example 3:
```
Input: n = 15
Output: ["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]
```

## Dart
#### Solution 1
```
class Solution {
  List<String> fizzBuzz(int n) {
    final res = <String>[];
    for (int i = 1; i <= n; i++) {
    StringBuffer str = StringBuffer();
    if (i % 3 == 0) str.write('Fizz');
    if (i % 5 == 0) str.write('Buzz');
    if (str.isEmpty) str.write(i);
    res.add(str.toString());
  }
  return res;
  }
}
```

#### Solution 2
```
class Solution {
  List<String> fizzBuzz(int n) {
  final divisors = [3, 5];
  final divisorToWord = {3: 'Fizz', 5: 'Buzz'};
  final res = <String>[];
  for (int i = 1; i <= n; i++) {
    StringBuffer str = StringBuffer();
    for (final divisor in divisors) {
      if (i % divisor == 0) {
        str.write(divisorToWord[divisor]);
      }
    }
    if (str.isEmpty) str.write(i);
    res.add(str.toString());
  }
  return res;
  }
}
```
#### Solution 3
```
class Solution {
  List<String> fizzBuzz(int n) {
    final res = <String>[];
 int threes = 1;
  int fives = 1;
  for (int i = 1; i <= n; i++) {
    String str = '';
    if (threes == 3 && fives == 5) {
      str = 'FizzBuzz';
      threes = 0;
      fives = 0;
    } else if (threes == 3) {
      str = 'Fizz';
      threes = 0;
    } else if (fives == 5) {
      str = 'Buzz';
      fives = 0;
    } else  {
      str = '$i';
    }
    res.add(str);
    threes++;
    fives++;
  }
  return res;
  }
}
```
#### Solution 4
```
class Solution {
  List<String> fizzBuzz(int n) {
  final res = <String>[];
  res.addAll(List.generate(n, (int i) => '${++i}'));
  for (int i = 2; i < n; i += 3) {
    res[i] = 'Fizz';
  }
  for (int i = 4; i < n; i += 5) {
    res[i] = 'Buzz';
  }
  for (int i = 14; i < n; i += 15) {
    res[i] = 'FizzBuzz';
  }
  return res;
  }
}
```