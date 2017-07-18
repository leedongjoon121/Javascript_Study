# Javascript_Study
자바스크립트를 공부하며, 잊지 말아야 할 내용들을 정리

---
layout: post
comments: true
title: Swift 언어의 기초
tags: iOS Swift dinfree
---

이 문서는 Swift 언어에 대한 특징과 기본문법, 핵심 개념등을 다루고 있다.<BR>
작성자: 황희정 , 마지막 수정: 2017.1.10

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



### 2.2 String and Int

+ 숫자 사이에 ` _ ` 를 넣어 보기 좋게 구분할 수 있다. 실제 프로그램에서는 없는것으로 인식됨. 예를 들어 1_235는 1235와 같다.
+ 문자열 결합시 + 연산자 사용이 가능함.
+ 변수를 포함해서 포맷팅하는 경우 `\(변수명)` 과 같이 사용할 수 있음.
+ 형변환은 자료형(변환변수) 형태로 사용함

```swift
let inputString = "100"
let answer = Int(inputString)! * 5
let msg = "\(name)님 사랑합니다."
let intValue = Int(123.45)
```



### 2.3 if, switch statement

+ 조건을 괄호에 넣지 않아도 됨.
+ switch 에는 break 문을 사용하지 않아도 됨.



### 2.4 for, while statement

+ `for n in 1…10 { }` , 1~10 까지
+ `for _ in dogNames{  }`  배열 출력의 경우임, "_"는 사용되지 않는 단순 for 진행 변수인 경우 사용함.
+ 반복문에서 print() 사용시 terminator 를 지정해 구분자로 사용할 수 있음(기본은 newline)

```swift
 for msg in array2 {
 	print(msg,terminator:"/")
}
```

+ wihle문 역시 for 와 유사한 구조를 가짐. `do ~ while` 과 같은 개념인 `repeat ~ while` 사용할 수 있음.



### 2.5 Collection Type

> Swift 의 Collection 타입은 Array, Set, Dictionary 이다. 이들은 모두 Foundation framework 의 NS 에 대한 bridge 타입이다.

![iOS Architecture](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/Art/CollectionTypes_intro_2x.png){:width="640px"}

**Array**

> 배열은 순차적으로 같은 타입의 데이터를 저장한다. 배열에 들어갈 자료형은 Array<Element> 와 같이 표현해야 하나 [자료형]과 같이 줄여(short hand) 사용하는 것이 가능 하다.

+ var	intArray = [Int]()
+ var intArray = [1,2,3]
+ var intArray:Int = [1,2,3]
+ var anotherThreeDoubles = Array(repeating: 2.5, count: 3) // 2.5 를 3개 생성
+ 배열 크기는 intArray.count 로 구함
+ append, insert(), remove()/removeAll() 메서드 사용
+ intArray.insert(5, at:2)
+ 배열 정렬은 sorted(by: < or > )

```swift
// 배열 데이터 출력
for value in intArray {
    print(value)
}
// 인덱스와 함께 출력하는 경우
for (index, value) in array2.enumerated() {
    print("\(index): \(value)")
}
```

**Set**

> Set 은 특정한 이름으로 묶여진 자료의 집합. Set<Element>와 같이 사용함.

```swift
var	numbers = Set<Int>()
numbers.insert(1)
var set2: Set = ["Hyundai", "BMW", "AUDI"]
for maker in set2.sorted() {
	print(maker)
}
```

**Dictionary**

> Dictionary 는 Key,Value 쌍의 자료 구조임. JSON 메시지와 유사한 구조로 프로그램에서 활용도가 높음. Dictionary<Key, Value> 구조로 선언함.

+ key:value 구조, 자료형 상관 없음. 선언시 자료형 지정 가능
+ var memList = ["1": "홍길동", "2": "아무개", "3": "김길동"]
+ var memList = [Int: String]()
+ Dictionary 값 참조는 인덱스로 하고 리턴값은 *Optional* 임.
+ 추가시 새로운 키로 값 할당하면 되고 삭세시 removeValue(forKey:) 사용
+ for 문을 사용할 경우 (key,value) 변수로 접근 가능

