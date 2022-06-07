# Inheritance

모든 객체는 extends Object 생략되어 있음

```
class Person {
  String name;
  int age;

  Person({required this.name, required this.age});

  void introduce() {
    print('${this.name}(${this.age}) 입니다.');
  }

  void greet() {
    print('안녕');
  }
}
```

```
class Man extends Person {
  Man(String name, int age) : super(name: name, age: age);

  @override
  void greet() {
    print('hi');
  }

  void introduceMan() {
    print('남자 ${this.name}(${this.age}) 입니다.');
  }
}
```

```
class Woman extends Person {
  Woman(String name, int age) : super(name: name, age: age);

  @override
  void greet() {
    print('hello');
  }

  void introduceWoman() {
    print('여자 ${this.name}(${this.age}) 입니다.');
  }
}
```

```
void main() {
  print('-- foo ----------');
  Person foo = Person(name: 'foo', age: 20);
  foo.introduce();

  print('-- cheolsu ----------');
  Man cheolsu = Man('cheolsu', 30);
  cheolsu.introduce();
  cheolsu.introduceMan();
  cheolsu.greet();
  print('cheolsu is Person: ${cheolsu is Person}');  // true
  print('cheolsu is Man: ${cheolsu is Man}');        // true

  print('-- younghee ----------');
  Woman younghee = Woman('younghee', 40);
  younghee.introduce();
  younghee.introduceWoman();
  younghee.greet();
  print('younghee is Person: ${younghee is Person}'); // true
  print('younghee is Woman: ${younghee is Woman}');   // true
}
```
