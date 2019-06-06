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

## 7.미들웨어에서 send 메소드를 이용해봅시다.<br>

```js
// app4.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http');

// 익스프레스 객체 생성
var app = express();

// 미들웨어에서 응답 전송할 때 send 메소드 사용하여 JSON 데이터 전송
app.use(function(req, res, next) {
	console.log('첫번째 미들웨어에서 요청을 처리함.');
	
	res.send({name:'소녀시대', age:20});
});

// Express 서버 시작
http.createServer(app).listen(3000, function(){
  console.log('Express 서버가 3000번 포트에서 시작됨.');
});
```
**실행**<br>
![node app4.js](https://krispedia.github.io/assets/images/node_app4_js.jpg)<br>

**브라우저**<br>
![node app4 b.js](https://krispedia.github.io/assets/images/node_app4_js_b.jpg)<br>

## 8.미들웨어 응답시 redirect해서 google.com으로 이동해봅시다.<br>

```js
//app5.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http');

// 익스프레스 객체 생성
var app = express();

// 미들웨어에서 redirect 메소드 사용
app.use(function(req, res, next) {
	console.log('첫번째 미들웨어에서 요청을 처리함.');
	
	res.redirect('http://google.co.kr');
});

// Express 서버 시작
http.createServer(app).listen(3000, function(){
  console.log('Express 서버가 3000번 포트에서 시작됨.');
});
```
**실행**<br>
![node app5.js](https://krispedia.github.io/assets/images/node_app5_js.jpg)<br>

**브라우저**<br>
![node app5 b.js](https://krispedia.github.io/assets/images/node_app5_js_b.jpg)<br>

## 9.미들웨어로 요청값을 보내고 확인해봅시다.<br>

```js
// app6.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http');

// 익스프레스 객체 생성
var app = express();

// 미들웨어에서 헤더와 파라미터 확인
// 아래 코드에서 파라미터는 GET 요청에 대해서만 처리 가능함 (POST는 req.body 객체 참조)
app.use(function(req, res, next) {
	console.log('첫번째 미들웨어에서 요청을 처리함.');
	
	var userAgent = req.header('User-Agent');
	var paramName = req.query.name;
	
	res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
	res.write('<h1>Express 서버에서 응답한 결과입니다.</h1>');
	res.write('<div><p>User-Agent : ' + userAgent + '</p></div>');
	res.write('<div><p>Param name : ' + paramName + '</p></div>');
	res.end();
});

// Express 서버 시작
http.createServer(app).listen(3000, function(){
  console.log('Express 서버가 3000번 포트에서 시작됨.');
});
```
**실행**<br>
![node app6.js](https://krispedia.github.io/assets/images/node_app6_js.jpg)<br>

**브라우저**<br>
![node app6 b.js](https://krispedia.github.io/assets/images/node_app6_js_b.jpg)<br>

## 10.POST 방식으로 파라미터를 전달해 봅시다.<br>
```js
// app7.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , static = require('serve-static');

// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

app.use(static(path.join(__dirname, 'public')));

// 미들웨어에서 파라미터 확인
app.use(function(req, res, next) {
	console.log('첫번째 미들웨어에서 요청을 처리함.');

	var paramId = req.body.id || req.query.id;
	var paramPassword = req.body.password || req.query.password;
	
	res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
	res.write('<h1>Express 서버에서 응답한 결과입니다.</h1>');
	res.write('<div><p>Param id : ' + paramId + '</p></div>');
	res.write('<div><p>Param password : ' + paramPassword + '</p></div>');
	res.end();
});

// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on port ' + app.get('port'));
});

```

**실행**<br>
![node app7.js](https://krispedia.github.io/assets/images/node_app7_js.jpg)<br>

**브라우저**<br>
![node app7 1.js](https://krispedia.github.io/assets/images/node_app7_js_1.jpg)<br>
![node app7 2.js](https://krispedia.github.io/assets/images/node_app7_js_2.jpg)<br>

## 11.라우터 객체를 이용해 로그인 페이지 만들기<br>

```js
// app8.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , static = require('serve-static');

// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

app.use('/public', static(path.join(__dirname, 'public')));


// 라우터 객체 참조
var router = express.Router();

// 라우팅 함수 등록
router.route('/process/login').post(function(req, res) {
	console.log('/process/login 처리함.');

	var paramId = req.body.id || req.query.id;
	var paramPassword = req.body.password || req.query.password;
	
	res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
	res.write('<h1>Express 서버에서 응답한 결과입니다.</h1>');
	res.write('<div><p>Param id : ' + paramId + '</p></div>');
	res.write('<div><p>Param password : ' + paramPassword + '</p></div>');
	res.write("<br><br><a href='/public/login2.html'>로그인 페이지로 돌아가기</a>");
	res.end();
});

// 라우터 객체를 app 객체에 등록
app.use('/', router);


// 등록되지 않은 패스에 대해 페이지 오류 응답
app.all('*', function(req, res) {
	res.status(404).send('<h1>ERROR - 페이지를 찾을 수 없습니다.</h1>');
});


// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on port ' + app.get('port'));
});

```
**실행**<br>
![node app8.js](https://krispedia.github.io/assets/images/node_app8_js.jpg)<br>

**브라우저**<br>
![node app8 1.js](https://krispedia.github.io/assets/images/node_app8_js_1.jpg)<br>
![node app8 2.js](https://krispedia.github.io/assets/images/node_app8_js_2.jpg)<br>

## 12.코드를 조금 수정해 봅시다.<br>

```js
// app8_02.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , static = require('serve-static');

// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

app.use('/public', static(path.join(__dirname, 'public')));


// 라우터 사용하여 라우팅 함수 등록
var router = express.Router();

router.route('/process/login/:name').post(function(req, res) {
	console.log('/process/login/:name 처리함.');

    var paramName = req.params.name;
    
	var paramId = req.body.id || req.query.id;
	var paramPassword = req.body.password || req.query.password;
	
	res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
	res.write('<h1>Express 서버에서 응답한 결과입니다.</h1>');
    res.write('<div><p>Param name : ' + paramName + '</p></div>');
	res.write('<div><p>Param id : ' + paramId + '</p></div>');
	res.write('<div><p>Param password : ' + paramPassword + '</p></div>');
	res.write("<br><br><a href='/public/login3.html'>로그인 페이지로 돌아가기</a>");
	res.end();
});

app.use('/', router);


// 등록되지 않은 패스에 대해 페이지 오류 응답
app.all('*', function(req, res) {
	res.status(404).send('<h1>ERROR - 페이지를 찾을 수 없습니다.</h1>');
});


// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on port ' + app.get('port'));
});

```

**실행**<br>
![node app8 02.js](https://krispedia.github.io/assets/images/node_app802_js.jpg)<br>

**브라우저**<br>
![node app8 b.js](https://krispedia.github.io/assets/images/node_app802_js_1.jpg)<br>
![node app8 b.js](https://krispedia.github.io/assets/images/node_app802_js_2.jpg)<br>

## 13.이제 error를 처리해 봅시다.<br>

```js
// app9.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , static = require('serve-static')
  , errorHandler = require('errorhandler');

// 에러 핸들러 모듈 사용
var expressErrorHandler = require('express-error-handler');

// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

app.use('/public', static(path.join(__dirname, 'public')));

// 라우터 사용하여 라우팅 함수 등록
var router = express.Router();

router.route('/process/login').post(function(req, res) {
	console.log('/process/login 처리함.');

	var paramId = req.body.id || req.query.id;
	var paramPassword = req.body.password || req.query.password;
	
	res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
	res.write('<h1>Express 서버에서 응답한 결과입니다.</h1>');
	res.write('<div><p>Param id : ' + paramId + '</p></div>');
	res.write('<div><p>Param password : ' + paramPassword + '</p></div>');
	res.write("<br><br><a href='/public/login2.html'>로그인 페이지로 돌아가기</a>");
	res.end();
});

app.use('/', router);

// 등록되지 않은 패스에 대해 페이지 오류 응답
app.all('*', function(req, res) {
	res.status(404).send('<h1>ERROR - 페이지를 찾을 수 없습니다.</h1>');
});

// 404 에러 페이지 처리
var errorHandler = expressErrorHandler({
    static: {
      '404': './public/404.html'
    }
});

app.use( expressErrorHandler.httpError(404) );
app.use( errorHandler );

// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on port ' + app.get('port'));
});
```
**실행**<br>
![node app9.js](https://krispedia.github.io/assets/images/node_app9_js.jpg)<br>

**브라우저**<br>
![node app9 b.js](https://krispedia.github.io/assets/images/node_app9_js_b.jpg)<br>

## 14.URL을 param 객체로 확인해 봅시다.<br>
```js
// app10.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , static = require('serve-static');

// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

app.use('/public', static(path.join(__dirname, 'public')));

// 라우터 사용하여 라우팅 함수 등록
var router = express.Router();

router.route('/process/users/:id').get(function(req, res) {
	console.log('/process/users/:id 처리함.');

    // URL 파라미터 확인
	var paramId = req.params.id;
	
	console.log('/process/users와 토큰 %s를 이용해 처리함.', paramId);

	res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
	res.write('<h1>Express 서버에서 응답한 결과입니다.</h1>');
	res.write('<div><p>Param id : ' + paramId + '</p></div>');
	res.end();
});

app.use('/', router);

// 등록되지 않은 패스에 대해 페이지 오류 응답
app.all('*', function(req, res) {
	res.status(404).send('<h1>ERROR - 페이지를 찾을 수 없습니다.</h1>');
});

// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on port ' + app.get('port'));
});

```
**실행**<br>
![node app10.js](https://krispedia.github.io/assets/images/node_app10_js.jpg)<br>

**브라우저**<br>
![node app10 b 1.js](https://krispedia.github.io/assets/images/node_app10_js_b1.jpg)<br>
![node app10 b 2.js](https://krispedia.github.io/assets/images/node_app10_js_b2.jpg)<br>

## 15.coockie를 이용해봅시다!<br>
```js
// app11.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , cookieParser = require('cookie-parser')
  , static = require('serve-static')
  , errorHandler = require('errorhandler');

// 에러 핸들러 모듈 사용
var expressErrorHandler = require('express-error-handler');


// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

app.use('/public', static(path.join(__dirname, 'public')));

// cookie-parser 설정
app.use(cookieParser());


// 라우터 사용하여 라우팅 함수 등록
var router = express.Router();

router.route('/process/showCookie').get(function(req, res) {
	console.log('/process/showCookie 호출됨.');

	res.send(req.cookies);
});

router.route('/process/setUserCookie').get(function(req, res) {
	console.log('/process/setUserCookie 호출됨.');

	// 쿠키 설정
	res.cookie('user', {
		id: 'krispedia',
		name: '소녀시대',
		authorized: true
	});
	
	// redirect로 응답
	res.redirect('/process/showCookie');
});

app.use('/', router);


// 404 에러 페이지 처리
var errorHandler = expressErrorHandler({
    static: {
      '404': './public/404.html'
    }
});

app.use( expressErrorHandler.httpError(404) );
app.use( errorHandler );


// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on port ' + app.get('port'));
});
```
**실행**<br>
![node app11.js](https://krispedia.github.io/assets/images/node_app11_js.jpg)<br>

**브라우저**<br>
![node app11 b 1.js](https://krispedia.github.io/assets/images/node_app11_js_b1.jpg)<br>
![node app11 b 2.js](https://krispedia.github.io/assets/images/node_app11_js_b2.jpg)<br>

## 16.이번엔 session을 사용해서 여러 페이지를 만들어 봅시다.<br>
```js
//app12.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , cookieParser = require('cookie-parser')
  , static = require('serve-static')
  , errorHandler = require('errorhandler');

// 에러 핸들러 모듈 사용
var expressErrorHandler = require('express-error-handler');

// Session 미들웨어 불러오기
var expressSession = require('express-session');


// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

app.use('/public', static(path.join(__dirname, 'public')));

// cookie-parser 설정
app.use(cookieParser());

// 세션 설정
app.use(expressSession({
	secret:'my key',
	resave:true,
	saveUninitialized:true
}));


// 라우터 사용하여 라우팅 함수 등록
var router = express.Router();

// 로그인 라우팅 함수 - 로그인 후 세션 저장함
router.route('/process/login').post(function(req, res) {
	console.log('/process/login 호출됨.');

	var paramId = req.body.id || req.query.id;
	var paramPassword = req.body.password || req.query.password;
	
	if (req.session.user) {
		// 이미 로그인된 상태
		console.log('이미 로그인되어 상품 페이지로 이동합니다.');
		
		res.redirect('/public/product.html');
	} else {
		// 세션 저장
		req.session.user = {
			id: paramId,
			name: '소녀시대',
			authorized: true
		};
		
		res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
		res.write('<h1>로그인 성공</h1>');
		res.write('<div><p>Param id : ' + paramId + '</p></div>');
		res.write('<div><p>Param password : ' + paramPassword + '</p></div>');
		res.write("<br><br><a href='/process/product'>상품 페이지로 이동하기</a>");
		res.end();
	}
});

// 로그아웃 라우팅 함수 - 로그아웃 후 세션 삭제함
router.route('/process/logout').get(function(req, res) {
	console.log('/process/logout 호출됨.');
	
	if (req.session.user) {
		// 로그인된 상태
		console.log('로그아웃합니다.');
		
		req.session.destroy(function(err) {
			if (err) {throw err;}
			
			console.log('세션을 삭제하고 로그아웃되었습니다.');
			res.redirect('/public/login2.html');
		});
	} else {
		// 로그인 안된 상태
		console.log('아직 로그인되어있지 않습니다.');
		
		res.redirect('/public/login2.html');
	}
});

// 상품정보 라우팅 함수
router.route('/process/product').get(function(req, res) {
	console.log('/process/product 호출됨.');
	
	if (req.session.user) {
		res.redirect('/public/product.html');
	} else {
		res.redirect('/public/login2.html');
	}
});

app.use('/', router);


// 404 에러 페이지 처리
var errorHandler = expressErrorHandler({
    static: {
      '404': './public/404.html'
    }
});

app.use( expressErrorHandler.httpError(404) );
app.use( errorHandler );


// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on port ' + app.get('port'));
});
```
**실행**<br>
![node app12.js](https://krispedia.github.io/assets/images/node_app12_js.jpg)<br>

**브라우저**<br>
![node app12 b 1.js](https://krispedia.github.io/assets/images/node_app12_js_b1.jpg)<br>
![node app12 b 2.js](https://krispedia.github.io/assets/images/node_app12_js_b2.jpg)<br>
![node app12 b 3.js](https://krispedia.github.io/assets/images/node_app12_js_b3.jpg)<br>

## 17.파일 업로드를 해 봅시다.<br>
```js
// app13.js

// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , cookieParser = require('cookie-parser')
  , static = require('serve-static')
  , errorHandler = require('errorhandler');

// 에러 핸들러 모듈 사용
var expressErrorHandler = require('express-error-handler');

// Session 미들웨어 불러오기
var expressSession = require('express-session');

// 파일 업로드용 미들웨어
var multer = require('multer');
var fs = require('fs');

//클라이언트에서 ajax로 요청 시 CORS(다중 서버 접속) 지원
var cors = require('cors');


// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

// public 폴더와 uploads 폴더 오픈
app.use('/public', static(path.join(__dirname, 'public')));
app.use('/uploads', static(path.join(__dirname, 'uploads')));

// cookie-parser 설정
app.use(cookieParser());

// 세션 설정
app.use(expressSession({
	secret:'my key',
	resave:true,
	saveUninitialized:true
}));


//클라이언트에서 ajax로 요청 시 CORS(다중 서버 접속) 지원
app.use(cors());


//multer 미들웨어 사용 : 미들웨어 사용 순서 중요  body-parser -> multer -> router
// 파일 제한 : 10개, 1G
var storage = multer.diskStorage({
    destination: function (req, file, callback) {
        callback(null, 'uploads')
    },
    filename: function (req, file, callback) {
        callback(null, file.originalname + Date.now())
    }
});

var upload = multer({ 
    storage: storage,
    limits: {
		files: 10,
		fileSize: 1024 * 1024 * 1024
	}
});


// 라우터 사용하여 라우팅 함수 등록
var router = express.Router();

// 파일 업로드 라우팅 함수 - 로그인 후 세션 저장함
router.route('/process/photo').post(upload.array('photo', 1), function(req, res) {
	console.log('/process/photo 호출됨.');
	
	try {
		var files = req.files;
	
        console.dir('#===== 업로드된 첫번째 파일 정보 =====#')
        console.dir(req.files[0]);
        console.dir('#=====#')
        
		// 현재의 파일 정보를 저장할 변수 선언
		var originalname = '',
			filename = '',
			mimetype = '',
			size = 0;
		
		if (Array.isArray(files)) {   // 배열에 들어가 있는 경우 (설정에서 1개의 파일도 배열에 넣게 했음)
	        console.log("배열에 들어있는 파일 갯수 : %d", files.length);
	        
	        for (var index = 0; index < files.length; index++) {
	        	originalname = files[index].originalname;
	        	filename = files[index].filename;
	        	mimetype = files[index].mimetype;
	        	size = files[index].size;
	        }
	        
	    } else {   // 배열에 들어가 있지 않은 경우 (현재 설정에서는 해당 없음)
	        console.log("파일 갯수 : 1 ");
	        
	    	originalname = files[index].originalname;
	    	filename = files[index].name;
	    	mimetype = files[index].mimetype;
	    	size = files[index].size;
	    }
		
		console.log('현재 파일 정보 : ' + originalname + ', ' + filename + ', '
				+ mimetype + ', ' + size);
		
		// 클라이언트에 응답 전송
		res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
		res.write('<h3>파일 업로드 성공</h3>');
		res.write('<hr/>');
		res.write('<p>원본 파일명 : ' + originalname + ' -> 저장 파일명 : ' + filename + '</p>');
		res.write('<p>MIME TYPE : ' + mimetype + '</p>');
		res.write('<p>파일 크기 : ' + size + '</p>');
		res.end();
		
	} catch(err) {
		console.dir(err.stack);
	}	
		
});
 
app.use('/', router);


// 404 에러 페이지 처리
var errorHandler = expressErrorHandler({
    static: {
      '404': './public/404.html'
    }
});

app.use( expressErrorHandler.httpError(404) );
app.use( errorHandler );

// Express 서버 시작
http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on port ' + app.get('port'));
});
``` 
**실행**<br>
![node app13.js](https://krispedia.github.io/assets/images/node_app13_js.jpg)<br>

**브라우저**<br>
![node app13 b 1.js](https://krispedia.github.io/assets/images/node_app13_js_b1.jpg)<br>
![node app13 b 2.js](https://krispedia.github.io/assets/images/node_app13_js_b2.jpg)<br>
![node app13 b 3.js](https://krispedia.github.io/assets/images/node_app13_js_b3.jpg)<br>

## 18.이번엔 파일을 다운받아 봅시다.<br>
```js
// Express 기본 모듈 불러오기
var express = require('express')
  , http = require('http')
  , path = require('path');

// Express의 미들웨어 불러오기
var bodyParser = require('body-parser')
  , cookieParser = require('cookie-parser')
  , static = require('serve-static')
  , errorHandler = require('errorhandler');

// 에러 핸들러 모듈 사용
var expressErrorHandler = require('express-error-handler');

// Session 미들웨어 불러오기
var expressSession = require('express-session');

// 파일 업로드용 미들웨어
var multer = require('multer');
var fs = require('fs');

//클라이언트에서 ajax로 요청 시 CORS(다중 서버 접속) 지원
var cors = require('cors');

// mime 모듈
var mime = require('mime');


// 익스프레스 객체 생성
var app = express();

// 기본 속성 설정
app.set('port', process.env.PORT || 3000);

// body-parser를 이용해 application/x-www-form-urlencoded 파싱
app.use(bodyParser.urlencoded({ extended: false }))

// body-parser를 이용해 application/json 파싱
app.use(bodyParser.json())

// public 폴더와 uploads 폴더 오픈
app.use('/public', static(path.join(__dirname, 'public')));
app.use('/uploads', static(path.join(__dirname, 'uploads')));

// cookie-parser 설정
app.use(cookieParser());

// 세션 설정
app.use(expressSession({
	secret:'my key',
	resave:true,
	saveUninitialized:true
}));


//클라이언트에서 ajax로 요청 시 CORS(다중 서버 접속) 지원
app.use(cors());


//multer 미들웨어 사용 : 미들웨어 사용 순서 중요  body-parser -> multer -> router
// 파일 제한 : 10개, 1G
var storage = multer.diskStorage({
    destination: function (req, file, callback) {
        callback(null, 'uploads')
    },
    filename: function (req, file, callback) {
        callback(null, file.originalname + Date.now())
    }
});

var upload = multer({ 
    storage: storage,
    limits: {
		files: 10,
		fileSize: 1024 * 1024 * 1024
	}
});


// 라우터 사용하여 라우팅 함수 등록
var router = express.Router();


//파일 다운로드 패스에 대한 라우팅
router.route('/process/download').get(function(req, res) {
	console.log('/process/download 호출됨.');
	
	try {
		var paramFilepath = req.param('filepath');
		var filepath = __dirname + paramFilepath;
		var filename = path.basename(paramFilepath);
        var mimetype = mime.lookup(paramFilepath);
		
		console.log('파일 패스 : ' + filepath);
		console.log('파일 이름 : ' + filename);
		console.log('MIME 타입 : ' + mimetype);
		
		// 파일 크기 확인
		var stats = fs.statSync(filepath);
		var fileSize = stats["size"];
		console.log('파일 크기 : ' + fileSize);
		
		// 클라이언트에 응답 전송
		res.setHeader('Content-disposition', 'attachment; filename=' + filename);
	    res.setHeader('Content-type', mimetype);
	    res.setHeader('Content-Length', fileSize);
	  
	    var filestream = fs.createReadStream(filepath);
	    filestream.pipe(res);
	    
	} catch(err) {
		console.dir(err.stack);
		
		res.writeHead('400', {'Content-Type':'text/html;charset=utf8'});
		res.write('<h3>파일 다운로드 실패</h3>');
		res.end();
	}	
		
});



// 파일 업로드 라우팅 함수 - 로그인 후 세션 저장함
router.route('/process/photo').post(upload.array('photo', 1), function(req, res) {
	console.log('/process/photo 호출됨.');
	
	try {
		var files = req.files;
	
        console.dir('#===== 업로드된 첫번째 파일 정보 =====#')
        console.dir(req.files[0]);
        console.dir('#=====#')
        
		// 현재의 파일 정보를 저장할 변수 선언
		var originalname = '',
			filename = '',
			mimetype = '',
			size = 0;
		
		if (Array.isArray(files)) {   // 배열에 들어가 있는 경우 (설정에서 1개의 파일도 배열에 넣게 했음)
	        console.log("배열에 들어있는 파일 갯수 : %d", files.length);
	        
	        for (var index = 0; index < files.length; index++) {
	        	originalname = files[index].originalname;
	        	filename = files[index].filename;
	        	mimetype = files[index].mimetype;
	        	size = files[index].size;
	        }
	        
	    } else {   // 배열에 들어가 있지 않은 경우 (현재 설정에서는 해당 없음)
	        console.log("파일 갯수 : 1 ");
	        
	    	originalname = files[index].originalname;
	    	filename = files[index].name;
	    	mimetype = files[index].mimetype;
	    	size = files[index].size;
	    }
		
		console.log('현재 파일 정보 : ' + originalname + ', ' + filename + ', '
				+ mimetype + ', ' + size);
		
		// 클라이언트에 응답 전송
		res.writeHead('200', {'Content-Type':'text/html;charset=utf8'});
		res.write('<h3>파일 업로드 성공</h3>');
		res.write('<hr/>');
		res.write('<p>원본 파일명 : ' + originalname + ' -> 저장 파일명 : ' + filename + '</p>');
		res.write('<p>MIME TYPE : ' + mimetype + '</p>');
		res.write('<p>파일 크기 : ' + size + '</p>');
		res.end();
		
	} catch(err) {
		console.dir(err.stack);
	}	
		
});
 
app.use('/', router);


// 404 에러 페이지 처리
var errorHandler = expressErrorHandler({
    static: {
      '404': './public/404.html'
    }
});

app.use( expressErrorHandler.httpError(404) );
app.use( errorHandler );


// Express 서버 시작
var server = http.createServer(app).listen(app.get('port'), function(){
  console.log('Express server listening on %s, %s', server.address().address, server.address().port);
});

``` 

**실행**<br>
![node app14.js](https://krispedia.github.io/assets/images/node_app14_js.jpg)<br>

**브라우저**<br>
![node app14 b 1.js](https://krispedia.github.io/assets/images/node_app14_js_b1.jpg)<br>
![node app14 b 2.js](https://krispedia.github.io/assets/images/node_app14_js_b2.jpg)<br>
![node app14 b 3.js](https://krispedia.github.io/assets/images/node_app14_js_b3.jpg)<br>
