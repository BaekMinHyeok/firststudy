node.js 강의 메모


1. 노드 설치 후 터미널

- node -v : 노드 버전확인
- ctrl + c 두번 : 빠져나가기

본격적으로 시작

npm 파일명 : 자바스크립트 파일을 Node.js의  V8 엔진으로 사용해서 이 코드를 해석
npm : npm 설치
Node Package Manager

express로 서버 열기
npm install express -s  =  npm install express --save : 처음에 넣는 명령어, 나증에 package.json에 설치한 모듈 관리가 쉬워짐
node_modules 폴더 안에 express폴더(express에 필요한 모든 파일 설치)가 설치가됨, 

그리고 서버가동이 나오면 작성했던 app.listen( 포트번호 , 를 localhost로 접속 후 Cannot GET / 확인

Cannot GET / 뒤에 루트경로를 지정해야함

http://localhost:3000
예를들어 app.get("/", (req, res) => {
	res.send("여기는 루트입니다")
});

브라우저 한테 응답과 요청을 하기위해서 req,res (request, response)
확인하려면 서버를 끄고 다시 실행 
실행중인 프로세스(서버) 종료는 ctrl + c

http://localhost:3000/login
app.get("/login", (req, res) => {
    res.send("여기는 로그인 화면입니다.");
});

-----------------------------------------------------
express를 안 쓰고 http를 이용해 서버 열기

const http = require("http");
const app = http.createServer((req, res) => {
    if (req.url === '/') {
        res.end("여기는 루트 입니다.");
    } else if (req.url === "/login") {
        res.end("여기는 로그인 화면 입니다.");
    }
});

app.listen(3001, () =>{
    console.log("http로 가동된 서버 입니다.")
})
하지만 서버를 열면 문자가 깨져서 따로 설정해줘야함


-----------------------------------------------------

ejs 추가 및 html 추가


app.js
//앱 세팅
app.set("views","./views");
app.set("view engine", "ejs");

app.get("/login", (req, res) => {
    res.render("home/login")  // 위에 views로 파일을 지정해서 경로가 views/home/login 
});

-----------------------------------------------------

routes로 더 쉽게 

app.js 에 
app.get("/login", (req, res) => {
    res.render("home/login")  // 위에 views로 파일을 지정해서 경로가 views/home/login 
});
 
이부분을 가져와서
routes/home/index.js 에 옮기기

자바스크립트 파일을 처음 만들때 
"use strict"; 
에크마스크립트를 명시하겠다는 표시


const express = require("express")
const router = express.Router(); //express에 router 불러오기

app 으로 표시했던 부분 router로 변경
router.get("/login", (req, res) => {
    res.render("home/login")  // 위에 views로 파일을 지정해서 경로가 views/home/login 
});

router를 외부로 사용할 수 있게 만들어줌 (연결을 하기위해서)
module.exports = router;


-----------------------------------------------------

package.json을 만들려면 

npm init : 패키지를 초기화 후 안에 내용을 설정 enter 누르면 기본값으로 진행 = npm ini -y ( yes 기본값으로 진행 )
-----------------------------------------------------
package.json

name: 모듈이름 , 예를 들어 npmjs.com 에 들어가서 express를 검색하면 나오는 이름
version: 배포되는 버전
description: 이 패키지 소프트웨어를 설명하는 텍스트(npmjs.com 사이트에서 검색)
main: 메인페이지
bin: 실행파일
dependencies: 의존하는 패키지 리스트
devDependencies: 개발할때만 필요한 패키지 리스트 ( 테스트도구 모듈,바벨,웹펙)?
scripts: 패키지에서 사용하고 싶은 명령어 ( 예를 들어 node 실행 서버 명령어를 지정
author: 만든사람
license: 프로젝트의 라이센스 ISC ,  MIT
homepage : 홈페이지가 있으면 추가


"ejs" : ^3.1.5  캐럿은 위에버전도 사용가능하게 표시 3버전까지만
~3.1.5 버전을 설치해달라
^3.1.x  x부분은 상관없이 사용가능하다
-----------------------------------------------------
깃에 올릴때
저장할때는 node_modules 대신에 package.json으로 대체해서 파일만 옮기고 
npm install을 하면 어디서나 동일하게 설치가능

powshell에서는 안됨
● nano 파일명 :  파일을 추가하고 내용도 추가가능
● nano .gitignore : 깃에 추가하면 안되는 파일들(node_modules) package.json으로 대체가능하기때문
추가로 하위폴더에 파일이 있으면 **표시로 

깃에서 .gitignore 파일로 들어가서 편집기에 왼쪽상단에 Choose .gitignore template버튼눌러서 Node 검색해서 누르면 알아서 노드에 업로드가 필요없는 파일들을 자동으로 등록해줌

insights - Community Standards - License - MIT -  create 하면 라이센스가 추가된다(License 파일도 추가됨)


-----------------------------------------------------

nodemon으로 서버 띄우기
sudo npm install nodemon -g : sudo 는 관리자 권환으로 설치 그냥 npm install nodemon -g 이걸로 해도됨

nodemon 서버경로 파일 : 서버가동 


m2 기본형 ram 16

