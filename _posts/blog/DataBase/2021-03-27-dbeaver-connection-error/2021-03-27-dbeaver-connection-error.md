---
layout: post
title: DBeaver | MySQLdb 오류 
date: 2021-03-27 01:45:00 +09:00
modified: 
category: database
tags: [MySQL]
image: "/assets/img/mysql_logo.png"
cover: ""
---

### 1. 오류 내용
```
Access denied for user 'root'@'172.17.0.1' (using password: NO) Current charset is UTF-8. If password has been set using other charset, consider using option 'passwordCharacterEncoding'
```

### 2. 해결 방법
<br>
db에서 아래 사항을 추가해주면 된다.<br>
<br>
```sql
ALTER USER '사용자이름'@'%' IDENTIFIED WITH mysql_native_password BY '비밀번호';
```