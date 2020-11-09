---
title: VSCode 확장프로그램 소개 - Terminal tabs
author: Roharui
date: 2020-11-09 19:16:00 +0800
categories: [Blogging, Tutorial]
tags: [vscode]
---

VSCode에서는 여러 기능을 제공합니다. 그중 대표적인 것이라고 한다면 아마 터미널을 여러개를 열수 있는 것일겁니다.

하지만 계속 사용하다보면 일일히 원하는 터미널을 선택해야하는 불편함이 있지요. 그래서 조금더 쉽게 사용할수 있는 확장프로그램을 찾다보니 이런게 있더군요.

## Terminal tabs

`터미널 탭스`. 이름 그대로 터미널을 탭처럼 사용할수 있는 확장입니다. 단순하지만 강력한 기능이죠.

실제 다운로드는 [여기](https://marketplace.visualstudio.com/items?itemName=Tyriar.terminal-tabs)에서 확인하시거나 `VSCode Extension`에서 terminal tabs를 검색하세요.

## 기능소개

설치 후 `Shift + p`를 눌러 명령 팔레트를 엽니다.

![터미널생성](/assets/img/vscode/create_terminal.png)

그럼 `Create Terminal`이 있을겁니다. 엔터를 누르면. 

![터미널탭](/assets/img/vscode/tabs.png)

하단 `Status bar`에 작은 아이콘이 생성 됩니다.

물론 여러 터미널을 생성하면 그만큼 아이콘이 생성됩니다.

![여러개의 터미널탭](/assets/img/vscode/four_tabs.png)

 아이콘들을 클릭해서 각각의 터미널을 바꿀수 있습니다. 하지만 사실 이 기능은 터미널이 몇개나 있나를 확인하는 용도로 쓰이지 실제로 클릭해서 바꾸는 경우는 거의 없습니다.

 단축키를 사용하면 더 편하게 탭을 바꿀수 있습니다. 하지만 `terminal tabs`는 기본 단축키를 제공하지 않기 때문에 일일히 설정해야합니다.

## 단축키 설정

 왼쪽 아래 설정버튼에서 `Keyboard Shortcuts`를 클릭합니다. 

![단축키설정](/assets/img/vscode/keyboard_shortcut.png)

단축키 설정에서 `terminal tabs`를 검색하시면 terminal tabs에서 제공하는 모든 단축키 설정을 볼수 있습니다.

![내단축키](/assets/img/vscode/mySetting.png)

저의 경우 터미널 생성은 `Ctrl + Shift + .`로, 터미널 전환은 `Ctrl + numpad1,2,3`을 사용하고 있습니다.

터미널 개수가 4개를 넘어가는 경우는 거의 없어서 3개만 사용하고 있지만 더 많이 사용하신다면 편하신대로 바꾸시면 됩니다.