## # simple-CNN README <br>
FashionMNIST 데이터를 활용한 간단한 CNN 학습(1개의 컨볼루션 레이어와 1개의 풀링레이어 포함)
1. 결과 요약
2. 요구사항
3. 결과

<br>

## 1. 결과 요약
- 가장 예측을 잘 한 종류는 `Sandal` 로 `98%` 맞게 예측
- 가장 예측을 잘 못한 종류는 `shirt` 로 `74%` 맞게 예측

![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/1f5e489b-a693-476a-ab84-bc9170d4f3a3)
<br><br>

- 가장 잘못 예측한 종류인 Shirt의 결과 그래프
- 결과를 통해 Shirt를 `36%`만큼 `T-Shirt/top`로 예측했다는 것을 알 수 있음

![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/efe3abd7-ffad-4329-b54e-fccce1f06158)
<br><br>

<br>

## 2. 요구사항

**[주제]**<br>
- 컴퓨터 비전 문제

<br>

**[목표]**<br>
- 간단한 컨볼루션 신경망(CNN)을 사용하여 이미지 분류 작업을 수행합니다.

<br>

**[데이터셋]**<br>
- Fashion-MNIST는 의류와 관련된 이미지로 구성된 데이터셋으로, 각 이미지는 28x28 픽셀의 그레이스케일 이미지입니다.
- 데이터셋에는 10개의 클래스가 있으며, 각 클래스는 다른 유형의 패션 아이템(예: 티셔츠, 바지, 풀오버, 드레스 등)을 나타냅니다.

<br>

**[주어진 데이터 분석]**<br>
- 축소한 Fashion-MNIST 데이터셋을 로드합니다.
- t10k-images-idx3-ubyte.gz은 10,000개의 images 입니다.
- t10k-labels-idx1-ubyte.gz은 10,000개의 labels 입니다.
- 축소한 Fashion-MNIST 데이터셋을 로드하고, 훈련 데이터와 테스트 데이터로 나눕니다.
- 이미지 데이터의 형태와 클래스 레이블을 시각적으로 탐색하고 분석합니다.

<br>

**[모델 구축 및 훈련]**<br>
- 간단한 CNN 모델을 구축합니다. 모델은 적어도 한 개의 컨볼루션 레이어와 풀링 레이어를 포함해야 합니다.
- 모델을 컴파일하고, 적절한 손실 함수와 최적화 알고리즘을 선택합니다.
- 훈련 데이터를 사용하여 모델을 훈련시키고, 훈련 과정에서의 손실과 정확도를 모니터링합니다.

<br>

**[모델 평가 및 결과 분석]**<br>
- 테스트 데이터셋을 사용하여 모델을 평가하고, 최종 정확도를 보고합니다.
- 잘못 분류된 이미지들을 분석하고, 어떤 클래스가 모델에 의해 가장 잘못 분류되었는지를 식별합니다.

<br><br>

## 3. 결과

**[데이터]**<br>
- `Train` / `Valid` / `Test` 데이터로 분할 및 데이터 개수 확인 <br><br>
![데이터 개수 확인](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/935a1be9-b70b-4abc-9463-3888e4d7a57a)

- `9개의 인덱스` 확인 <br>
<img width="1011" alt="image" src="https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/b9f89842-c9a2-4a19-b724-311d7caf3028">
 <br><br>
 
- 인덱스별 sample 데이터 확인 <br><br>
![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/5180f47f-e616-44fe-8381-24f87cd9287e)
 <br><br>

 - 데이터 종류별 개수 확인 <br><br>
![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/77360b93-cde3-449d-a148-f31e80d45440)
 <br><br>

**[CNN 모델]**<br>
- 1개의 `컨볼루션 레이어`와 1개의 `풀링 레이어`를 사용
- `Conv2d` 함수를 통해 컨볼루션 레이어를 생성
- `MaxPool2d` 함수를 통해 풀링 레이어를 생성
- `Flatten` 함수를 통해 1차원 행렬로 변경
- `Linear` 함수를 통해 전결합층 레이어로 넣음
- `forward(순전파)` 함수에서 Conv2d -> relu -> MaxPool2d -> flatten -> Linear -> log_softmax 의 과정을 거침
  
&nbsp;&nbsp;&nbsp;&nbsp;![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/3f87b349-0154-4df8-bda3-3cfedb26b0d0)
 <br><br>

**[학습]**<br>
- 학습은 `epoch` 을 10으로 하여 진행
- 학습은 `train_data` 를 사용하고, 평가는 `valid_data` 를 사용
- `Acc` 는 높아지고, `Loss` 는 낮아지는 것을 볼 수 있음

![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/23a63a00-b481-4f67-8fdd-bb37ccd7073f)

 <br><br>

 **[최종 평가]**<br>
- `Loss` 값과 `Acc` 를 계산
- 결과를 통해 정확도가 `88%` 로 높게 나온 것을 볼 수 있음

&nbsp;&nbsp;&nbsp;&nbsp;<img width="202" alt="image" src="https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/f87ec582-1f70-461a-9cf7-554848fa8299">
 <br><br>

 **[결과 확인]**<br>
- 샘플 데이터 선정하여 결과 확인
- 해당 샘플은 잘못 예측한 것으로, 정답은 `Shirt` 이지만 `Pullover` 로 예측
  
&nbsp;&nbsp;&nbsp;&nbsp;![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/ce1ca88d-d2d7-4e4a-8fb2-af20bb0b0772)
<br><br>

- Confusion Matrix로 확인
- 대부분이 올바르게 예측함

![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/11d18be0-da24-4c9c-a26f-a242b69a4e7a)
<br><br>


- 올바르게 예측한 그래프
- 가장 잘 예측한 종류는 `Sandal` 로 507개 중 `497개` 로 `98%` 맞게 예측 

![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/8e6e58f7-82e4-4af0-9f4a-51c3fffdfdb1)
<br><br>

- 잘못 예측한 그래프
- 가장 잘못 예측한 종류는 `shirt` 로 531개 중 `136개` 로 `25%`를 잘못 예측

![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/3e20f95a-5e3b-4d84-9377-c043d554b7be)
<br><br>

- 가장 잘못 예측한 종류인 Shirt의 결과 그래프
- 결과를 통해 Shirt를 `36%`만큼 `T-Shirt/top`로 예측했다는 것을 알 수 있음

![image](https://github.com/Konkuk-Univ-Glocal-Campus/introai202401-midterm-bkk21/assets/108513540/6c1fbc7e-13e5-4cd5-a3f3-97b4fdb342d7)
<br><br>
