> nomadcoders
> https://nomadcoders.co/dart-for-beginners

# Dart Language

- Dart는 **Object Oriented Language**이다

# INTRODUCTION

---

## 0.1 Why Dart

### Compile

- JIT (Just In Time)

dart VM에서 버츄얼 머신을 사용해 컴파일
**개발** 시 변경사항을 빠른 반영으로 결과를 바로 확인할 수 있음

- AOT (Ahead Of Time)

**배포** 환경에서 빠른 속도를 위해 컴파일
여러 아키텍처에 사용할 수 있게 컴파일됨



# VARIABLES

---

## 1.0 Hello World

## main 함수

거의 모든 프로그램 언어에서 필수인 메서드 [ void main() ]
프로그램을 실행시키기 위해서 default로 main을 찾는다

## semicolon (;)

다른 언어는 세미콜론을 빼먹어도 자동으로 추가해주거나 무시하고 컴파일 되는 등 큰 문제가 생기진 않지만,
**다트는 일부러 세미콜론을 쓰지 않는 경우가 있기 때문에** (cascade operator) 세미콜론이 필요한 곳에는 **반드시 세미콜론을 추가**해 주어야한다



## 1.1 Var Type

> var은 함수나 메소드 내부에 지역변수를 선언할 때 사용
> Properties (field parameter)를 선언할 때는 Var을 사용하지 않고 명시적으로 선언

명시적으로 타입을 지정해주지 않고 선언할 수 있음
선언한 타입은 지정한 타입에 맞게 변하고 수정 시 그 타입에 맞아야 함



## 1.2 Dynamic Type

> 변수가 어떤 타입인지 모를때 사용

var로 변수를 선언할 때 초기화시켜주지 않으면 dynamic 타입이다
dynamic으로 변수를 선언하면 if문에서 그 타입의 메서드를 사용 가능하다 (자동완성 기능에서 추천해 줌)

```dart
void main(){
  dynamic name = 'name';
  if(name is String){
    print(name.length);
  }
  else if (name is int){
    print(name.isEven);
  }
}
```



## 1.3 Nullable Variables

> dart의 null safety 기능

dart에서 변수들의 default는 not nullable이기에 null을 사용하고 싶다면 선언하는 타입의 끝에 물음표(?)를 붙여서 nullable임을 명시해 준다

```dart
void main() {
  String? name = 'name';
  print(name.isNotEmpty);
  name = null;
  print(name?.isNotEmpty);
}

/// true
/// null
```



## 1.4 Final Variables

> 변하지 않은 변수를 사용할 때 선언

한 번 정의된 변수를 수정하지 못하게 만든다
타입을 컴파일러가 알아서 추론하기에 굳이 타입을 붙이지 않아도 된다

```dart
void main() {
  final name = 'name';
}
```



## 1.5 Late Variables

> 초기에 변수를 초기화하지 않고 선언할 수 있게 해준다
> 주로 API와 연동할 때 사용

final이나 var앞에 붙여줄 수 있다
변수를 먼저 만들고 데이터를 나중에 넣어줄 수 있게 해준다
데이터를 넣어주기 전까지는 접근할 수 없게 만들어준다

```dart
void main(){
  late final name;
  // print(name); <- error
  name = 'name';
  print(name);
}

/// name
```



## 1.6 Constrant Variables

> 컴파일 전부터 알고있고, 정해져있는 변수에 사용한다

dart의 const 키워드는 다른 언어와 다르게 compile-time constant이다
compile-time constant는 컴파일 할때 하드코딩 되는 것과 같다



## 1.7 Recap (recapitulate)



# DATA TYPES

---

dart의 모든 타입은 object이다

## 2.0 Basic Data Types

String
bool
int
double
num (int와 double의 상위클래스)



## 2.1 Lists

> 리스트의 마지막 element에 ,가 있으면 화면상 정리가 더 잘된다

```dart
var numbers = [1,2,3,4,];
// List<int> numbers = [1,2,3,4,]; 로 컴파일됨
```



### collection if

```dart
var isTrue = true;
var numbers = [
  1,
  2,
  3,
  4,
  if (isTrue) 5,
]
```



## 2.2 String Interpolation

> $ 를 사용해서 String에 변수를 넣을 수 있다
> ${ } 로 계산한 결과를 사용할 수도 있다

```dart
var name = 'name';
var age = 10;
var greeting = "Hello everyone, my name is $name and I'm ${age + 4}";
```



## 2.3 Collection for

```dart
var oldNum = ['4','5'];
var newNum = [
  '1',
  '2',
  '3',
  for (var number in oldNum) 'added $number',
];

/// [1, 2, 3, added 4, added 5]

```



## 2.4 Maps

```dart
var player = {
  'name': 'name',
  'tall': 183.7,
  'age': 30,
}
```



## 2.5 Sets

```dart
var numbers = {1,2,3,4};
// Set<int> numbers = {1,2,3,4};
```



# FUNCTIONS

---

## 3.0 Defining a Fuction

> function이 return 한 줄만 가지고 있을때 fat arrow syntax 사용

