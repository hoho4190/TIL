# private, getter && setter



```
class Person {
  // class, function, field 에 _붙이면 private 됨
  String _name;

  Person(this._name);

  // getter
  String get name => this._name;

  // setter - 오직 하나의 파라미터만 가
  set name(String name) => this._name = name;

  void introduce() {
    print('${this._name} 입니다.');
  }
}
```

```
void main() {
  Person foo = Person('foo');
  print(foo.name);

  foo.name = 'bar';
  print(foo.name);
}
```
