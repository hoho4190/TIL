# Functional programming

### 기본 형변환

```
void main() {
  /*
   * []: List
   * {}: Object
   * (): Iterable
   */

  List<String> foods = ['치킨', '피자'];
  print(foods);         // [치킨, 피자]
  print(foods.asMap()); // {0: 치킨, 1: 피자}
  print(foods.toSet()); // {치킨, 피자}

  Map foodMap = foods.asMap();
  print(foodMap.keys);            // (0, 1)
  print(foodMap.values);          // (치킨, 피자)
  print(foodMap.values.toList()); // [치킨, 피자]

  Set foodSet = foods.toSet();
  print(foodSet.toList()); // [치킨, 피자]
}
```

### map method

```
void main() {
  
  // List
  List<String> foods = ['치킨', '피자'];
  final deliFoods1 = foods.map((e) {
    return '맛있는 $e';
  });
  final deliFoods2 = foods.map((e) => '맛있는 $e');
  print(deliFoods2); // (맛있는 치킨, 맛있는 피자)
  print('deliFoods1 == deliciousFoods2: ${deliFoods1 == deliFoods2}'); // false

  // Map
  Map<String, int> contactMap = {
    'foo': 01011110000, 
    'bar': 01055551111
  };
  final newContactMap = contactMap
      .map((key, value) => MapEntry(key, 8200000000000 + value));
  print(newContactMap); // {foo: 8201011110000, bar: 8201055551111}

  // Set
  Set foodSet = {'치킨', '피자'};
  final newFoodSet = foodSet.map((e) => '새 $e');
  print(newFoodSet); // (새 치킨, 새 피자)
}

```

### where method

필터

```
void main() {
  
  // List
  List<Map<String, String>> people = [
    {
      'name': 'foo',
      'address': 'Seoul'
    },
    {
      'name': 'bar',
      'address': 'Incheon'
    }
  ];

  final seoulPeople = people.where((e) => e['address'] == 'Seoul');
  print(seoulPeople);
}
```

### reduce method

컬렉션의 요소를 반복적으로 결합하여 단일 값으로 변경

리턴 타입이 원래 타입과 동일해야 함

```
void main() {

  print('-- reduce(int) -------------');
  List<int> nums = [1, 3, 5, 7, 9];

  // 맨 처음의 prev는 nums[0], element는 nums[1]
  final reduceNum = nums.reduce((prev, element) {
    int total = prev + element;
    print('prev=$prev, element=$element -> total=$total');
    return total;
  });
  print('total=$reduceNum'); // 25



  print('-- reduce(String) -------------');
  List<String> words = ['a', 'bb', 'ccc'];
  print(words.reduce((v, e) => v + ' ' + e)); // a bb ccc
}
```

### fold method

컬렉션의 각 요소를 기존 값과 반복적으로 결합하여 컬렉션을 단일 값으로 변경

리턴 타입이 원래 타입과 달라도 됨

```
void main() {

  print('-- fold(int) -------------');
  List<int> nums = [1, 3, 5, 7, 9];

  int initialValue = 10;
  print('initialValue=$initialValue');

  // 맨 처음의 prev는 initialValue, element는 nums[0]
  final foldNum = nums.fold<int>(initialValue, (prev, element) {
    int total = prev + element;
    print('prev=$prev, element=$element -> total=$total');
    return total;
  });
  print('total=$foldNum'); // 35



  print('-- fold(String) -------------');
  List<String> words = ['a', 'bb', 'ccc'];

  final foldWordLength = words
      .fold<int>(0, (prev, element) => prev + element.length);
  print('foldWordLength=$foldWordLength'); // 6
}
```
