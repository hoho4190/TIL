# Interface

interface 키워드 없음 class로 선언하고 implements 키워드로 인터페이스 구현

인터페이스를 class로 선언하였기 때문에 인스턴스 생성 가능함, 이를 방지하려면 abstract class로 생성 가능

```
// interface
abstract class PersonInterface {
  String name;
  int age;

  PersonInterface(this.name, this.age);

  void introduce();
}
```

```
class Man implements PersonInterface {
  String name;
  int age;

  Man(this.name, this.age);

  void introduce() {
    print('남자 ${this.name}(${this.age}) 입니다.');
  }
}
```

```
class Woman implements PersonInterface {
  String name;
  int age;

  Woman(this.name, this.age);

  void introduce() {
    print('여자 ${this.name}(${this.age}) 입니다.');
  }
}
```

```
void main() {
  print('-- Man ----------');
  Man cheolsu = Man('cheolsu', 30);
  cheolsu.introduce();
  print('cheolsu is PersonInterface: ${cheolsu is PersonInterface}'); // true
  print('cheolsu is Man: ${cheolsu is Man}');                         // true

  print('-- Woman ----------');
  Woman younghee = Woman('younghee', 40);
  younghee.introduce();
  print('younghee is PersonInterface: ${younghee is PersonInterface}'); // true
  print('younghee is Woman: ${younghee is Woman}');                     // true
}
```
