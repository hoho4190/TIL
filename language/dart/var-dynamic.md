# var와 dynamic

### var와 dynamic의 공통점

둘 다 초기화된 값으로 타입이 결정

### var와 dynamic의 차이점

var는 타입이 한 번 결정되면 다른 타입으로 변경이 불가능

dynamic은 다른 타입으로 계속 변경 가능

### 예제

```
void main() {
  var var1 = 'str';
  print(var1.runtimeType); // String
  
  var var2 = 20;
  print(var2.runtimeType); // int

  // var은 한 번 결정된 타입은 다른 타입으로 변경 불가능
  // var1 = 10; // error

  
  
  dynamic dy1 = 'str';
  print(dy1.runtimeType); // String
  dy1 = 2;
  print(dy1.runtimeType); // int
}
```
