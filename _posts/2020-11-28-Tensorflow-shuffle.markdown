---
title: 섞인 이미지 맞추는 인공지능 - Tensorflow
author: Roharui
date: 2020-11-09 19:16:00 +0800
categories: [Blogging, Develope]
tags: [Deep Learning]
---

> 이 포스트는 인공지능을 전문적으로 공부한 적이 없는 사람이 작성한 것입니다.
> 만약 이 포스트를 더 개선할 방법이 있다면 [깃헙](https://github.com/Roharui/FindShffledImage/issues)으로 문의해주세요.


제 4차 산업혁명 어쩌구 저쩌구... 는 그만합시다. 여러분들도 한번쯤은 지겹도록 들어봤을겁니다? 그쵸? 저만 그런건 아닐거에요?

인공지능입니다. 정확히 말하자면 `딥러닝`이라고 하는게 옳겠지요. 자세한 차이는 인터넷에서 찾아 보시고 바로 실전으로 갑시다.

## 기획

손글씨 구분이나 개, 고양이 구분은 안할겁니다. 기본적으로 너무 진부하잖아요?

그래서 기존에 있는 `cifar10` 데이터셋 이미지를 4조각으로 나누고 섞은 다음 인공지능 보고 찾게 시킬겁니다.

어려워 보이지만 조금의 응용만 한다면 의외로 쉽게 할수 있어요!

![원본-섞인_비교](/assets/img/shuffle/ori_shuffle.png)

## 데이터셋 모으기

위에서 보셨듯 데이터셋은 `cifar10`을 사용할겁니다. 이 데이터셋은 비행기, 사슴, 고양이, 개 등등 10 종류의 사진들을 나타냅니다. 

하지만 이 것들은 사실 쓸데가 없죠. 저희가 필요한 것은 섞인 사진, 그리고 어떤 순서로 섞었는지에 대한 정보입니다.

```python
(x_train_ori, _), (x_test_ori, _) = tf.keras.datasets.cifar10.load_data()
```

위의 코드는 `cifar10` 데이터 셋을 불러옵니다. 처음 실행하기는 분들은 다운받는데 시간이 걸릴거에요. (Tensorflow 필수)

```python
#이미지 4분할 하기
def slice(x): 
    return np.array([
        x[ 0:16,  0:16], 
        x[ 0:16, 16:32], 
        x[16:32,  0:16], 
        x[16:32, 16:32]
        ]
    )

#분할된 이미지 합치기
def together(x):
    [t1, t2, t3, t4] = x
    return np.concatenate(
        (np.concatenate((t1, t2), axis=1),
        np.concatenate((t3, t4), axis=1)), 
    axis=0)
```

`slice()` 함수는 들어온 사진을 4분할합니다. `together()`함수는 반대로 4개로 나뉜 이미지 배열을 하나의 이미지로 만듭니다.

```python
x_train = []
y_train = []

for i in x_train_ori:
    y = np.random.permutation(range(4))
    x = slice(i)
    x = x[y]
    x_train.append(together(x))
    y_train.append(y)
```

그럼 이제 모든 이미지를 뒤섞어야 겠죠. `np.random.permutation(range(4))`는 0부터 3까지의 숫자를 이리저리 뒤섞습니다.

![배열뒤섞기](/assets/img/shuffle/range_shuffle.png)

이렇게 뒤섞인 배열은 y가 됩니다. `x = x[y]`는 x를 y 대로 뒤섞고 하나의 이미지로 만들어 `x_train`에 넣이집니다. y는 `y_train`에 넣어지고요.

훈련세트를 전부 뒤섞었으니 코드를 조금 바꿔서 테스트 세트도 뒤섞어 줍니다.

```python
x_test = []
y_test = []

for i in x_test_ori:
    y = np.random.permutation(range(4))
    x = slice(i)
    x = x[y]
    x_test.append(together(x))
    y_test.append(y)
```

![랜덤데이터셋](/assets/img/shuffle/shuffled_img.png)

이제 데이터셋은 준비가 끝났습니다!

## 텐서플로우 모델 설계

딥러닝 학습에 가장 필수적인 데이터셋 수집에 성공했으니 이제 모델 설계가 필요합니다.

중요한 부분만 짧게 설명하고 넘어가겠습니다. 

```python
# Sequential 모델 선언
model = Sequential(name="Shuffle_Finder")

# 입력될 이미지 크기 입력
model.add(Input(shape=(32, 32, 3)))
# 컨볼루션 (합성곱) 레이어
model.add(Conv2D(32, (2, 2), padding='same', activation='relu'))
# 배치 정규화
model.add(BatchNormalization(-1))
model.add(Conv2D(16, (2, 2), padding='same', activation='relu'))
model.add(BatchNormalization(-1))
# 맥스풀 레이어 (이미지 크기 줄여줌)
model.add(MaxPool2D((2, 2)))
model.add(Conv2D(32, (2, 2), padding='same', activation='relu'))
model.add(BatchNormalization(-1))
model.add(Conv2D(16, (2, 2), padding='same', activation='relu'))
model.add(BatchNormalization(-1))
model.add(MaxPool2D((2, 2)))
model.add(Conv2D(32, (2, 2), padding='same', activation='relu'))
model.add(BatchNormalization(-1))
model.add(MaxPool2D((2, 2)))
# Flatten 레이어 (모든 데이터를 하나의 배열로 만듭니다)
model.add(Flatten())
# Dropout 레이어 (학습에 제외할 퍼셉트론을 선택합니다. 과적합을 줄여줍니다!)
model.add(Dropout(0.25))
# 밀집 레이어 (실제 학습의 핵심입니다!)
model.add(Dense(300))
model.add(Dropout(0.25))
model.add(Dense(100))
model.add(Dropout(0.25))
model.add(Dense(16))
# 크기 조정 레이어 (4 * 4의 데이터로 만듭니다.)
model.add(Reshape((4, 4)))
# Softmax 레이어 (중요!)
model.add(Softmax(axis=2))
```

![모델개요](/assets/img/shuffle/model_summary.png)

모델 설계는 이 정도입니다. 이제 `Softmax`레이어에 대해 설명하겠습니다.

### SoftMax

Softmax 레이어는 배열안에 있는 모든 값을 더했을때 1이 나오도록 만듭니다. 저희는 순서를 학습시켜야 하므로 살짝 복잡해집니다.

```python
# Softmax가 없을 경우 딥러닝 모델의 출력값입니다.
[ 0.26225463, -0.77424911,  2.34001811, -1.05016257],
[-1.79506395,  0.61382497,  2.04409541,  0.07119106],
[ 0.6591533 ,  0.58129702,  1.57090345, -1.01565791],
[ 0.00243039,  0.27532564,  0.85292896,  0.09001241]

#현재의 결과 값입니다.
[0,3,2,1]
```

딥러닝 출력값과 실제 결과값이 동일해야 학습이 진행됩니다. 하지만 `sparse_categorical_crossentropy`를 사용해서 이 문제를 해결할수 있습니다.

```python
#sparse_categorical_crossentropy는 결과값을
[0, 3, 2, 1]
#이런식으로 바꿔서 학습시켜 줍니다.
[
    [1., 0., 0., 0.],
    [0., 0., 0., 1.],
    [0., 0., 1., 0.],
    [0., 1., 0., 0.]
]
```

하지만 일반적인 Softmax는 한 열을 대상이 아닌 배열안의 모든 숫자를 대상으로 연산이 진행됩니다. 그렇기 때문에 `axis`를 매개변수로 사용합니다.

`axis = 0` 일 경우 모든 숫자를 대상으로 연상.

`axis = 1` 일 경우 행별로 연산.

`axis = 2` 일 경우 열별로 연산.

> 위의 설명은 정확하지는 않습니다! axis에 대한 설명은 다른 사이트를 참고해주세요.

### 모델 컴파일 및 학습

```python
model.compile(optimizer='adam', loss="sparse_categorical_crossentropy", metrics=['acc'],)
```

컴파일입니다. `adam` 옵티마이저를 사용했습니다. 손실함수로 `sparse_categorical_crossentropy`를 사용했습니다. 정확도를 표시해줍니다.

```python
checkpoint_filepath = '''
checkpoint/checkpoint-epoch-{epoch:02d}-loss-{loss:.2f}-trial.h5
'''
model_checkpoint_callback = tf.keras.callbacks.ModelCheckpoint(
    filepath=checkpoint_filepath,
    save_weights_only=True,
    monitor='loss',       # loss 값이 개선되었을때 호출됩니다
    verbose=1,            # 로그를 출력합니다
    save_best_only=True,  # 가장 best 값만 저장합니다
    mode='auto'           # auto는 알아서 best를 찾습니다. min/max
)
```

체크포인트입니다. 학습 중간중간 가중치를 저장합니다.

```
model.fit(x_train, y_train, batch_size=1000, epochs=20, callbacks=[model_checkpoint_callback])
```

학습 코드입니다. 배치사이즈 1000개, 20번 학습합니다.

## 학습 결과

```
Epoch 1/20
50/50 [==============================] - ETA: 0s - loss: 2.0857 - acc: 0.3226
Epoch 00001: loss improved from inf to 2.08567, saving model to 
checkpoint/checkpoint-epoch-01-loss-2.09-trial.h5

50/50 [==============================] - 109s 2s/step - loss: 2.0857 - acc: 0.3226
Epoch 2/20
50/50 [==============================] - ETA: 0s - loss: 1.3072 - acc: 0.4539
Epoch 00002: loss improved from 2.08567 to 1.30717, saving model to 
checkpoint/checkpoint-epoch-02-loss-1.31-trial.h5

.
.
.


Epoch 00020: loss improved from 0.63127 to 0.61734, saving model to 
checkpoint/checkpoint-epoch-20-loss-0.62-trial.h5

50/50 [==============================] - 109s 2s/step - loss: 0.6173 - acc: 0.7578
```

최종적으로 손실률 : `0.61`, 정확도 : `0.75`가 나왔네요.

## 테스트 결과

![결과](/assets/img/shuffle/model_test_result.png)