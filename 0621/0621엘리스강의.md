06/21


##Middleware란?
미들웨어는 Express.js 동작의 핵심
HTTP 요청과 응답 사이에서 단계별 동작을 수행해주는 함수

##middleware 작성법
req, res, next를 가진 함수를 작성하면 해당 함수는 미들웨어로 동작할 수 있음
✓  req는 HTTP 요청을 처리하는 객체
✓  res는 HTTP 응답을 처리하는 객체
✓  next는 다음 미들웨어를 실행하는 함수

Route Handler도 미들웨어의 한 종류
Route Handle는 라우팅 함수(get, post, put, delete 등)에 적용된 미들웨어
일반적인 미들웨어와는 다르게 path parameter를 사용할 수 있음

next() 함수가 호출되지 않으면
미들웨어 사이클이 멈추기 때문에 주의

##middleware 사용법 - 어플리케이션 미들웨어  app.
-use 나 http method 함수를 사용하여 미들웨어를 연결할 수 있음
-HTTP 요청이 들어온 순간부터 적용된 순서대로 동작 함

##middleware 사용법 - 라우터 미들웨어  router.
-router 객체에 미들웨어가 적용되는 것 외에는 어플리케이션 미들웨어와 사용 방법은 동일
-특정 경로의 라우팅에만 미들웨어를 적용하기 위한 방법
-app 객체에 라우터가 적용된 이후로 순서대로 동작함

##middleware 사용법 - 미들웨어 서브 스택 middleware sub-stack
-use 나 http method 함수에 여러 개의 미들웨어를 동시에 적용할 수 있음
-주로 한 개의 경로에 특정해서 미들웨어를 적용하기 위해 사용
-전달된 인자의 순서 순으로 동작

##오류처리 미들웨어  error handling middleware
오류처리 미들웨어는 일반적으로 가장 마지막에 위치하는 미들웨어 
다른 미들웨어들과는 달리 err, req, res, next 네 가지 인자를 가지며, 
앞선 미들웨어에서 next 함수에 인자가 전달되면 실행됨

##함수형 middleware
하나의 미들웨어를 작성하고, 작동 모드를 선택하면서 사용하고 싶을 경우 
미들웨어를 함수형으로 작성하여 사용할 수 있음
Ex) API별로 사용자의 권한을 다르게 제한하고 싶은 경우

##REST API란?
REST 아키텍처를 준수하는 웹 API RESTful API라고 부르기도 함

##REST API 기본 가이드 - HTTP Method의 사용
REST API는 API의 동작을 HTTP method + 명사형 URL로 표현함 
/posts 라는 URL은 '게시글'이라는 자원을 가리킨다고 할 때,
GET- 가져오기, POST - 새로 만들기, PUT - 수정하기, DELETE - 삭제하기 의 
HTTP method와 결합하여 API 동작을 정의하여야 함

##REST API 정리
REST API는 REST 아키텍처를 준수하는 웹 API를 의미하며,
URL을 통한 자원의 표현 방법과, HTTP method를 통한 API 동작의 정의 정도만 
사용해도 훌륭한 REST API를 구현할 수 있음

##JSON 이란?
JavaScript Object Notation
자바스크립트에서 객체를 표현하는 표현식으로 시작함 
데이터를 표현하는 방법이 단순하고 이해하기 쉬워서 
웹 API에서 데이터를 전송할 때 표현식으로 주로 사용됨

##JSON을 사용하는 이유
웹 API는 기본적으로 데이터를 문자열로 전송하게 됨
어떤 객체를 웹 API를 통해서 문자열로 전달하기 위해 JSON을 사용함

##JSON 가이드 - Object
JSON에서 Object는 { key: value }로 표현함
value에는 어떤 값이라도 사용될 수 있음 (문자열, 숫자, JSON 객체 등) 
Ex) {"name": 'elice', "age": 5, "nationality": 'korea' }

##JSON 가이드 - Array
JSON에서 Array는 [item1, item2] 로 표현함
item에는 어떤 값이라도 사용될 수 있음 (문자열, 숫자, JSON 객체 등) 
Ex) ['first', 10, { name: 'bob' }]

##MVC 패턴
MVC 패턴은 웹 서비스의 가장 대표적인 프로젝트 구성 패턴으로
프로젝트의 기능들을 어떻게 분리할지에 대한 하나의 구성 방법 
Model - View - Controller를 구분하여 프로젝트 구조를 구성하는 것

##MVC 패턴 - Model
Model은 데이터에 접근하는 기능 또는 데이터 그 자체를 의미함 
데이터의 읽기, 쓰기는 Model을 통해서만 이루어지도록 구성해야 함

##MVC 패턴 - View
View는 데이터를 표현하는 기능을 의미함
주로 Controller에 의해 데이터를 전달받고 
전달받은 데이터를 화면에 표시해주는 기능을 담당

##MVC 패턴 - Controller
Controller는 Model을 통해 데이터에 접근하여, 
처리 결과를 View로 전달하는 기능을 의미함 
웹 서비스에선 주로 라우팅 함수가 해당 기능을 수행함


##Postman
Postman은 API를 테스트할 수 있는 도구로,
HTTP 요청을 손쉽게 작성하여 테스트해 볼 수 있게 도움 
추가로 API를 문서화 할 수 있는 기능 및 다양한 도구를 제공함

##Postman으로 API 문서화하기
✓  collection 만들기
✓ api request 만들기
✓ document 작성하기
✓  전체 문서 확인하기

##Postman으로 API 테스트하기
✓ HTTP Method 설정하기
✓ query param 사용하기
✓ path variable 사용하기
✓  body 사용하기