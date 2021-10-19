# Visibility modifiers(접근제어자, 접근제한자)

## 정

|           | 같은 class | 같은 module    | 다른 module    | 제한 없음 |
| --------- | -------- | ------------ | ------------ | ----- |
| private   | O        |              |              |       |
| protected | O        | (상속 받았을 때 O) | (상속 받았을 때 O) |       |
| internal  | O        | O            |              |       |
| public    | O        | O            | O            | O     |

public > protected | internal > private

* private : 속해있는 class 에서만 접근 가능
* internal : private + 같은 모듈 안에서 접근 가능
* protected : private + 상속받은 클래스에서도 접근 가능
* public : protected + 접근 제한 없음

project > module > package > class

* project - 최상위 개념이다. 여러 module을 가질 수 있다
* module - 여러 package를 가질 수 있다
* package - 여러 member, function, class 를 가질 수 있다
* class - member, function을 가질 수 있다

## Reference

* [Visibility modifiers](https://kotlinlang.org/docs/visibility-modifiers.html)
* [접근제한자, 접근제어자 (public, private, protected, internal) 이 뭔데?](https://wellohorld.tistory.com/156)
