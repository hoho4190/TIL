# Future

```
// 미래에 받아올 값
Future<String> nameFuture = Future.value('foo');

/**
 * Future.delayed
 * 2개의 파라미터
 * 1번 파라미터 - 지연할 기간 Duration
 * 2번 파라미터 - 지연 시간이 지난 후 실행할 함수
 */
Future.delayed(Duration(seconds: 2), () {
 print('Delay 끝');
});
```

### delayed 예제

```
void main() {
  addNumbers(1, 2);
  addNumbers(3, 4);
  // 계산 시작: 1 + 2
  // 함수 완료: 1 + 2
  // 계산 시작: 3 + 4
  // 함수 완료: 3 + 4
  // 계산 완료: 1 + 2 = 3
  // 계산 완료: 3 + 4 = 7
}

void addNumbers(int number1, int number2) {
  print('계산 시작: $number1 + $number2');

  // 서버 시뮬레이션
  Future.delayed(Duration(seconds: 2), () {
    print('계산 완료: $number1 + $number2 = ${number1 + number2}');
  });

  print('함수 완료: $number1 + $number2');
}
```

### await 예제1

```
void main() {
  addNumbers(1, 2);
  addNumbers(3, 4);
  // 계산 시작: 1 + 2
  // 계산 시작: 3 + 4
  // 계산 완료: 1 + 2 = 3
  // 함수 완료: 1 + 2
  // 계산 완료: 3 + 4 = 7
  // 함수 완료: 3 + 4
}

void addNumbers(int number1, int number2) async {
  print('계산 시작: $number1 + $number2');

  // 서버 시뮬레이션
  await Future.delayed(Duration(seconds: 2), () {
    print('계산 완료: $number1 + $number2 = ${number1 + number2}');
  });

  print('함수 완료: $number1 + $number2');
}
```

### await 예제2

```
void main() async {
  await addNumbers(1, 2);
  await addNumbers(3, 4);
  // 계산 시작: 1 + 2
  // 계산 완료: 1 + 2 = 3
  // 함수 완료: 1 + 2
  // 계산 시작: 3 + 4
  // 계산 완료: 3 + 4 = 7
  // 함수 완료: 3 + 4
}

Future<void> addNumbers(int number1, int number2) async {
  print('계산 시작: $number1 + $number2');

  // 서버 시뮬레이션
  await Future.delayed(Duration(seconds: 2), () {
    print('계산 완료: $number1 + $number2 = ${number1 + number2}');
  });

  print('함수 완료: $number1 + $number2');
}
```

### Future 리턴 예제

하나의 데이터 타입으로만 리턴 받을 수 있음

```
void main() async {
  final result1 = await addNumbers(1, 2);
  final result2 = await addNumbers(3, 4);

  print('result1: $result1');
  print('result2: $result2');
  print('result1 + result2: ${result1 + result2}');
}

Future<int> addNumbers(int number1, int number2) async {
  print('계산 시작: $number1 + $number2');

  int result = 0;

  // 서버 시뮬레이션
  await Future.delayed(Duration(seconds: 2), () {
    result = number1 + number2;
    print('계산 완료: $number1 + $number2 = ${result}');
  });

  print('함수 완료: $number1 + $number2');

  return result;
}
```
