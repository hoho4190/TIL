# typedef

함수를 시그니쳐화 함

리턴 타입, 파라미터가 동일한 function을 할당하여 사용 가능

```
void main() {
  Operation operation = add;
  print(operation(10, 20, 30)); // 60

  operation = subtract;
  print(operation(10, 20, 30)); // -40


  print(calculate(10, 20, 30, add)); // 60
  print(calculate(10, 20, 30, subtract)); // -40
}

// signature
typedef Operation = int Function(int x, int y, int z);

int add(int x, int y, int z) => x + y + z;
int subtract(int x, int y, int z) => x - y - z;

// 사용 예제
int calculate(
  int x, 
  int y, 
  int z, 
  Operation operation
) => operation(x, y, z);
```
