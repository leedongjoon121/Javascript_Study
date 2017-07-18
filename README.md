# Javascript_Study
자바스크립트를 공부하며, 잊지 말아야 할 내용들을 정리

**Index**

---

## 1. 자바스크립트 객체
자바스크립트에서는 거의 모든 것들이 객체이거나 객체처럼 동작한다.

```swift
  <script>
  
  var myObject = new Object();
  myObject['0'] = 'l';
  myObject['1'] = 'e';
  myObject['2'] = 'e';
  
  console.log(myObject); // Object {0="l", 1="e", 2 = "e"}가 기록된다
  
  var myString = new String('dongjoon');
  console.log(myString); // dongjoon {0="l", 1="e", 2 = "e"}가 기록된다
  </script>
```

myObject와 myString은 둘다 객체이다. 두객체 모두 속성을 가지고 있으며 속성을 상속하고 생성자
함수를 사용해 만들어졌다.

<br/>

사용자 정의 생성자 함수를 통해서도 객체를 만들수 있다.

```swift
 <script>
 
   var dong1 = new Object();
   dong1.living = true;
   dong1.age = 25;
   dong1.gender = 'male';
   dong1.getGender = function(){return dong1.gender;};
   console.log(dong1); // Object {living=true, age = 25, gender = "male" ...}객체가 기록된다.
   
   /* 아래에서도 동일한 객체가 만들어지지만 네이티브 Object()생성자가 아닌 사용자가
      정의한 생성자와 new연산자를 사용해 인스턴스로 만들수있다.
   */
   
   // 사용자가 정의한 생성자 포멧
   var Person = function(living,age,gender){
    this.living = living;
    this.age = age;
    this.gender = gender;
    this.getGender = function(){return this.gender;};
   }
   
   var dong2 = new Person(true,25,'male');
   
   console.log(dong2);
 </script>

```
사실 자바스크립트에 원래 포함된 네이티브 객체생성자는 굉장히 작으며, 이러한 객체 생성자는 세분화된 자료형(ex, 숫자,문자열,함수,객체,배열 등)값을
표현하는 복합 객체를 만들때 사용된다.

결국 객체를 어떻게 만들던 상관없이 최종 결과로는 결국 복합객체가 만들어진다.

<br/>

#### 2. 자바스크립트 생성자는 객체 인스턴스를 생성하고 반환한다.
+ **생성자 함수의 역할** : 같은값과 동작을 공유하는 객체를 여러개 만드는것.
++ **생성자 함수는 새로 만든 객체(즉,this)를 반환한다.**

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




