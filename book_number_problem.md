# Book pages numbering
>Mary wrote a book that had 1536 pages. She numbered all the pages by hand. How many times did she write the digit 6?

## Dart
#### Solutions
*Time complexity:O(n)*

*Space complexity:O(1)*

#### Solution 1
```
void main(){
  final pages=1536;
  int count=0;
  for(int i=0;i<= pages;i++){
    // e.g. 6 appears in 16 1 time
   count+='6'.allMatches('$i').length;
  }
  print(count);
}
```
#### Solution 2
```
void main(){
  final pages=1536;
  // find how many times 6 appears in the number
  int count=1;
  for(int i=7;i<= pages;i++){
    // e.g. 16=>1,6=>6=>count=>1
   count+='$i'.split('').where((e)=>e=='6').length;
  }
  print(count);
}
```
## Python 3

```
```