```swift
var products1:[String:Int] = ["apple iphone":1000000,"samsung S7":2000000]
var products2 = ["apple iphone":1000000,"samsung S7":2000000]
print(products2["apple iphone"]!)

// 딕셔너리를 튜플로 핸들링
for(key, value) in memList {
  print("memList[\(key)]=\(value)")
}
```



### 2.6 Tuple

+ 튜플은 여러 개의 데이터를 묶음으로 관리하는 자료형으로 서로 다른 데이터 타입으로 구성이 가능함.

```swift
  let myTuple = (1001, "황희정", "010-1111-1111", 40)
  print(myTuple.2)
  var (id, name, tel, age) = myTuple
  print(name)
```



### 2.7 Function, Method

+ 클래스안에서 사용하는 함수 -> 메서드
+ func 키워드를 사용함.
+ _func fname(매개변수:타입, ...) -> 리턴타잎 { }_
+ 다른 언어와의 차이는 함수 호출시 매개변수 이름과 값을 함께 사용해야 한다는점.
+ 매개변수는 호출용과 내부용이 있으며 호출용은 `_` 를 사용해 생략가능.

```swift
func calcData(num1:Int , num2:Int) -> Int {
  return num1+num2
}
print(calcData(num1:20, num2:50))

// 튜플 형식의 리턴
func calcData(num1:Int , num2:Int) -> (String, Int) {
  return ("계산결과는=", num1+num2)
}

let (msg, result) = calcData(num1:20, num2:50)
print("함수 호출의 \(msg) \(reslt) 입니다")
```



### 2.8 Access Control

> swift 2.x 까지는 public, internal, private 접근 제어가 있고 자바와 유사한 의미로 이해하고 사용하는데 무리가 없었으나 swift3 에서 변경된 부분이 있어 정확하게 알아둘 필요가 있다.

* **open**
    * open으로 선언된 클래스와 클래스의 멤버에 대해서는 같은 모듈내에서나 이 모듈을 임포트(import)한 다른 모듈에서 접근할 수 있다.
      * open 으로 선언된 클래스를 상속 할 수 있고 멤버를 오버라이드 할 수 있다.
* **public**
    * open과 마찬가지로 어떤 모듈에서든 접근할 수 있다. 단, 상속과 오버라이딩은 제한적임.
    * 같은 모듈 내에서의 상속만 가능. public 멤버를 오버라이드하는 것도 동일 모듈에서만 허용됩니다. 프레임워크와 같이 구조적으로 분리된 체계를 만든다면 public과 open의 차이를 구별해서 사용해야 함.
    * 프레임워크의 사용자가 서브 클래스를 만들거나 메서드를 오버라이드할 수 있도록 허용하려면 open 으로 선언.
* **internal**
    * 같은 모듈 내에서만 접근을 허용합니다. 모듈의 외부에서는 접근할 수 없습니다.
    * 디폴트 액세스 레벨.
* **fileprivate**
    * 같은 소스 파일 내부에서만 접근이 가능합니다.
    * extension 에서 접근 가능함.
* **private**
    * 선언된 스코프 내에서만 접근이 가능합니다.
    * 만일 기존과 같이 extension 에서 접근 가능하려면 fileprivate 로 선언해야 한다.
* **final**
    * final 은 접근제어자는 아니지만 open 을 제외한 모든 접근제어자에 함께 사용될 수 있다.
    * 상속이나 메서드 오버라이딩 등을 금지할 수 있음.



#### 2.9 Swift 언어의 에러 처리

> Swift는 런타임에 회복 가능한 에러를 던지고, 잡고, 전파하고, 조작하는 first-class support를 제공한다(throwing, catching, propagating, and manipulating recoverable errors at runtime).
> 몇몇 함수와 메소드는 항상 완전한 실행과 유용한 정보를 출력한다고 보장할 수 없다. 물론 Optional은 값의 부재를 표현하기 위해 사용되지만 함수가 실패했을때 실패원인을 이해하고 거기에 맞춰 코드를 대응하는게 더 유용할때가 있다.

* **Optional**
  * Optional 자체가 에러처리는 아니지만 잘못된 변수 참조로 인한 프로그램 오류를 사전에 방지할 수 있기 때문에 적절한 Optional 변수의 사용은 에러처리에 도움이 된다.

