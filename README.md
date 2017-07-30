# Ajax

<hr/>
<br/>

## 목차

* [1. JQuery Ajax](#JQuery-Ajax)


---

# JQuery-Ajax
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

