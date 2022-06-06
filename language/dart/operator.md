# Operator

### Null 조건 operator

```
void main() {
  double? doubleNum = null;
  doubleNum ??= 3.0; // null일 경우 3.0 저
  print(doubleNum); // 3
  
  doubleNum ??= 5.1;
  print(doubleNum); // 3
}
```

### 타입 비교 operator

```
void main() {
  int num1 = 1;
  
  print(num1 is int); // true
  print(num1 is! int); // false
}
```
