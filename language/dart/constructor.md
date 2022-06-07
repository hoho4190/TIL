# constructor

### 기본 생성자와 named 생성

```
class Person {
  String name;

  // 기본 생성자
  // Person(String name) : this.name = name;
  Person(this.name); // 생성자 간단히

  // named 생성자 - 원하는 이름으로 가능
  Person.fromName(String name) : this.name = name;

  void introduce() {
    print('${this.name} 입니다.');
  }
}
```

```
void main() {
  Person foo = Person('foo');
  Person bar = Person.fromName('bar');
  foo.introduce();
  bar.introduce();
}
```

### Immutable 프로그래밍과 const 생성자

```
class Person {
  final String name;

  // const 생성자
  const Person(this.name);

  Person.fromName(String name) : this.name = name;

  void introduce() {
    print('${this.name} 입니다.');
  }
}
```

```
void main() {
  Person foo = Person('foo');
  Person bar = const Person('bar');
  Person baz = Person.fromName('baz');
  foo.introduce();
  bar.introduce();
  baz.introduce();


  // name이 final이라서 error 발생
  foo.name = 'name is final';

  // const 생성자라서 컴파일 시 DateTime.now()를 알 수 없기 때문에 error
  Person qux = const Person(DateTime.now().toString());
  
  Person quux = Person(DateTime.now().toString());


  // 필드 값이 같아도 다른 객체
  Person mutablePerson1 = Person('name');
  Person mutablePerson2 = Person('name');
  print(mutablePerson1 == mutablePerson2); // false

  // const 생성자로 클래스의 필드 값이 모두 같게 생성 시 같은 객체
  Person immutablePerson1 = const Person('name');
  Person immutablePerson2 = const Person('name');
  print(immutablePerson1 == immutablePerson2); // true
}
```

필드를 final로 선언하면 const 생성자를 만들 수 있음

const 생성자로 const Person(...), Person(...) 두가지로 사용 가능
