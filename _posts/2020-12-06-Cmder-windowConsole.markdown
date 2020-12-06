---
title: 멋진 콘솔 - cmder
author: Roharui
date: 2020-11-28 20:30:00 +0800
categories: [Blogging, Tutorial]
tags: [Windows]
---

예전부터 윈도우의 콘솔에는 불만이 많았습니다.

정확히는 MaxOS의 콘솔을 봤을때지만요.

왜냐면 멋이 없어요!

![console](/assets/img/cmder/cmd.png)

검은 줄에 하얀 글씨라니! 게다가 폰트도 그렇게 이쁘지가 않아요!

그래서 찾아보던 도중 제 미적 감각을 완벽하게 충족시켜줄 물건이 나왔습니다.

## CMDER

Cmder 윈도우용 콘솔 프로그램이지요.

기능은 여러가지 있지만 중요한건 그게 아닙니다. 이뻐요! 그것 만으로 모든 것이 충족되는 프로그램입니다.

![cmder](/assets/img/cmder/cmder.png)

물론 이쁜것 말고도 탭을 사용할수 있다던지 사용하지 않을때 불투명해진다든지 장점은 있습니다.

자세한건 여러분들이 사용하면서 알아내 보세요!

## 설치하기

> CMDER은 오픈소스 소프트웨어입니다! 깃 레포지토리는 [여기](https://github.com/cmderdev/cmder)에서 확인하세요!

[여기](https://cmder.net/)에 접속합니다.

![cmder.net](/assets/img/cmder/cmder_net.png)

다음과 같은 사이트에서 밑으로 내리면 다운로드 할수 있습니다.

![installcmder](/assets/img/cmder/cmder_download.png)

콘솔이 기본적으로 개발자들을 위한 것이다 보니 git포함버전이 따로 있습니다. 오른쪽이 깃포함 왼쪽이 미포함 버전입니다.

되도록이면 깃 포함버전을 다운로드 하시는게 편할거에요.

다운로드 하시면 다음과 같은 압축파일이 있을 겁니다. cmder은 따로 설치 프로그램이 없어요.

![다운로드](/assets/img/cmder/cmder_zip.png)

이 파일의 압축을 푸시고 원하는 위치에 둡시다. 저는 `C:\cmder`에 두었습니다. 그러는 편이 편해요!

이제 환경변수 설정을 합니다. 하지 않으셔도 되지만 하시는 편이 여러모로 편하실겁니다.

내 pc -> 속성 -> 고급 시스템 설정 -> 환경변수에 들어갑니다.

시스템 변수의 `Path`든 사용자 변수의 `Path`든 원하는 곳에 여러분이 cmder을 설치한 곳의 경로를 적어줍니다.

![환경변수](/assets/img/cmder/cmder_path.png)

이러시면 설치 완료입니다!

## 사용하기

시작 -> cmder을 검색하면 이제 바로 뜰겁니다.

대략적인 화면은 이렇습니다.

![cmder_screen](/assets/img/cmder/cmder_clear.png)

만약 git이 있으면 경로 뒤에 (master)가 표시됩니다. 변경사항이 있으면 노란색으로 바껴요

![cmder_git](/assets/img/cmder/cmder_git.png)

package.json이 있다면 이 모듈의 의존성 이름을 표시힙니다.

![cmder_npm](/assets/img/cmder/cmder_npm.png)

약간의 설정을 통해 VSCode에서도 사용할수 있어요!

![cmder_vscode](/assets/img/cmder/cmder_vscode.png)

## 마무리

이 포스트에서는 기능을 많이 소개하지는 않았지만 새탭 열기, 기록 검색 등 여러가지 편리한 기능들이 많습니다.

일반 콘솔보다는 약간 느리지만 그래도 기능성이나 디자인 측면에서는 일반 콘솔보다 월등하다고 생각해요.

ls, clear등 리눅스 명령어를 사용할수 있으니 리눅스에 익숙하신 분들이라면 꼭 사용하기는걸 추천드려요