```dart
void sayHello(String name){
  print("hello $name!");
}

String sayHello(String name){
  return "hello $name!";
}

// fat arrow syntax
String sayHello(String name) => "hello $name!";
```



## 3.1 Named Parameters

> Positional Parameters 와 반대의 개념
>
> null safety를 위해서 default value를 정해주거나,
> required를 사용해서 Parameter를 항상 받을 수 있게 해줘야한다

```dart
String sayHello({String name = '', int age = 0, String country=''})
  => 'Hello my name is $name, $age and I\'m from $country';

void main(){
  print(sayHello(name: 'name', age: 30, country: 'korea'));
}

/// Hello my name is name, 30 and I'm from korea
```

```dart
String sayHello({required String name, required int age, required String country})
  => 'Hello my name is $name, $age and I\'m from $country';

void main(){
  print(sayHello(name: 'name', age: 30, country: 'korea'));
}

/// Hello my name is name, 30 and I'm from korea
```



## 3.2 Recap



## 3.3 Optional Positional Parameters

```dart
String sayHello( String name, int age, [String? country])
  => 'Hello my name is $name, $age and I\'m from $country';

void main(){
  print(sayHello('name', 30));
}

/// Hello my name is name, 30 and I'm from null
```



## 3.4 QQ Operator (Null Aware Operator)

> ??
> ??=
>
> left ?? right
>
> - left가 null이면 right을 return하고 left가 not null이면 left를 return함
>
> 변수 ??= 값
>
> - 변수가 null이면 값을 할당한다

```dart
String upperCase(String? name)
  => name != null ? name.toUpperCase() : 'Need Name';

void main(){
  print(upperCase('name'));
  print(upperCase(null));
}

/// NAME
/// Need Name
```

```dart
String upperCase(String? name)
  => name?.toUpperCase() ?? 'Need Name';

void main(){
  print(upperCase('name'));
  print(upperCase(null));
}

/// NAME
/// Need Name
```



## 3.5 Typedef

> Type을 alias하는 것
> Map이나 Set같은 복잡한 타입은 class로 정의하는 것이 좋다

```dart
typedef LoI = List<int>;

LoI reverseList(LoI loi)
  => loi.reversed.toList();

void main(){
  print(reverseList([1,2,3]));
}

/// [3, 2, 1]
```



# CLASSES

---



## 4.0 Your First Dart Class

> Class의 Properties를 정의할 때는 var가 아닌 해당 데이터에 대한 정확한 타입을 명시해 주어야 한다
>
> instance를 생성할 때 new를 붙일 필요가 없다
> 클래스의 메서드 생성 시, 클래스 Property는 this. 를 붙이지 않아도 된다. 다만, Property와 동일한 이름의 지역변수가 있다면 this.를 붙어야한다

```dart
class Player {
  String name = 'name';
  int age = 20;
  
  void sayHello(){
    print('Hi my name is $name and I\'m $age');
  }
}

void main(){
  var player = Player();
  player.sayHello();
  player.name = 'name1';
  player.sayHello();
}

// Hi my name is name and I'm 20
// Hi my name is name1 and I'm 20
```



## 4.1 Constructors

> 생성자

```dart
class Player {
  late final String name;
  late int age;
  
  Player(String name, int age){
    this.name = name;
    this.age = age;
  }
  
  void sayHello(){
    print('Hi my name is $name and I\'m $age');
  }
}

void main(){
  var player = Player('name1', 20);
  player.sayHello();
  var player2 = Player('name2', 22);
  player.sayHello();
}

// Hi my name is name1 and I'm 20
// Hi my name is name2 and I'm 22
```



dart에서 생성자는 더 간단하게 구현할 수 있다

```dart
class Player {
  final String name;
  int age;
  
  Player(this.name, this.age); // <--
  
  void sayHello(){
    print('Hi my name is $name and I\'m $age');
  }
}

void main(){
  var player = Player('name1', 20);
  player.sayHello();
  var player2 = Player('name2', 22);
  player.sayHello();
}

// Hi my name is name1 and I'm 20
// Hi my name is name2 and I'm 22
```



## 4.2 Named Constructor Parameters



```dart
class Player {
  final String name;
  int age, backNumber;
  String team, position;

  Player({
    required this.name,
    required this.age,
    required this.backNumber,
    required this.team,
    required this.position,
  });

  void sayHello() {
    print('Hi my name is $name and I\'m $age');
  }
}

void main() {
  var player = Player(
    name: 'name1',
    age: 20,
    backNumber: 15,
    team: 'team1',
    position: 'position1',
  );
  player.sayHello();
  
  var player2 =  Player(
    name: 'name2',
    age: 22,
    backNumber: 19,
    team: 'team2',
    position: 'position2',
  );
  player2.sayHello();
}

// Hi my name is name1 and I'm 20
// Hi my name is name2 and I'm 22
```



## 4.3 Named Constructors ★

> 다양한 생성자를 만드는 방법
> `ClassName.constructure({}):`
> 콜론 이후에 선언된 변수들 매핑한다

