---
layout: post
title: "[Ubuntu 18.04] postfix google stmp 설정 "
categories: jetsonnano
tag : []
---

### 1. postfix 설치
---
```
sudo apt-get update & sudo apt-get install mailutils
```

### 2. Postficx Configuration
---

Internet Site -> 호스트네임 -> ok 클릭

### 3. 구글 아이디 설정
---
아이디 정보가 들어있는 파일 생성 

```
vim /etc/postfix/sasl_passwd
```
내용 추가 
```
[smtp.gmail.com]:587 username@gmail.com:password
```
권한설정
```
chmod 600 /etc/postfix/sasl_passwd
```
파일 암호화
```
postmap /etc/postfix/sasl_passwd
```

### 4. /etc/postfix/main.cf 설정
파일 열기
```
vi /etc/postfix/main.cf
```
아래 설정 내용 변경 및 추가
```
relayhost = [smtp.gmail.com]:587
smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
```

### 5. postfix 재시작
```
systemctl restart postfix && systemctl enable postfix
```

### 6. 사용
```
mail -s "Test subject" 받는사람@이메일.com
```
![postfix_1](https://krispediadot.github.io/assets/images/postfix_1.jpg)
![postfix_2](https://krispediadot.github.io/assets/images/postfix_2.jpg)

<div class="divider"></div>

**[참고 자료]**

- [https://linuxscriptshub.com/configure-smtp-with-gmail-using-postfix/](https://linuxscriptshub.com/configure-smtp-with-gmail-using-postfix/)
- [https://tsy0668.tistory.com/11](https://tsy0668.tistory.com/11)