* **Error**
  * Error 은 Swift의 에러타입을 지정하기 위한 프로토콜 이다. 따라서 커스텀 에러타입을 지정하려면 Error 을 구현해야 하며 보통은 관련된 에러를 묶어 Enumeration 타입(enum) 으로 정의해 사용한다.
  * Error 사용예

  ```swift
  enum AddrBookError: Error {
      case InvalidRequest(validUrl: String)
      case NotFound
      case NotAdded
  }
  ```

* **Throwing Error**
  * 에러 처리는 기본적으로 자바언어와 거의 유사하다. 함수 혹은 메서드에서 에러를 던질 수 있다는 것을 표현하기 위해 throws 키워드를 사용한다. `func canThrowErrors() throws -> String`

* **try - catch Error**
  * throws 메서드를 호출할 경우 자바와 마찬가지로 try ~ catch 구문으로 처리 해야 한다. `do` 블럭을 이용해 요청 메서드를 사용하고 이때 try 를 지정한다. catch 에서의 처리는 일종의 콜백 메서드의 형태로 파라미터에 전달된 값을 사용할 수 있다.

```swift
  	enum AddrBookError: Error {
  		case InvalidRequest(validUrl: String)
  		case NotFound
  		case NotAdded
  	}

  	class ErrorTest {
  		func request(rurl url: String) throws {
  			throw AddrBookError.InvalidRequest(validUrl: "required url")
  		}
  	}

  	let test = ErrorTest()
  	do {
  		try test.request(rurl: "request url")
  	}
  	catch AddrBookError.InvalidRequest(let url) {
  		print("error:\(url)")
  	}
```



----

### 3. 주요 핵심 개념 정리

#### 3.1 Any, AnyObject
> Swift 에서는 특정되지 않은 타입을 위해 Any와 AnyObject 라는 특수한 타입을 제공 한다. 프로그램에서 특정할 수 없는 상황에서 활용할 수 있다. Any와 AnyObject는 프로토콜로 Swift에서 사용 가능한 모든 타입은 Any를 따르도록 설계되었고, 모든 클래스들에는 AnyObject 프로토콜이 적용되어 있다.

* Any 는 함수 타입을 포함한 모든 타입을 대표할 수 있다.
* AnyObject 는 클래스 타입의 인스턴스 타입만 대표할 수 있다.



#### 3.1 Optional

> Optional 은 Swift 에서 애플리케이션의 크래시를 예방하기 위한 안전기능으로 변수나 상수에 nil이 들어가는 경우 문제가 생기는 것을 방지하기 위한 목적을 사용한다. 변수나 상수에 nil 을 직접적으로 대입하면 컴파일 오류가 발생하지만 특히 변수의 경우 프로그램 중간에 제대로 값이 전달되지 못해 nil 을 참조할 수 있으면 이경우 문제가 될 수 있다.

* nil : 존재하지 않는 객체의 포인터, 값이 없는게 아니라 값이 없는 객체인 nil 을 지정하는 것
* 변수명:타입? 형태, 초기화 하지 않아도 기본이 nil, Wrap 한다고 함.
* Optional 변수를 그냥 하용하게 되면 nil 을 참조할수도 있으므로 그냥사용하면 안되고 nil 체크를 해야함.
* 사용은 유효성 체크후 변수명뒤에 ! 를 붙여서 사용
* Optional 은 내부적으로 Optional(값) 형태로 저장되어짐. ! 를 붙이면 Optional 을 빼고 값만 가지고옴. -> Unwrap

  ```swift
    // un-wrap 해서 사용 ! 이용
    var varInt:Int? = 100
    var result = varInt! + 20

    // 암묵적인 un-wrap 변수에 넣어서 꺼내기
    var varInt:Int? = 100
    var testInt:Int! = varInt
    var result = testInt + 20
  ```

* **Optional Binding**

> 옵셔널 바인딩은 옵셔널 값의 존재 여부를 검사하고 존재한다면 다른 변수에 값을 대입해 사용하는 방식을 말한다.

