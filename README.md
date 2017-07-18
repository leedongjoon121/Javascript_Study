# Javascript_Study
자바스크립트를 공부하며, 잊지 말아야 할 내용들을 정리

---
layout: post
comments: true
title: Swift 언어의 기초
tags: iOS Swift dinfree
---


**Index**

* TOC
{:toc}

**Resources**

* 스위프트로 시작하는 아이폰 앱 개발 교과서
* [The Swift Programming Language (Swift 3.0.1)-Apple](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/index.html#//apple_ref/doc/uid/TP40014097-CH3-ID0)
* swift_basic_dinfree.playground

---

## 1. 시작하기
완전한 Swift 명령은 statement 이다. 하나의 statement는 기본적으로 라인으로 구분한다.

```swift
print("hello")
print("world")
```

만일 한줄에 두 statement 를 작성하려면 ";"로 구분해야 한다.물론 세미콜론은 항상 붙여도 상관 없다.

`print("hello"); print("world")`

주석은 다른 프로그램언어와 동일한 스타일을 지원한다.

```swift
print("hello") // 주석입니다.
/* 이것도 주석 입니다. */
print("world")
```

블럭 구조는 `"{ }"` 로 구분한다. 라인 구분 없이 작성하는 것도 가능 하지만 보기에 좋지 않기 때문에 권장되지 않는다.

```swift
class Doc {
    func bark() {
        print("woof")
    }
}
```

#### Swift 언어의 특징
+ **빠르다** : 새로운 설계로 기존 Objective-C보다 실행속도가 빠름. Swift라는 단어는 빠르다 혹은 '칼새'라는 의미를 가지고 있다. Swift 로고가 바로 칼새.
+ **현대적이다** : Scala, JavaScript, Phython, Ruby 등 새로운 언어의 특징을 수용함.
+ **안전하다** : 문법적으로 실행 중에 오류가 발생하기 어려운 구조로 만들어짐. 실행중 발생할 수 있는 오류를 문법오류(ex. optional)로 알려줌. Swift3 에 이르러서는 실행중에 오류가 나는 프로그램을 만드는것 자체가 어려워짐.




---

## 2. 기초 문법

### 2.1 변수 선언
+ var : 변수
+ let : 상수
+ 타입 지정

```
변수명: 타입 형식임. `ex) myVar: Int`
```
+ 명명 규칙

| Name        |     Description      |               Example |
| :---------- | :------------------: | --------------------: |
| Camel Case  | 두번째 단어부터 시작 단어를 대문자로 |   myData, productName |
| Pascal Case |  모든 단어의 시작 단어를 대문자로  |   MyData, ProductName |
| Snake Case  |    단어 사이에 언더바를 붙임    | my_data, product_name |




