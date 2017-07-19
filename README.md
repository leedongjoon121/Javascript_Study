# Javascript_Study
자바스크립트 핵심 기능 & 개념 정리 => 추후 응용 단계까지 업로드 예정

### name :  Dongjoonlee 
### nation : south korea
### date of birth : 1993.04.06
### univ : gachon university
### email : ehdwns46@naver.com

<hr/>
<br/>

## 목차

* [1. 자바스크립트 객체](#자바스크립트객체)
* [2. 자바스크립트 객체와 속성](#객체와속성)
* [3. Function 객체](#자바스크립트함수)
* [4. 자바스크립트에서 함수를 정의하는 세가지 방식 ★☆★☆](#중요1)
* [5. 자바스크립트에서 함수 호출하는 네가지 패턴 ★☆★☆](#중요2)
* [6. 자바스크립트 1급 객체 ★☆★☆](#중요3)



---

# 자바스크립트객체

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
보통은 리터럴 방식을 사용하면 new 연산자를 사용한 것과 동일한 효과를 볼수있으며 심지어 훨씬 편리함

<br/>
<br/>

# 객체와속성

### 1. 복합 객체에 다른객체 포함하기
Object(), Arrray(), Function() 객체는 다른 복합 객체를 포함할 수있다.

```swift
   <script>
   
      var object1 = {
             object2 : {
                object2_1 : {name:'dong'},
                object2_2 : {},
             },
             object3 : {
               object3_1 : {},
               object3_2 : {},
             }
      }; 
      
      console.log(object1.object2.object2_1.name); // 'dong' 이 기록됨
    </script>
```

### 2. 객체의 속성을 삭제 할 수있다.
delete연산자를 이용하면 객체에서 특정 속성을 완전히 제거할 수 있다.

```swift
  <script>
    var man = {name : 'dong'};
    delete man.name;
    console.log('dong' in man); // in : 해당 객체에 해당 속성이 있는지 검사, false가 찍힘
  </script>
```
★ 단, delete연산자는 프로토타입 체인에 있는속성을 제거 하지는 않는다!! 객체의 속성만 제거 ★

<br/><br/>

### ★☆★☆ 3. 프로토타입 체인 ★☆★☆
예를 들어 접근한 속성이 객체에 포함되어 있지 않으면 자바스크립트는 항상 프로토타입체인을 이용해 속성과 메서드를 찾는다


```swift
  <script>
    var myArray = ['lee','kim'];
    
    console.log(myArray.join()); // join :  배열을 구성하는 각 요소들을 하나의 문자열로 변환
      // join 메서드는 myArray의 메서드가 아닌데도 기능이 동작 => 프로토타입체인 동작
      // Array.prototype.join 으로 처리 되어 동작
      
    var myArray2 = ['dong','joon'];
    
    console.log(myArray2.toLocalString());  // 'dong,joon' 이기록됨
      // 1. toLocalString()는 myArray객체에서 정의 되어 있지않다.
      // 2. 따라서, Array.prototype에서 toLocalString()을 찾아본다 => 하지만 없다.
      // 3. 따라서, Object.prototype에서 toLocalString()을 찾아본다 => 존재한다.
      // 4. Object.prototype까지 올라가서 찾아보고 있으면 적용, 없으면 undifinded
  </script>
```
어떤 속성이 없는 객체에서 해당 속성을 찾으면, 자바스크립트는 이 값을 프로토타입 체인에서 찾는다
프로토타입 체인의 종점은 Object.prototype이다

<br/>

#### 따라서 모든 객체는 Object.prototype을 상속 받는다.

```swift
   <script>
    Object.prototype.dongjoon = 'handsome';
    
    var myString = 'kim';
    
    console.log(myString.dongjoon); // 'handsome'이 기록된다 => 
                                   // 프로토타입체인을 통해 Object.prototype.dongjoon 로 부터 가져왔다
   </script>

```

<br/>

# 자바스크립트함수


```swift
   <script>
    
    //생성자를 이용해 function 객체 할당
    var func1 = new Function('num1','num2','return num1+num2');
    console.log(func1(2,4)); // 6
    
    // 리터럴 방식을 이용해 function 객체 할당
    var func2 = function(num1,num2){return num1+num2 ;};
    console.log(func2(2,4); // 6
    
   </script>

```

# 중요1

<br/>

###  1.자바스크립트에서 함수를 정의하는 세가지 방식 ★☆★☆
자바스크립트 함수는 1.함수 생성자, 2.함수 선언문, 3.함수 표현식 세가지의 다른 방식으로 정의할 수 있다.

```swift
 <script>
 
   //1.  함수 표현식
    var myFunc = function(x,y){return x+y};
    console.log(myFunc(5,5)); // 10출력
   
   //2.  함수 생성자
    var myFunc2 = new Function('x','y','return x+y'); //마지막 매개변수는 로직부분
    console.log(myFunc2(7,8)); // 15출력
   
   //3.  함수 선언문
    function myFunc3(x,y){ return x+y };
    console.log(myFunc3(10,20)); // => 30출력
    
    //4.  apply() 와 call()패턴
    var myObject = {};
    
    function myFunc4(param1,param2){ 
      this.str1 = param1;
      this.str2 = param2;
      console.log(this); 
      //call() 또는 apply()를 통해 자바스크립트가 함수 스코프내에 설정한 this의 값을 재정의할 수있다.
     };
     
     myFunc4.apply(myObject, ['blue','green']); //배열안에 값을 넣어야함 : Object {str1:"blue",str2:"green"}가 기록됨 , 
   
     myFunc4.call(myObject,'lee','dong'); // Object {str1:"lee",str2:"dong"}가 기록됨
     
      // apply와 call의 차이점은 함수에 매개변수를 전달하는 방식뿐이다.
 </script>
```

<br/>

# 중요2

###  2.자바스크립트에서 함수 호출하는 네가지 패턴 ★☆★☆
자바스크립트 함수는 함수, 메서드, 생성자, apply() or call()을 이용하여 호출 가능

```swift
  <script>
  
   // 함수 패턴
    var myFunc = function(){return 'dongjoon'};
    console.log(myFunc()); // 'dongjoon' 이 출력
    
   // 메서드 패턴
    var myFunc2 = {
                    dongjoon : function(){return 'dj';}
                   };
    console.log(myFunc2.dongjoon()); // 'dj' 이 출력
   
   // 생성자 패턴
    var Human = function(name,age,tall){
      this.name = name;
      this.age = age;
      this.tall = tall;
    };
    var Djobj = new Human('dongjoon',25,185);
    console.log(Djobj.name, Djobj.age, Djobj.tall); // dongjoon 25 185 출력
   
    
  </script>
```

<br/>

# 중요3

###  3. 1급 객체 ★☆★☆
1급 객체는 4가지조건을 충족 해야한다.
- 1. 객체를 변수에 저장할 수 있어야 한다.
- 2. 객체의 인자로 넘길 수 있어야 한다.
- 3. 객체의 반환값을 사용할 수 있어야 한다.
- 4. 동적으로 프로퍼티를 생성 할 수 있어야 한다.

<br/>

#### 1. 객체를 변수에 저장할 수 있어야 한다.
```swift
 var a = function(){
   console.log("1.함수를 변수에 저장합니다.");
 }();
```

<br/>

#### 2. 객체의 인자로 넘길 수 있어야 한다.
```swift
 function func(){
   console.log("함수를 인자로 전달합니다.");
 };
 
 var b = function(parameter){
    parameter();
 }(func);
```

<br/>

#### 3. 객체의 반환값을 사용할 수 있어야 한다.
```swift
 function sum(a,b){
    return a+b;
 }
 console.log("3. 반환된 값이 나옵니다. 결과값 : "+sum(5,3));
```

<br/>

#### 4. 동적으로 프로퍼티를 생성 할 수 있어야 한다.
```swift
  var c = { };
  c.dongjoon = function(){
     console.log("4. 프로퍼티에 할당된 객체");
  };
  c.dongjoon();
```

<br/>



###  4. 익명 함수 ★☆★☆

###  5. 자기호출 표현식 ★☆★☆