* 기본적으로는 if let 을 사용하며 여러 옵셔널을 한번에 바인딩 할 수 있고 조건을 추가할수도 있다.

  ```swift
  // if let 을 Optional Binding

  var varInt:Int? = 100

  if let tmp = varInt {

    print(tmp)

  }

  // 하나의 if로 여러 옵셔널 값을 바인딩하는 경우, 모든 옵셔널 값이 존재해야만 if 블럭이 실행됨

  if let name = optionalName, email = optionalEmail {

    // name과 email 값이 존재

  }

  // 옵셔널 바인딩에 조건을 추가 하는 경우, 옵셔널 바인딩 이후 조건 체크가 이루어지게 됨.

  if let age = optionalAge, age >= 20 {

      // age의 값이 존재하고, 20 이상입니다.

  }
  ```

* **Guard**

> if let 을 이용한 옵셔널 바인딩에 의해 대입된 변수는 if 블럭에서만 사용할 수 있으므로 실제 프로그램에서 불편한 점들이 있다. 이를 보완한 개념이 guard를 사용한 방법임.

	* guard 를 사용하면 옵셔널 값을 새로운 변수로 받고 그렇지 않은 경우 return 을 통해 아무런 처리도 안하게 됨.

```swift
	func testGuard(_ testInt:Int?) {
	  guard let tmp = testInt else {
		return
	  }
	  print(tmp)
	}
	var varInt:Int? = 100 // 값을 넣지 않으면 nil 이 되어 guard 에서 return 되어 출력문 실행 안됨.
	testGuard(varInt)
```

* **Optional Chaining**

> 옵셔널 체이닝은 옵셔널 사용을 좀 더 간결하게 만들어주는 swift 언어의 특징으로 옵셔널의 바인딩 과정을 ? 키워드로 줄여주는 역할을 한다.

* 예를 들어 다음과 같은 배열이 선언되어 있고 중간에 배열이 비어있는지을 확인해야 한다고 할때

```swift
let array: [String]? = []
```
옵셔널 바인딩을 통한다면 다음과 같이 코드를 작성할 수 있을것이다.
```swift
if let array = array, array.isEmpty {
	isEmptyArray = true
} else {
	isEmptyArray = false
}
```
옵셔널 체이닝을 사용하면 다음과 같이 코드를 줄일 수 있다.

```swift
	let isEmptyArray = array?.isEmpty == true
```



#### 3.2 Type Casting(형변환)

> 타입 캐스팅은 인스턴스의 타입을 명확히 함으로써 인스턴스의 기능을 사용할 수 있도록 하는 데 목적이 있다. 속성 접근이나 나 메소드 호출 또는 특정 클래스의 서브클래스 혹은 프로토콜을 준수하는 지 확인할때 필요함.
> is와 as 오퍼레이터를 이용해 타입 캐스팅을 할 수 있다.

* is 연산자는 타입 체크 연산자로서, 인스턴스가 특정 서브클래스 타입인지를 체크함. 주로 if나 switch 조건문에서 많이 사용.
* 서브클래스의 인스턴스로 형변환 하는 경우 as 연산자를 이용해 서브클래스 타입으로 변환할 수 있는데, 이것을 다운캐스트라고 함.

그런데 이러한 다운캐스트는 실패의 가능성이 있기 때문에 두가지 방식을 제공함.

* as? 는 다운캐스트 하려는 타입의 옵셔널 값을 리턴하며, as 는 다운캐스트한 뒤 그 결과를 force unwrap 한다.
- 타입캐스트가 성공하리라는 보장이 없으면 as?를 사용하는 것이 안전. 잘못된 타입으로 as 다운캐스트를 하면 런타임 에러 발생.
* as!는 강제 변환 연산임. !는 변환이 실패할 수도 있다는 것을 의미하며, 실패시에는 크래시를 일으킬 수 있음.



#### 3.3 Enumeration Type

> enum 은 Swift 의 Enumeration Type 이다. 다른 프로그래밍 언어와 마찬가지로 Enumeration Type 은 프로그램내에서 명확한 참조나 가시적인 코딩을 위해 매우 유용 하다.

