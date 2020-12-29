---
layout: post
title: "[MacOS] VS Code c++ 컴파일/디버깅 설정"
categories: 
tag : []
---

알고리즘 문제 풀이를 위해 가벼운 환경이 필요했고 <br>
기존에 사용하던 CLion을 VS Code로 대체하기 위해 설정이 필요했다.<br>

- 터미널 타이핑을 최소한으로 줄이기
- 단축키 설정
- Local & Global variable 디버깅으로 확인 가능

하도록 하는 것이 목표였고 이를 위한 방법은 다음과 같다.<br>

(VS Code는 설치되어 있다고 가정한다.)

### 1. C/C++ extension 설치 

extensions 에서 `C/C++` 검색 후 설치한다.<br> 

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_1.jpg)

### 2. CodeLLDB extension 설치 

extensions 에서 `CodeLLDB` 검색 후 설치한다.<br> 

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_2.jpg)

### 3. 코드를 작성할 폴더 생성

`testo`라는 이름의 폴더를 생성<br>

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_3.jpg)

### 4. 테스트용 cpp 파일 생성 

`test.cpp` 생성

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_4.jpg)

### 5. tasks.json 파일 생성

상단 버튼 중 Terminal -> Configure Tasks -> 컴파일러 선택

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_5.jpg)

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_6.jpg)

위 과정을 거치고 나면 tasks.json 파일이 생성된다.<br>

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_7.jpg)

### 6. tasks.json 파일 내용 변경

기본으로 생성되는 tasks.json 파일 내용은 아래와 같다.(선택한 컴파일러에 따라 다를 수 있음)<br>
```
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "cppbuild",
			"label": "C/C++: g++ build active file",
			"command": "/usr/bin/g++",
			"args": [
				"-g",
				"${file}",
				"-o",
				"${fileDirname}/${fileBasenameNoExtension}"
			],
			"options": {
				"cwd": "${workspaceFolder}"
			},
			"problemMatcher": [
				"$gcc"
			],
			"group": "build",
			"detail": "compiler: /usr/bin/g++"
		}
	]
}
```

파일의 내용을 원하는 바에 따라 아래와 같이 변경한다. <br>
```
{
	"version": "2.0.0",
	"tasks": [
        {
            "label": "build file",
            "type": "shell",
            "command": "/usr/bin/g++",
            "args": [
				"-g",
                "${file}",
                "-o",
				"${fileDirname}/${fileBasenameNoExtension}.out"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": [
                "$gcc"
            ]
        },
        {
            "label": "run file",
            "type": "shell",
            "command": "${fileDirname}/${fileBasenameNoExtension}.out",
            "args": [
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": [
				"$gcc"
			]
        },
    ]
}
```

파일을 저장하고 `command + shift + b` 단축키를 누르면 두가지 tasks를 선택할 수 있도록 리스트가 나온다.<br>

build -> run 순서로 사용하면 된다.<br>

### 7. tasks.json 파일 동작 확인 

#### build를 한 결과 
- test.out.dSYM 폴더가 생성<br>
- test.out 파일 생성<br> 

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_8.jpg)

#### run을 한 결과

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_9.jpg)

### 8. 디버깅을 위해 launch.json 파일 생성

상단 버튼 중 Run -> Start Debugging -> LLDB 선택

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_10.jpg)

버튼을 클릭하면 launch configuration이 제공되지 않는다는 오류 메세지가 나온다.<br>

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_11.jpg)

OK 버튼을 클릭하면 launch.json 파일이 생성된다.<br>

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_11.jpg)

### 9. launch.json 파일 내용 변경

기본으로 생성되는 launch.json 파일 내용은 아래와 같다.(선택한 환경에 따라 다를 수 있음)<br>
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "type": "lldb",
            "request": "launch",
            "name": "Debug",
            "program": "${workspaceFolder}/<your program>",
            "args": [],
            "cwd": "${workspaceFolder}"
        }
    ]
}
```

파일을 원하는 바에 따라 변경한다.<br>

```
{ 
    "version": "0.2.0", 
    "configurations": [ 
        { 
            "type": "lldb", 
            "request": "launch", 
            "name": "Launch", 
            "program": "${fileDirname}/${fileBasenameNoExtension}.out", 
            "args": [], 
            "preLaunchTask": "build file", 
            "stdio": [null,null,null], 
            "terminal": "integrated" 
        } 
    ] 
}
```

변경한 파일을 저장하고 상단 바의 Run -> Start Debugging을 시작하면 디버깅이 된다. <br>

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_12.gif)

breakpoint를 사용해서 디버깅을 할 수 있다.<br>

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_13.jpg)

![](https://krispediadot.github.io/assets/images/macos_vscode_c++_14.gif)

### 10. 알고리즘 문제풀이용 tasks.json & launch.json

알고리즘 문제를 풀다보면 input.txt를 받아 사용하는게 편할때가 있다. <br>

그때는 tasks.json과 launch.json을 다음과 같이 설정하면 된다.<br>

- tasks.json<br>
```
{
	"version": "2.0.0",
	"tasks": [
        {
            "label": "build file",
            "type": "shell",
            "command": "/usr/bin/g++",
            "args": [
				"-g",
                "${file}",
                "-o",
				"${fileDirname}/${fileBasenameNoExtension}.out"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": [
                "$gcc"
            ]
        },
        {
            "label": "run file",
            "type": "shell",
            "command": "${fileDirname}/${fileBasenameNoExtension}.out",
            "args": [
				"<",
				"${fileDirname}/input.txt",
				">",
				"${fileDirname}/output.txt"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": [
				"$gcc"
			]
        },
    ]
}
```

- launch.json<br>
```
{ 
    "version": "0.2.0", 
    "configurations": [ 
        { 
            "type": "lldb", 
            "request": "launch", 
            "name": "Launch", 
            "program": "${fileDirname}/${fileBasenameNoExtension}.out", 
            "args": [], 
            "preLaunchTask": "build file", 
            "stdio": ["${fileDirname}/input.txt",null,null], 
            "terminal": "integrated" 
        } 
    ] 
}
```

### 11. 단축키 설정 

사용하기 편리하도록 단축키를 설정하면 된다.<br>

- Start Debugging
- (Debugging)Step Over
- (Debugging)Step Into

등등 