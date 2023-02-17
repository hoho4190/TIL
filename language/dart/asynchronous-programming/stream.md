# Stream

### listen 예제

여러 데이터 타입으로 받을 수 있음

```
import 'dart:async';

void main() {
  final ctrl = StreamController();
  final stream = ctrl.stream;

  final streamListener1 = stream.listen((event) {
    print('Listener1 : $event');
  });

  ctrl.sink.add(1);
  ctrl.sink.add(3);
  ctrl.sink.add('a');
}
```

### broadcast 예제1

```
void main() {
  final ctrl = StreamController();
  final stream = ctrl.stream.asBroadcastStream();

  final streamListener1 = stream.listen((event) {
    print('Listener1 : $event');
  });

  final streamListener2 = stream.listen((event) {
    print('Listener2 : $event');
  });

  ctrl.sink.add(1);
  ctrl.sink.add(3);
  ctrl.sink.add('a');

  // Listener1 : 1
  // Listener2 : 1
  // Listener1 : 3
  // Listener2 : 3
  // Listener1 : a
  // Listener2 : a
}
```

### broadcast 예제2

```
import 'dart:async';

void main() {
  final ctrl = StreamController();
  final stream = ctrl.stream.asBroadcastStream();

  final streamListener1 = stream
      .where((event) => event % 2 == 0)
      .listen((event) {
        print('Listener1 : $event');
      });

  final streamListener2 = stream
      .where((event) => event % 2 == 1)
      .listen((event) {
    print('Listener2 : $event');
  });

  ctrl.sink.add(1);
  ctrl.sink.add(2);
  ctrl.sink.add(3);
  ctrl.sink.add(4);

  // Listener2 : 1
  // Listener1 : 2
  // Listener2 : 3
  // Listener1 : 4
}
```

### yield 예제1

```
import 'dart:async';

void main() {
  calculate(2).listen((event) => print('calculate(2): $event'));
  // calculate(2): 0 // 1초 대기 
  // calculate(2): 2 // 1초 대기 
  // calculate(2): 4 // 1초 대기 
  // calculate(2): 6 // 1초 대기 
  // calculate(2): 8 // 1초 대기 
}

Stream<int> calculate(int number) async* {
  for (int i = 0; i < 5; i++) {
    yield i * number;

    await Future.delayed(Duration(seconds: 1));
  }
}
```

### yield 예제2

```
import 'dart:async';

/**
 * Stream yield
 */
void main() {
  calculate(2).listen((event) => print('calculate(2): $event'));
  calculate(4).listen((event) => print('calculate(4): $event'));
  // calculate(2): 0
  // calculate(4): 0 // 1초 대기
  // calculate(2): 2
  // calculate(4): 4 // 1초 대기
  // calculate(2): 4
  // calculate(4): 8 // 1초 대기
}

Stream<int> calculate(int number) async* {
  for (int i = 0; i < 3; i++) {
    yield i * number;

    await Future.delayed(Duration(seconds: 1));
  }
}
```

### yield\* 예제

Future의 await와 비슷하게 동작

```
import 'dart:async';

void main() {
  playAllStream().listen((event) {
    print(event);
  });
  // 0
  // 1
  // 2 // 1초 대기
  // 0
  // 1000
  // 2000 // 1초 대기
}

/**
 * Future의 await와 비슷하게 작동
 */
Stream<int> playAllStream() async* {
  yield* calculate(1); // yield*: calculate(1)의 스트림이 끝날때까지 기다림
  yield* calculate(1000);
}

Stream<int> calculate(int number) async* {
  for (int i = 0; i < 3; i++) {
    yield i * number;

    await Future.delayed(Duration(seconds: 1));
  }
}
```
