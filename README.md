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

### 1. 자바스크립트 생성자는 객체 인스턴스를 생성하고 반환한다.
+ **생성자 함수의 역할** : 같은값과 동작을 공유하는 객체를 여러개 만드는것. => 생성자 함수는 새로 만든 객체(즉,this)를 반환한다.

```swift
  <script>
  
    // Array 객체의 인스턴스를 만들어 myArray에 저장한다.
    var myArray = new Array(); 
    
    console.log(typeof myArray); // Object가 기록된다?? =>  왜냐하면, 배열은 객체(Object)의 한 종류이다.
     
    console.log(myArray); // [] 기록
    
    console.log(myArray.constructor); // Array() 가 기록된다
    
  </script>
```
자바스크립트에서 대부분의 값(원시값은 제외)은 생성자 함수를 사용해 객체로 만들거나 인스턴스화 할 수있다.

<br/>

#### 자바스크립트에 포함된 네이티브(내장) 객체 생성자
 - Number()
 - String()
 - Boolean()
 - Object()
 - Array()
 - Function()
 - Date()
 - RegExp()
 - Error()


---
<hr/>

### 2. 리터럴을 사용한 값 생성하기 

자바스크립트에는 new 연산 방식말고 네이티브 객체값을 만들수 있는 "리터럴" 이라는 방식이 있다.

```swift
  <script>
    
    var myObject = new Object();
    var myOjbectLiteral = { }; // 리터럴
    
    var myArray = new Array('dong','joon');
    var myArrayLiteral = ['dong','joon'];  // 리터럴
    
    var myFunc = new Function("x","y","return x+y");
    var myFuncLiteral = function(x,y){return x+y}; // 리터럴
    
    var myRegExp = new RegExp('\bt[a-z]+\b');
    var myRegExpLiteral = /\bt[a-z]+\b/; // 리터럴
    
 </script>

```


# Swift : 이부분은 삭제 예정

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