```dart
class Player {
  final String name;
  int age, backNumber;
  String team, position;

  Player({
    required this.name,
    required this.age,
    required this.backNumber,
    required this.team,
    required this.position,
  });
  
  Player.createBluePlayer({required String name, required int age}):
  this.name = name,
  this.age = age,
  this.backNumber = 0,
  this.team = 'Blue',
  this.position = 'not fixed';

  void printProperties() {
    print('name=$name\nage=$age\nbackNumber=$backNumber\nteam=$team\nposition=$position\n');
  }
}

void main() {
  var player = Player.createBluePlayer(
    name: 'name1',
    age: 20,
  );
  player.printProperties();
  
  var player2 =  Player(
    name: 'name2',
    age: 22,
    backNumber: 19,
    team: 'team2',
    position: 'position2',
  );
  player2.printProperties();
}

/*
name=name1
age=20
backNumber=0
team=Blue
position=not fixed

name=name2
age=22
backNumber=19
team=team2
position=position2
*/
```



## 4.4 Recap



## 4.5 Cascade Notation

> 인스턴스의 속성들을 수정할 때 한번에 나열하여 수정할 수 있음
> `..` 을 이용하고 연속해서 이어서 재할당 할 수 있음

```dart
class Player {
  final String name;
  int age, backNumber;
  String team, position;

  Player({
    required this.name,
    required this.age,
    required this.backNumber,
    required this.team,
    required this.position,
  });
  
  void printProperties() {
    print('name=$name\nage=$age\nbackNumber=$backNumber\nteam=$team\nposition=$position\n');
  }
}
  
void main() {
  var player1 = Player(name: 'name1', age: 12, backNumber: 10, team: 'red', position: 'striker');
  player1.printProperties();
  player1..age=22..backNumber=33..team='blue'..position='guard'; // Cascade Notation (재할당)
  player1.printProperties();
}

/*
name=name1
age=12
backNumber=10
team=red
position=striker

name=name1
age=22
backNumber=33
team=blue
position=guard
*/ 
```



## 4.6 Enums

> enum은 선택의 폭을 좁혀주는 역할을 한다 (실수 방지)
> 

```dart
enum Team { red, blue }

class Player {
  final String name;
  int age, backNumber;
  Team team;
  String position;
  
  Player({
    required this.name,
    required this.age,
    required this.backNumber,
    required this.team,
    required this.position,
  });
  
  void printProperties() {
 print('name=$name\nage=$age\nbackNumber=$backNumber\nteam=$team\nposition=$position\n');
  }
}

void main() {
  var player1 = Player(name: 'name1', age: 12, backNumber: 10, team: Team.red, position: 'striker');
  player1.printProperties();
}

/*
name=name1
age=12
backNumber=10
team=Team.red
position=striker
*/
// printProperties의 $team 부분을 ${team.name}으로 수정하면 red나 blue의 값을 가져오고, ${team.index}로 수정하면 0이나 1의 결과가 나온다
```



## 4.7 Abstract Classes

> extends로 abstract 클래스를 상속받으면 해당 메서드들을 구현할 책임을 가진다

```dart
abstract class Human {
  void walk();
  String howTall();
  String sayHelloTo(String name);
}
```



## 4.8 Inheritance

```dart
enum Team { red, blue }

class Human {
  final String name;
  Human({required this.name});
  void sayHello() {
    print('Hi my name is $name');
  }
}

class Player extends Human {
  int age, backNumber;
  Team team;
  String position;
  
  Player({
    required String name,
    required this.age,
    required this.backNumber,
    required this.team,
    required this.position,
  }) : super(name : name);
  
  @override
  void sayHello() {
    super.sayHello();
    print('and I play for ${team}');
  }
  
  void printProperties() {
 print('name=$name\nage=$age\nbackNumber=$backNumber\nteam=${team.index}\nposition=$position\n');
  }
}

void main() {
  var player1 = Player(name: 'name1', age: 12, backNumber: 10, team: Team.blue, position: 'striker');
  player1.printProperties();
  player1.sayHello();
}

/*
name=name1
age=12
backNumber=10
team=1
position=striker

Hi my name is name1
and I play for Team.blue
*/
```



## 4.9 Mixins

> Mixin은 **생성자가 없는 클래스**의 **메서드와 속성**을
> `with` 키워드를 이용해서 가지고 올 수 있다

```dart
enum Team { red, blue }

class Tall {
  late final int tall;
}

class Jump {
  void jump() {
    print('Jump!');
  }
}

class Player with Tall, Jump {
  final String name;
  int age, backNumber;
  Team team;
  String position;

  Player({
    required this.name,
    required this.age,
    required this.backNumber,
    required this.team,
    required this.position,
  });

  void printProperties() {
    print(
        'name=$name\nage=$age\nbackNumber=$backNumber\nteam=$team\nposition=$position\n');
  }
}

void main() {
  var player1 = Player(
      name: 'name1',
      age: 12,
      backNumber: 10,
      team: Team.red,
      position: 'striker');
  player1.printProperties();
  player1.jump();
  player1.tall = 180;
  print(player1.tall);
}

/*
name=name1
age=12
backNumber=10
team=Team.red
position=striker

Jump!
180
*/
```