* enum은 기본적으로 raw value 라고 하는 기본값들을 가질 수 있다. 대부분은 언어에서 Int 를 기본으로 하지만 Swift 에서는 String를 비롯해 다른 객체 타입도 사용이 가능하다.
* Int 의 경우 기본값은 자동으로 증가 한다.
* description() -> String 과 같은 간단한 함수를 통해 각각에 대해 표현값을 설정할 수 있다.

```swift
    enum RequestMethod: Int {
    	case GET = 1 // 시작값이되고 나머지 값은 자동 증가 할당. 지정하지 않으면 0 부터 시작됨.
    	case POST
    	case PUT
    	case PUSH
    	case DELETE

    	func description() -> String {
    		switch self {
    		case .GET: // RequestMethod.GET 이어야 하지만 eum 선언내 이므로 생략가능
    			return "http://xxx.com/getall"
    		case .POST:
    			return "http://xxx.com/add"
    		default:
    			return "unknown"
    		}
    	}
    }

    print(RequestMethod.GET.rawValue)
    print(RequestMethod.POST.rawValue)
    print(RequestMethod.GET.description())
```

* 타입을 예측할 수 있다면 타입명의 생략이 가능함.

```swift
    func request(with method: RequestMethod) {
      	print(method)
    }
    request(with: .DELETE) // 함수 인자 타입이 정의 되어 있어 추론이 가능한 부분이라 .으로 사용
    let method: RequestMethod = .PUSH // 타입 지정으로 타입명 생략 가능.
```

* 연관값을 가질수 있다. 앞의 Error 처리에서 살펴본바 있다. 이렇게 타입이 설정된 값은 if-case 혹은 switch 문을 통해 꺼내올 수 있다.
* 앞의 에러 처리 예의 코드를 활용해 값을 출력하는 코드는 다음과 같다.

```swift
    let error:AddrBookError = .InvalidRequest(validUrl: "test")
    if case AddrBookError.InvalidRequest(let method) = error {
    	print(method)
    }
```

* 재미있는 사실은 Optional 이 enum 타입이라는 것이다.

```swift
    public enum Optional<Wrapped> {
    	case none // nil 인 경우
    	case some(Wrapped)
    }
```





----

### 4. 클래스, 프로토콜, 클로저

#### 4.1 클래스 와 구조체
* 객체지향의 기본적인 개념은 다른 객체지향 언어와 대동소이 하다.
* 클래스는 class 로 구조체는 struct 로 정의 한다.
* 클래스는 참조(reference)를 이용하고 구조체는 복사(copy)해서 사용한다.
* 클래스는 상속이 가능하고 구조체는 안됨.
* 객체 생성시 new 키워드가 필요없이 클래스이름() 과 같이 생성

```swift
// 기본 클래스 생성
class TestClass {
    var num:Int = 10;

    func getNum() -> Int {
        return num
    }
}

// 클래스 상속
class TestClass2 : TestClass{
    var num2:Int = 10;
    // 오버라이딩
    override func getNum() -> Int {
        return num2+100
    }
}

// 기본 구조체 생성
struct TestStruct {
    var num:Int = 10;

    func getNum() -> Int {
        return num
    }
}

var tc: TestClass = TestClass()
var tc2: TestClass2 = TestClass2()

print(tc.getNum())
print(tc2.getNum())

// 클래스 참조 테스트, tc 의 num을 20으로 변경하고 tc3 에서 출력해도 참조이므로 20 출력
tc.num = 20
var tc3 = tc
print(tc3.getNum())

// 구조체의 경우 복사 개념으로 ts와 ts2 는 서로 다름 따라서 ts 의 값을 변경해도 ts2 는 영향 없음.
var ts: TestStruct = TestStruct()
var ts2 = ts

ts.num = 20
print(ts2.getNum())
```

클래스와 구조체 모두 생성자를 가질 수 있으며 속성의 초기값 지정등의 역할을 수행. 실제 클래스의 멤버(속성)의 경우 옵셔널이 아닌경우 반드시 초기값을 가져야 하는데 이때 선언시 혹은 생성자에서 초기값을 부여해야 컴파일러 에러가 발생하지 않음.

