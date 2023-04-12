---
layout: post
title: C++ | Windows Offline 환경에서 사용하기
date: 2023-04-12 17:00:00 +09:00
modified: 
category: cpp
tags: [install]
image: "/assets/img/cpp_logo.jpeg"
cover: ""
---

### 1. MinGW-w64 설치하기

g++/ gcc가 설치되지 않았다면  공식홈페이지에 들어가서 MinGW-w64를 다운받는다.<br>
(다른 대안을 선택해도 된다.)

다운받은 폴더의 압축을 아래 경로에 풀어준다.<br>
사용하는 시스템에 따라 다른 경로를 지정해야할 수 있다.<br>

>C:\Program Files\mingw64

### 2. 환경변수 설정

>설정 > 시스템 > 정보 > 고급시스템설정 > 환경변수

환경변수 설정은 사용자 환경변수 vs 시스템 환경변수 두가지 종류가 있는데<br>

사용자 환경변수에 설정해두었다. 

>사용자명 환경변수 > Path 편집 > 새로 만들기

위 버튼을 클릭하고 방금 설치한 mingw64 폴더 아래 g++.exe/ gcc.exe가 있는 위치를 걸어준다.<br>

### 3. CMD 에서 g++/gcc 설치 확인

아래 명령어를 입력해 제대로 설치 및 경로가 잡혔는지 확인한다.<br>

```
g++ -v
gcc -v 
```

### 4. VSCode에서 C++ 사용

##### 1) C++ extentions 설치

기본적으로 아래 3개를 설치한다.<br>

- C/C++
- C/C++ Extension Pack
- C/C++ Themes

Offline 환경에서는 extentions를 바로 다운받을 수 없기 때문에 Online 환경에서 VSIX 파일을 사용해 설치한다.<br>

##### 2) 빌드 및 실행 작업 정의

VSCode를 통해 C++ 파일을 실행하기 위에 Object 파일을 만들고 실행파일을 생성하는 작업을 정의해줘야한다.<br>

.vscode 폴더 아래에 아래 3가지 json 파일을 생성해주면 된다.<br>

1. c_cpp_properties.json
```json
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "_UNICODE"
            ],
            "compilerPath": "C:\\Program Files\\mingw64\\bin\\g++.exe",
            "cStandard": "c17",
            "cppStandard": "gnu++14",
            "intelliSenseMode": "windows-gcc-x64"
        }
    ],
    "version": 4
}
```
2. launch.json
```json
{
    "configurations": [
        {
            "name": "C/C++: g++.exe 활성 파일 빌드 및 디버그",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "C:\\Program Files\\mingw64\\bin\\gdb.exe",
            "setupCommands": [
                {
                    "description": "gdb에 자동 서식 지정 사용",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                },
                {
                    "description": "디스어셈블리 버전을 Intel(으)로 설정",
                    "text": "-gdb-set disassembly-flavor intel",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "C/C++: g++.exe 활성 파일 빌드"
        }
    ],
    "version": "2.0.0"
}
```
3. tasks.json
```json
{
    "tasks": [
        {
            "type": "cppbuild",
            "label": "C/C++: g++.exe 활성 파일 빌드",
            "command": "C:\\Program Files\\mingw64\\bin\\g++.exe",
            "args": [
                "-fdiagnostics-color=always",
                "-g",
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": "build",
            "detail": "디버거에서 생성된 작업입니다."
        }
    ],
    "version": "2.0.0"
}
```

##### 3) 단축키 지정

조금 더 편하게 cpp 파일을 실행하기 위해 VSCode 환경설정에서 단축키를 지정하면 된다.<br>

> File > Preferences > Keyboard Shorcuts
