---
title: VSCode C/C++ undefined reference to 에러 해결
author: Roharui
date: 2021-02-15 20:30:00 +0800
categories: [Blogging, Tutorial]
tags: [C++]
---

## 원인

VSCode에서 헤더피일을 인식하지 못해서 생기는 문제. 

빌드작업 실행시 명령어가 `g++ -g main.cpp -o main` 이렇게 되어있다면 헤더파일을 인식하지 못함.
`g++ -g main.cpp <헤더파일용 cpp> -o main`을 넣어주면 성공적으로 빌드 할수 있다.

## 해결 방법

> 리눅스 전용입니다.

간단히 다음 문자열을 `.vscode` 안의 `task.json`에 넣어주면 된다. (없으면 만들자)

```
{
    "tasks": [
        {
            "type": "shell",
            "label": "g++ build active file",
            "command": "/usr/bin/g++",
            "args": [
                "-g",
                "<main이 있는 cpp 위치>", // 중요!
                "<헤더파일 위치>", // 중요!
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}"
            ],
            "options": {
                "cwd": "/usr/bin"
            },
            "problemMatcher": [],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ],
    "version": "2.0.0"
}
```

헤더파일 위치와 main cpp 위치를 잘 확인하도록 하자.

## 실행하기

`Ctrl + Shift + B`로 바로 빌드를 할수 있다. 다음 파일이 선택되지 않는다면 `터미널 -> 작업 실행` 에서 직접 선택후 실행하면 잘 빌드 되는 것을 확인할수 있다.