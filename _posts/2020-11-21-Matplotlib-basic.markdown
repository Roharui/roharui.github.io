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

주피터 노트북은 세가지 방식으로 사용할수 있습니다. 

하나는 `아나콘다`라고 하는 파이썬 모듈 관리 프로그램을 설치하는 방식.

또 하나는 `PIP`모듈을 이용하는 벙법이 있습니다.

남은 하나는 `Google`에서 제공하는 [Colab](https://colab.research.google.com/)을 사용하는 벙법입니다. 설치가 따로 필요없기에 전문가가 아니라면 코랩을 사용하는게 훨씬 간편합니다!

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

### Colab 사용하기

[Colab](https://colab.research.google.com/)에 접속합니다.

![Colab](/assets/img/jupyter/colab.png)

성공!

## 사용하기

> Colab은 Jupyter와는 차이점이 있습니다! Colab을 사용하시는 분이라면 참고용도로만 사용합시다!

![jupyter_elements](/assets/img/jupyter/jupyter_elements_small.png)

1. 누르면 이름을 바꿀수 있습니다.
2. 저장입니다. 수시로 눌러 줍시다.
3. 하단에 셀을 추가합니다.
4. 셀을 잘라냅니다. 삭제로 사용하셔도 됩니다.
5. 셀을 복사합니다.
6. 복사하거나 잘라낸 셀을 붙여넣습니다.
7. 위의 셀을 선택합니다.
8. 하단의 셀을 선택합니다.
9. 선택한 셀의 코드를 실행합니다.
10. 실행중인 코드를 중지시킵니다.
11. 커널을 재시작합니다. 주피터에 저장된 모든 데이터가 날라가니 주의합시다.
12. 모든 셀의 코드를 실행시킵니다.
13. 선택된 셀의 종류를 바꿀수 있습니다. (Code: 파이썬 코드, Markdown: 마크다운)

### 셀의 특징

![jupyter_cell_init](/assets/img/jupyter/jupyter_cell_init.png)

`In [1]` 이 표시는 첫번째로 실행된 셀이라는 소리입니다.

`Out [1]` 은 첫번째로 실행된 셀의 결과값입니다.

셀에서 생성된 모든 변수는 저장됩니다.

위의 셀에서 선언된 변수 `x`가 아래 셀에서도 호출되는 것을 볼수 있습니다.

그리고 셀은 중복 실행이 가능합니다.

![jupyter_cell_twice](/assets/img/jupyter/jupyter_cell_twice.png)

위에서 `x += 3`이 두번 실행되었기에 변수 `x`의 값이 7(1 + 3 + 3)이 되는 걸 보실수 있습니다.

만약 셀을 중복해서 실행했다면 당황하지 말고 커널을 재시작 합시다.

### 그래프 그리기

[Matplotlib](https://matplotlib.org/)을 이용하면 주피터 랩에서 손쉽게 그래프를 그릴수 있습니다.

![random_graph](/assets/img/jupyter/jupyter_random_graph.png)

`Matplotlib`에 대한 자세한 사항은 [공식사이트](https://matplotlib.org/)를 확인하거나 구글링을 합시다.

## 마무리

`Jupyter Notebook`은 데이터 분석에 가장 많이 사용되는 도구입니다.

자신이 데이터를 다루어야 한다면 한번쯤 사용해보는 것도 나쁘지 않을거에요. (당신이 코딩에 능숙하다는 전제하에)

`VSCode`에서도 `Jupyter Notebook`을 지원합니다! 

>최근에 `Jupyter`라는 VSCode 확장이 새로 나왔습니다. 관심있는 사람은 한번 설치해봅시다!