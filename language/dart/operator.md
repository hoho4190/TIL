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

### cascade notation

하나의 오브젝트에 함수 호출, 필드 접근을 순차적으로 수행할 수 있음

이 과정 중간에 어떤 값이 반환되더라도 무시됨

```
void main() {

  // cascade notation
  Person(name: 'foo', age: 1)
      ..name = 'bar'
      ..age = 99
      ..introduce(); // bar(99) 입니다.
}
```

```
class Person {
  String name;
  int age;

  Person({required this.name, required this.age});

  void introduce() {
    print('${this.name}(${this.age}) 입니다.');
  }
}
```

### spread operator

여러 개의 요소를 컬렉션에 간편하게 추가할 수 있음

```
void main() {

  // spread operator
  List<int> numList1 = [1, 2, 3];
  List<int> numList2 = [4, 5, 6];
  List<int> numList3 = [...numList1, 4, 5, 6];

  print([numList1, numList2]); // [[1, 2, 3], [4, 5, 6]]
  print([...numList1, ...numList2]); // [1, 2, 3, 4, 5, 6]
  print(numList3); // [1, 2, 3, 4, 5, 6]
}
```
