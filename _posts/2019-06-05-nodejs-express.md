---
layout: post
title: "[Node.js] express로 웹 서버 만들기"
comments: true
description: "Node.js"
tag : [Node.js]
---

#### Node.js express로 웹 서버를 만들어 봅시다.<br>

## 1. 먼저 Node.js를 설치합니다. <br>
아래 링크로 가서 Node.js를 다운 받습니다. (LTS / Current 둘 중 선택)<br>

[https://nodejs.org/en/](https://nodejs.org/en/)<br>

에디터가 필요하신 분들은 추가로 설치하시면 됩니다.<br>

제가 사용하고 있는 VS Code는 아래 링크에서 다운 받으실 수 있습니다.<br>

[https://code.visualstudio.com/download](https://code.visualstudio.com/download)<br>

## 2. 설치가 완료되었는지 확인해 봅시다.<br>

#### 1- 실습 폴더에 test.js 파일을 만들어 봅시다.<br>

```js
// test.js
console.log("hello");
```

#### 2- test.js 파일을 실행해 봅시다.<br>

![test.js](https://krispedia.github.io/assets/images/test_js.jpg)

console 객체를 이용해 콘솔창에 결과를 뿌려주었습니다. <br>
`console.log("hello");`<br>
`console.log('숫자: %d', 10);`<br>
`console.log('문자열: %s', 'hi!');`<br>
`console.log('JSON 객체: %j',{name: 'krispedia'});`<br>
등으로 콘솔에 결과를 보여줄 수 있습니다. <br>


Node.js 상에서 여러 모듈을 사용할 수 있습니다. <br>
노드 설치시 미리 제공되는 **내장모듈**,<br>
npm으로 필요시 설치할 수 있는 **외장모듈**이 있습니다. <br>

프로젝트 별 필요한 모듈 별 패키지을 한번에 설치 할 수 있도록 package.json파일로 관리할 수 있습니다.<br>

`npm install 패키지명 --save` 하면 package.json파일에 정보가 추가됩니다. <br>

이렇게 정리해둔 프로젝트를 복사해서 다른곳에서 사용할 경우 `npm install`명령어를 통해 package.json 파일에 정리된 패키지를 한번에 설치할 수 있습니다.<br>

## 3. 이번 포스트에 필요한 패키지를 package.json파일을 이용해 설치합시다.<br>

#### 1- 아래의 package.json 파일을 실습 폴더위치에 넣습니다.<br>

```json
// package.json
{
  "name": "Exmaple",  
  "version": "0.0.1",  
  "private": true,  
  "scripts": {  
    "start": "node app.js"  
  },  
  "dependencies": {  
    "body-parser": "^1.15.2",  
    "cookie-parser": "^1.4.3",  
    "cors": "^2.8.1",  
    "errorhandler": "^1.4.3",  
    "express": "^4.14.0",  
    "express-error-handler": "^1.1.0",  
    "express-session": "^1.14.1",  
    "fs": "0.0.1-security",  
    "mime": "^1.3.4",  
    "morgan": "^1.7.0",  
    "multer": "^1.2.0",  
    "pug": "^2.0.0-beta6",  
    "serve-favicon": "^2.3.0",  
    "serve-static": "^1.11.1"  
  }  
}
```
#### 2- 실습 폴더 내부에 들어가 `npm install`명령어를 실행합니다.<br>

![npm install](https://krispedia.github.io/assets/images/npm_install.jpg)

## 4. 간단한 익스프레스 샘플(app.js)을 만들어 봅시다.<br>

#### 1- app.js 파일을 생성한 후 `node app.js`로 실행합니다.

```js
// app.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http');
 
// 익스프레스 객체 생성
var app = express();

// 기본 포트를 app 객체에 속성으로 설정
app.set('port', process.env.PORT || 3000);

// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('익스프레스 서버를 시작했습니다 : ' + app.get('port'));
});
```

![app.js](https://krispedia.github.io/assets/images/app_js.jpg)

#### 2- 실행 후 브라우저를 열어 `http://localhost:3000/`를 확인합니다.<br>

실행 결과 **Cannot GET/** 만 뜹니다. <br>

![node app.js](https://krispedia.github.io/assets/images/node_app_js.jpg)<br>

app.js에서는 서버를 시작만 하도록 해 놓았기 때문에 어떠한 일도 하지 않습니다.<br>

## 5.미들웨어를 하나 추가해 결과창을 띄워봅시다.<br>

```js
// app2.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http');

// 익스프레스 객체 생성
var app = express();

// 직접 미들웨어 객체를 만들어 설정
app.use(function(req, res, next) {
	console.log('첫번째 미들웨어에서 요청을 처리함.');
	
	res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
	res.end('<h1>Express 서버에서 응답한 결과입니다.</h1>');

});

// Express 서버 시작
http.createServer(app).listen(3000, function(){
  console.log('Express 서버가 3000번 포트에서 시작됨.');
});
```
**실행**<br>
![node app2 c.js](https://krispedia.github.io/assets/images/node_app2_js_c.jpg)<br>

**브라우저**<br>
![node app2.js](https://krispedia.github.io/assets/images/node_app2_js.jpg)<br>

미들웨어에서 요청을 처리해줬습니다.<br>

## 6.미들웨어를 두개 추가해 봅시다.<br>

```js
// app3.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http');

// 익스프레스 객체 생성
var app = express();

// 첫번째 미들웨어에서 다음 미들웨어로 넘김
app.use(function(req, res, next) {
	console.log('첫번째 미들웨어에서 요청을 처리함.');
	
	req.user = 'mike';

	next();
});

// 두번째 미들웨어에서 응답 전송
app.use('/', function(req, res, next) {
	console.log('두번째 미들웨어에서 요청을 처리함.');
	
	res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
	res.end('<h1>Express 서버에서 ' + req.user + '가 응답한 결과입니다.</h1>');

});

// Express 서버 시작
http.createServer(app).listen(3000, function(){
  console.log('Express 서버가 3000번 포트에서 시작됨.');
});
```

**실행**<br>
![node app3.js](https://krispedia.github.io/assets/images/node_app3_js.jpg)<br>

**브라우저**<br>
![node app3 b.js](https://krispedia.github.io/assets/images/node_app3_js_b.jpg)<br>