* 서브 클래스에서 생성자를 만드는 경우 반드시 override 를 명시해 주어야 한다.
* 서브 클래스에서 슈퍼클래스의 속성에 접근하려면 생성자에서 super.init() 한 이후에 가능 하다.


```swift
class Car {
  var model: String?
  var maxSpeed: Int

  init() {
    self.maxSpeed = 150
  }
}
```



#### 4.2 Protocol

> 프로토콜은 자바의 Interface 와 같은 개념으로 최소한 가져야할 속성이나 메서드를 정의 한다. 물론 구현부는 없고 오로지 정의만 한다. 앞에서 살펴본 Any와 AnyObject가 바로 프로토콜 이다. 프로토콜을 사용하면 프레임워크 설계등을 할 수 있고 iOS 앱 개발시 Delegate 구현에도 활용할 수 있다.

* 프로토콜은 클래스와 구조체에 적용할 수 있다. 이 경우 프로토콜에서 선언된 모든 메서드를 구현해 주어야 한다.
* 프로토콜은 다른 프로토콜을 따를 수 있다.
* Swift 에서 기본적으로 제공하는 주요 프로토콜중 CustomStringConvertible 은 자바의 toString() 처럼 description() 메서드를 통해 문자열로 커스텀 객체 정보 혹은 메시지 출력을 가능하게 한다.

```swift
    struct Car: CustomStringConvertible {
    	var model: String
    	var maker: String
    	var description: String {
    		return "\(maker) \(model)"
    	}
    }

    let genesis = Car(model: "제네시스 G80", maker: "현대 자동차")
    print(genesis)
```

* ExpressibleByXXXLiteral 프로토콜은 특정 타입을 Literal 즉, 객체 생성이 아닌 값 대입의 형태로 사용할 수 있게 해준다. 예를들어 swift 는 문자열이나 숫자 모두 객체 타입이지만 대입형으로 사용해도 되는데 바로 이 프로토콜이 적용되어 있기 때문 이다.

```swift
    struct Car2: ExpressibleByStringLiteral{
    	typealias StringLiteralType = String
    	var model: String

    	init(rawValue: String) {
    		model = rawValue
    	}
    		public init(unicodeScalarLiteral value: String) {
    			self.init(rawValue: value)
    		}

    		public init(extendedGraphemeClusterLiteral value: String) {
    			self.init(rawValue: value)
    		}

    		public init(stringLiteral value: String) {
    			self.init(rawValue: value)
    		}
    }

    let grandure: Car2 = "그랜저 3.0"
    print(grandure.model)
```



#### 4.3 함수

> Swift 에서도 함수에 대한 기본적인 개념은 일반적인 프로그래밍 언어와 동일하다. 클래스에 사용된 함수는 메서드라고 부르지만 함수 선언이 func 인 관계로 크게 명칭을 구분해서 하는것 같지는 않다. 리턴 타입은 ` -> `로 지정 한다.

* **Swift 함수의 특징**
  * 함수를 호출할때 파라미터 이름을 사용할 수 있으며 호출시 이름과 내부사용 이름을 다르게 할수도 있다.
  * `_` 를 사용해 호출 파라미터 이름은 생략이 가능하지만 사용하는 것이 코드 가독성 측면에서는 좋다.
  * 파라미터에 기본값을 할당할수도 있으며 이 경우 해당 파라미터는 생략이 가능함.
  * `...`을 사용하면 개수가 정의 되지 않은 파라미터를 받을수 있다.

```swift
    func sum(_ numbers: Int...) -> Int {
    	var sum = 0
    	for number in numbers {
    		sum += number
    	}
    	return sum
    }

    sum(1, 2)
    sum(3, 4, 5)
```

* 함수안에 함수를 정의하는 것도 가능 하다.

```swift
    func printMsg(msg: String, time: Int) {
    	func message(msg: String) -> String {
    		return msg
    	}

    	for _ in 0..<time {
    		print(message(msg: msg))
    	}
    }

    printMsg(msg: "Hello World",time: 3)
```

* 함수안에 정의된 함수를 리턴 하는 것도 가능 하다. 함수 리턴이라는 의미로 (파라미터)를 사용한다.

