# Ajax & Promise 

<hr/>
<br/>

## 목차

* [1. JQuery Ajax](#JQueryAjax)
* [2. 헬퍼함수](#헬퍼함수)
* [2. Promise 패턴](#Promise)

---

# JQueryAjax
## Ajax : Asynchronous Javascript And Xml
### XHR(XmlHttpRequest)객체이용
### XHR 객체를 이용한 요청 단위는 페이지가 아니라 데이터
- 자바스크립트 코드를 이용하여 XHR객체를 통해 HTTP서버와 데이터를 주고받음
- 브라우저 화면의 일부만 갱신할 수 있음
- 주로, 서버에 HTTP요청을 보낸뒤 XML,JSON,TEXT형식 등으로 응답을 받아 페이지의 일부만 변경

<br/>

### JQuery Ajax 규격
#### $.ajax()
- 제이쿼리에서 모든 Ajax() 메소드는 내부적으로는 $.ajax()메서드를 사용(기본메서드)
- $.ajax() 메서드는 사용자가 지정한 URL 경로에 파일의 데이터를 전송하고,  URL파일로부터
  요청한 데이터를 불러오는 기능을 수행
- 불러올 수 있는 외부 데이터로는 HTML, XML, JSON, TEXT유형 등이 있음

```swift
  $.ajax({
      url :  // 전송 페이지(액션 페이지)
      type : // 전송방식(get,post)
      data : // 전송할 데이터
      timeout : 응답 제한시간
      datatype : 요청한 데이터 타입(HTML,XML,JSON,TEXT등)
      async : //비동기 여부(default : true)
      success : function(data){    }     // 성공콜백함수, data : 서버의 반환값
      error : function(){  }    // 실패 콜백함수
      complete : // function(){   }     // 요청이 완료 되었을때 실행콜백함수  
  });
```
### JQuery Ajax 메서드
- $.get()    :  GET 방식의 ajax() 메서드
```swift
  $.get('index.html',function(data){
      $('#area').html(data);
  });
```
- $.post()    :  POST 방식의  ajax() 메서드
```swift
     $.post('index.html',function(data){
       $('#area').html(data);
     });
```
- $.getJSON()    : JSON 형식으로 응답받음
```swift
   $.getJSON('sample.json',function(data){
      $('#area').html('<p>'+data.age+'</p>');
   });
```
- load()    : 서버로부터 데이터를 받아서 일치하는 요소 안에 HTML을 추가
```swift
    $('#area').load('index.html',function(){    });
```
- $.getScript()   : 자바스크립트 형식으로 응답 받는 ajax()메서드
```swift
   $.getScript('sample.js',function(){});
```
- $.ajaxSetup()     : ajax() 메소드의 선택 사항들에 대한 기본값 설정
```swift
   $.ajaxSetup({url:'service.php'});
```
- ajaxStart()      :   첫 번째 Ajax요청이 시작될 때 호출되는 이벤트 메소드
```swift
    $('#img1').ajaxStart(function(){
        $(this).show();
    });
```
- ajaxStop()      :    모든 Ajax 요청이 끝날 때 호출되는 이벤트 메소드
```swift
    $('#img1').ajaxStop(function(){
        $(this).fadeOut(2000);
    });
```
- ajaxSend()      :    특정 Ajax 요청을 보내기 전에 호출되는 이벤트 메소드
```swift
    $('#msg').ajaxSend(function(event,request,settings){
        $(this).append("<p>"+settings.url+"페이지 요청 시작</p>");
    });
```
- ajaxSuccess()    :   특정 Ajax요청이 성공적으로 완료될 때마다 호출되는 이벤트 메소드
```swift
    $('#mgs').ajaxSucess(function(event,request,settings){
        $(this).append("<p>요청 성공</p>");
    });    
```
- ajaxError()      :    Ajax 요청들에 대한 오류 발생시 호출되는 메소드
```swift
   $('#mgs').ajaxError(function(event,request,settings){
       $(this).append("<p>"+settings.url+"페이지 요청 실패</p>");
   });
```
- ajaxComplete()      :   Ajax 요청들이 완료되면(성공/실패 관련 없이) 호출되는 이벤트 메소드
```swift
    $('#msg').ajaxComplete(function(event,request,settings){
        $(this).append("<p>요청완료</p>");
    });
```
# 헬퍼함수
> JQuery Ajax()함수의 기본 Content-Type은 "application/x-www-from-urlencoded"이다
  따라서 전송할 데이터는 QueryString형식(인코딩 폼 형식)으로 작성해야 한다.

> "application/x-www-from-urlencoded" 형식의 문자열을 직접 만드는 것은 비효율적

따라서 헬퍼함수가 나왔으며, 헬퍼함수는 사용자의 입력 값을 손쉽게 인코딩 폼 형식으로 변환

- $(form).serialize() : 폼 요소를 선택하고 호출했을때 입력 필드의 name특성(attribute)을 이용해 인코딩된 폼 데이터 생성
- $(form).serializeArray() :  폼 요소를 선택하고 호출했을때 입력 필드의 name특성(attribute)을 이용해 객체로 구성된 배열 생성
- $.param()     :  객체의 배열이나 객체를 파라미터로 전달하여 인코딩된 폼 데이터를 생성

# Promise
