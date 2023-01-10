> nomadcoders
> https://nomadcoders.co/dart-for-beginners

# Dart Language



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

>>> true
>>> null
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

>>> name
```



## 1.6 Constrant Variables

> 컴파일 전부터 알고있고, 정해져있는 변수에 사용한다

dart의 const 키워드는 다른 언어와 다르게 compile-time constant이다
compile-time constant는 컴파일 할때 하드코딩 되는 것과 같다



## 1.7 Recap (recapitulate)