```swift
    func msgGenerator(message: String) -> (String) -> String {
    	func gen(name: String) -> String {
    		return message + name
    	}
    	return gen
    }

    let gen = msgGenerator(message: "가천대학교 컴퓨터공학과 ")
    gen("황희정")
```

#### 4.3 Closure
> 클로저는 현대적 프로그래밍 모델이라고 하는 함수형 프로그래밍 언어 Clojure 와 마찬가지로 함수형 프로그래밍 모델을 Swift 에서 지원하기 위해 만든 개념이다. 기본적으로 함수와 유사하지만 이름과 정의가 없으며 파라미터를 받을수 있고 리턴값을 가질 수 있다. 일반적인 함수를 이름이 있는 클로저 라고 한다면 이해가 쉬울 것이다.클로저는 구조로서의 특징도 중요하지만 컴파일러 내부적으로 실행되는 구조에 특장점이 있으며 고속의 병렬 프로그래밍을 보다 효과적으로 구현할 수 있다는 장점이 있다.

* 클로저는 `{ }`로 감싸며 리턴은 일반 함수와 같이 `->`로 표현 한다. 클로저의 실행부는 in 키워드를 사용해 구분한다.
* 함수의 마지막 예제를 클로저로 변경하면 다음과 같다.

```swift
       func msgGenerator(message: String) -> (String) -> String {
       	return { (name:String) -> String in
       		return message + name
       	}
       }
```

* 타입 추론을 활용하면 코드를 더 단순화 할 수 있다. 여기서는 파라미터와 리턴타입이 제공되므로 다음과 같이 클로저 코드를 줄일 수 있다.

```swift
       func msgGenerator(message: String) -> (String) -> String {
       	return { (name) in
       		return message + name
       	}
       }
```

* 타입 추론을 활용하면 코드를 더 단순화 할 수 있다. 여기서는 파라미터와 리턴타입이 제공되므로 다음과 같이 클로저 코드를 줄일 수 있다.

```swift
       func msgGenerator(message: String) -> (String) -> String {
       	return { (name) in
       		return message + name
       	}
       }
```

* 파라미터는 $0, $1 과 같이 대체 할 수 있다.

```swift
       func msgGenerator(message: String) -> (String) -> String {
       	return {
       		return message + $0
       	}
       }
```

* 클로저 내부의 코드가 한줄인 경우 return{} 블럭도 생략이 가능 하다.

```swift
       func msgGenerator(message: String) -> (String) -> String {
       	return message + $0
       }
```

* 클로저를 파라미터로 전달하는 것도 가능하다. 이때 파라미터는 `using block: 파라미터 타입 -> 리턴타입` 형태로 정의 된다.
* sort() 와 filter() 메서드의 경우 파라미터가 클로저인 형태 이다. sort() 가 아니라 `sort {    }` 로 원하는 정렬 알고리즘을 넣어 실행 결과를 조작할 수 있다.


#### 4.4 Extension
> 확장(_Extensions_)은 기존에 있는 클래스, 구조체, 열거형, 프로토콜 타입에 새로운 기능을 추가한다. 확장은 Objective-C에서의 카테고리(categories)와 유사하다(Objective-C 카테고리와 다르게, Swift 확장은 이름을 가지지 않는다). 쉽게 이미 정의된 타입에 새로운 속성이나 메서드를 추가할 수 있는 기능이라고 이해하면 된다.

Swift Extension이 할수 있는 것들:

* 계산 인스턴스 프로퍼티와 계산 타입 프로퍼티를 추가 할 수 있다.
* 인스턴스 메소드와 타입 메소드를 정의 할 수 있다
* 새로운 초기화를 제공 할 수 있다
* 서브스크립트를 정의 할 수 있다.
* 새로 중첩된 타입을 정의 하고 사용 할 수 있다.
* 기존 타입에 프로토콜을 적용 할 수 있다.

```swift
    extension String {
      var length: Int {
    	return self.characters.count
      }

      func reversed() -> String {
    	return self.characters.reversed().map { String($0) }.joined(separator: "")
      }
    }

    let str = "안녕하세요"
    str.length // 5
    str.reversed() // 요세하녕안
```
