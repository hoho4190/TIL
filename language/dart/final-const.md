# final과 const

### final과 const 공통점

변수의 값을 한 번 초기화된 뒤로 변경 불가능

```
void main() {
  final String finalStr = 'final str';
  // finalStr = 'final str2'; // error

  const String constStr = 'const str';
  // constStr = 'const str2'; // error

  // 데이터 타입 생략 가능
  final finalNum = 1;
  const constNum = 2;
}
```

### final과 const 차이점

final은 런타임 시 값이 결정됨(런타임 시 해당 라인이 실행 될 때)

const 컴파일 시 값이 결정됨

```
void main() {
  // 런타임 시 해당 라인이 실행 될 때 현재 시간을 변수에 저장함
  final finalNow = DateTime.now();

  // 컴파일 시 해당 라인이 실행 될 때의 현재 시간을 알 수 없음
  // const finalNow = DateTime.now(); // error
}
```
