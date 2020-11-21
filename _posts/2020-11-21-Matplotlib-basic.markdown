---
title: Jupyter notebook 사용법
author: Roharui
date: 2020-11-15 16:25:00 +0800
categories: [Blogging, Tutorial]
tags: [Deep Learning]
---

데이터 시각화 작업이나 인공지능 학습 등 데이터 처리에 관련된 작업을 할때면 코딩이 굉장히 비효율적이게 됩니다.

왜냐하면 프로그램이 실행되고 난 후에 데이터를 컴퓨터가 저장하지 않기 때문이죠.

게다가 그래프를 수정해야 할때 사진으로 저장하지 않는한 컴퓨터는 그래프를 저장해 두지 않습니다.

전 세계 수많은 개발자들이 이런 불편함을 감수했을까요?

당연히 아니죠! 소개합니다. `Jupyter Notebook`

## 개요 

`Jupyter Notebook`은 파이썬 모듈이자 IDE의 일종입니다.

정확히 말하자면 모듈형식으로 다운로드 할수 있는 IDE라고 하는게 정확할 거에요.

![jupyter](/assets/img/jupyter/jupyter_notebook.png)

이렇게 생겼습니다. 눈치채신 분들도 있겠지만 주피터 노트북은 브라우저 상에서 작동합니다.

실행된 주피터 서버가 저희가 전송한 코드들을 즉시 실행시킨후 값을 보여줍니다.

![jupyter_cell](/assets/img/jupyter/jupyter_cell.png)

이런식으로요. 이런 코드칸 하나하나를 전부 `Cell`이라고 합니다.

주피터는 저희가 저장한 변수들을 전부 저장하고 있고 `Cell`을 실행시킬때 결과값을 전부 보여주기에 

데이터 시각화, 인공지능 학습등에 가장 적합하다고 할수 있지요.

## 설치하기

주피터 노트북은 두가지 방식으로 사용할수 있습니다. 

하나는 `아나콘다`라고 하는 파이썬 모듈 관리 프로그램을 설치하는 방식.

또 하나는 `PIP`모듈을 이용하는 벙법이 있습니다.

되도록이면 첫번째 방식을 사용합시다. 설치가 간편한건 둘째로 `아나콘다`는 굉장하거든요!

### 아나콘다로 설치하기

[여기](https://www.anaconda.com/products/individual#download-section)로 들어가서 아나콘다를 설치합니다.

![ananconda](/assets/img/jupyter/anaconda.png)

버전에 맞게 설치하시면 끝입니다.

왜냐! 아나콘다를 설치하면 `Jupyter Notebook`은 자동으로 설치가 되거든요.

![notebook](/assets/img/jupyter/window_jupyter.png)

설치가 완료됬다면 시작 -> jupyter 검색하시면 프로그램이 나옵니다. 그걸 실행하면 되요.

### PIP모듈으로 설치하기

콘솔을 열고 다음 명령어를 입력합니다.

> 파이썬 설치는 필수입니다!

```
pip install notebook
```

이러면 마찬가지로 설치는 끝입니다. 실행은

```
jupyter notebook
```

입력하시면 됩니다.

## 사용하기

> 추가예정