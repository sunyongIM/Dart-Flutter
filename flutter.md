> nomadcoders
> https://nomadcoders.co/flutter-for-beginners



# Flutter



## 1.2 Why Flutter

> 하나의 언어(dart)와 하나의 프레임워크(flutter)로 ios, 안드로이드, 웹, 맥OS, 윈도우,  리눅스, 임베디드 등을 구현할 수 있다

Wonderous 어플리케이션 구경
flutter.dev/showcase



## 1.3 How Flutter Works

> 네이티브 프레임워크는 운영체제와 직접적으로 소통하며 작동하지만, 플러터는 C와 C++로 작동하는 엔진을 통해 렌더링과 기능들을 구현한다 (비디오 게임의 엔진과 비슷하다)
> 그렇기에 플러터는 플랫폼의 Native Widget을 사용하지 않는다
>
> 플랫폼은 자신의 운영체제의 기능들을 이용하는 대신 플러터의 엔진을 구동시킨다
>
> 비록 네이티브 위젯을 사용하지 못하지만, 플러터를 통해서 통제할 수 있는 범위가 넓어진다 (호스트에 의존할 필요가 없다)



## 1.4 Flutter vs React Native

> 운영체제의 기본 버튼, 네비게이션, 동작 스타일등의 화면이 필요하다면 리엑트 네이티브
> 운영체제에 존재하지 않는 기능을 구현해야 하거나, 기존의 스타일과 다르게 커스터마이징 하고싶다면 플러터



## 1.5 Recap

플러터로 만든 어플리케이션이 다양한 플랫폼에서도 동작 가능한 이유
-> 플랫폼의 운영체제와 독립적으로 플러터 엔진이 UI를 그리고 렌더링하기 때문 (자바스크립트도 사용하지 않음)



## 2.0 Installation

> 콘솔설치가 제일 쉽고 깔끔하다

window는 chocolatey를 이용, mac은 homebrew를 이용해 설치하자

simulator는 document를 읽고 따라하면 된다



## 2.1 Dart Pad

> dart pad에서도 flutter를 실행할 수 있다 (javascript로 컴파일 가능하기 때문)
> 하지만 dart pad에서는 파일을 생성하지는 못한다



## 2.2 Running Flutter

## 2.3 Hello World

> runApp은 'package:flutter/material.dart'를 import 받아서 사용할 수 있는 메서드이다
>
> Widget을 만들기 위해서는 flutter SDK에 있는 3개의 core Widget중에 하나를 상속받아야 한다 (그렇지 않다면 그냥 클래스에 불과하다)

## core Widget

1. StatelessWidget
2. StatefulWidget
3. ??



### build 메서드

build는 Widget의 UI를 만드는 메서드이다 (따라서, 모든 Widget에 필요한 메서드이다)
build 메서드는 Widget을 return 해야한다



### root Widget - 앱의 시작 위젯

root Widget은 MaterialApp이나 CupertinoApp 위젯을 return 해야한다
MaterialApp - 구글의 디자인 시스템
CupertinoApp - 애플의 디자인 시스템

*커스텀 앱을 만들고 싶다고 해도 위의 두 위젯 중 하나를 선택해야한다*
주로 MaterialApp을 선택한다

property - home



### Scaffold Widget

스캐폴드 위젯은 위젯들을 정렬하고 화면에 맞게 구현하기 위해 필요한 골격이다
property - appBar, body ...