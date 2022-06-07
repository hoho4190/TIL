# function과 parameter

### Positional parameter

```
void main() {
  print(addStrings1('a', null)); // a null
}

String addStrings1(
  String str1, 
  String? str2
) => '$str1 $str2'; // arrow function
```

### Optional parameter

초기값이 있어야&#x20;

```
void main() {
  print(addStrings2());         // null c
  print(addStrings2('a'));      // a c
  print(addStrings2('a', 'b')); // a b
}

String addStrings2([
  String? str1,
  String str2 = 'c'
]) => '$str1 $str2';
```

### Named parameter

파라미터 순서 상관 없음

required 아닌 경우 초기값이 있어야 함

```
void main() {
  print(addStrings3(str1: 'a'));                       // a null cc
  print(addStrings3(str2: 'b', str1: 'a'));            // a b cc
  print(addStrings3(str2: 'b', str3: 'c', str1: 'a')); // a b c
}

String addStrings3({
  required String str1, 
  String? str2, 
  String str3 = 'cc'
}) => '$str1 $str2 $str3';
```

