# AIFFELTON canAIry(열화상 CCTV)

## 목차
1. [프로젝트 목적](#프로젝트-목적)
2. [파일 설명](#파일-설명)
3. [데이터 설명](#데이터-설명)
4. [데이터 정제](#데이터-정제)
5. [Object_Detection : YOLOV5, YOLOV7](#Object_Detection-:-YOLOV5,-YOLOV7)
6. [Anomaly Detection Model1 - PatchCore](#Anomaly-Detection-Model1---PatchCore)
7. [Anomaly Detection Model1 - PatchCore(학습과정)](#Anomaly-Detection-Model1---PatchCore(학습과정))
8. [Anomaly Detection 결과](#Anomaly-Detection-결과)
9. [Anomaly Detection Model2 - ML(SVM)과 비교](#Anomaly-Detection-Model2---ML(SVM)과-비교)
10. [YOLOV5를 활용한 이상치 탐지 평가지표](#YOLOV5를-활용한-이상치-탐지-평가지표)
11. [YOLOV5와 YOLOV7 이상치 탐지 비교](#YOLOV5를-활용한-이상치-탐지-평가지표)
12. [모델 경량화 성능 비교](#모델-경량화-성능-비교)
13. [최종 데이터 선정](#최종-데이터-선정)
14. [최종 모델 선정](#최종-모델-선정)
15. [최종 결과](#최종-결과)

<br/>

## 프로젝트 목적

열화상 이미지 활용한 실시간 산업시설 안전사고 예방 및 점검 시스템 구축<br/>

사용모델

- object_detection : YOLOV5, YOLOV7
- anomaly_detection : PatchCore
- machine learning : SVM

<br/>

## 파일 설명
EDA
: 모델 작업전 데이터 EDA

anomaly_detection
: 이상치 탐지 모델 구현 코드

object_detection
: 객체 탐지 모델(YOLOV5, YOLOV7)코드와 경량화 한 코드 포함

<br/>

## 데이터 설명
[열화상 데이터](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=514)

|데이터 영역|재난 안전 환경|데이터 유형|이미지|
|---|---|---|---|
|데이터 형식|JPG, JSON|데이터 출처|열화상 온라인 시스템 구축을 통한 열화상 및 실화상 데이터, 휴대용 시스템을 이용한 설비 측정 데이터|
라벨링 유형|바운딩박스(이미지)|라벨링 형식|JSON|
데이터 활용 서비스|전기 설비 및 기계 설비의 결함을 미리 확인하고 설비의 문제로 인한 사고 예방|데이터 구축년도,데이터 구축량|21년,38.5만 장|

- 구축 열화상 이미지 수: 452,788개<br/>
- 서부발전소 부품별 수량(단위: 개)<br/>

|고압전동기|차단기|변압기 접속부|신재생 설비|
|:---:|:---:|:---:|:---:|
|36,329|27,145|27,046|34,193|

- 변전소 부품별 수량(단위: 개)<br/>

|단로기(DS)|계기용변성기(MOF)|변압기 케이블 연결개소 포함|계기용 변압기(PT)|
|:---:|:---:|:---:|:---:|
|25,003|13,584|34,156|27,068|
|**계기용 변류기(CT)**|**전자접촉기**|**케이블&부스 연결개소**|**접지용 콘덴서**|
|11,017|22,899|25,640|9,139|

<br/>

## 데이터 정제
- 데이터수가 너무 많고 용량이 높아 로컬에서 다운 후 데이터 EDA를 거쳐 쓸모없는 데이터 삭제 후 사용

<br/>

![그림1](https://user-images.githubusercontent.com/98515262/193463506-c0d8a0e7-cbda-406f-8f7a-e3f745e983ae.png)



## Object_Detection : YOLOV5, YOLOV7

**사용이유 : 실시간으로 장비의 이상 유무를 판단하는 것이기 때문에 YOLO 모델을 사용함**

**학습 과정**

- 기본적인 욜로 학습 과정<br/>
![2](https://user-images.githubusercontent.com/98515262/192439678-4a12bca1-42a9-4371-9916-89864b64b022.png)
- input에 열화상 데이터를 넣어서 학습 시킴_RGB 파일<br/>
![화면 캡처 2022-09-27 142010](https://user-images.githubusercontent.com/98515262/192438616-f02de0c4-f2e9-4004-9f8a-c3b6b5bf6b9d.png)
- input에 열화상 데이터를 넣어서 학습 시킴_RAW 파일<br/>
![화면 캡처 2022-09-27 142140](https://user-images.githubusercontent.com/98515262/192438835-4133af37-1650-4e0d-bbec-2251c1f6ccf5.png)

<br/>


## Anomaly Detection Model1 - PatchCore
![화면 캡처 2022-09-27 143118](https://user-images.githubusercontent.com/98515262/192440233-db8bb2f3-eada-4f44-ac61-573d95044c84.png)

<br/>


## Anomaly Detection Model1 - PatchCore(학습과정)
![그림1](https://user-images.githubusercontent.com/98515262/193442493-c485c599-54c1-4d16-a126-308c1bede693.png)

<br/>

## Anomaly Detection 결과

- YOLOV5를 사용한 이상치 탐지와 결과를 비교해봄

<br/>

![그림2](https://user-images.githubusercontent.com/98515262/193463731-b6bc6a57-8565-40ff-bd66-0143e1e103e9.png)

<br/>

## Anomaly Detection Model2 - ML(SVM)과 비교

- YOLO를 사용한 이상치 탐지가 더 뛰어난걸 확인할 수 있음

<br/>

![그림3](https://user-images.githubusercontent.com/98515262/193463896-4c93a939-a089-4f51-b7f3-4aafb51f5443.png)

<br/>


## YOLOV5를 활용한 이상치 탐지 평가지표

**위의 실험을 통해 이상치 탐지에 YOLO를 사용해야 한다는 것이 밝혀졌다.**

**이번엔 RGB 데이터와 RAW 데이터 중 이상치 탐지를 어느 데이터에서 잘 하는지 확인해보겠음**

<br/>

- 변전소<br/>
![그림3](https://user-images.githubusercontent.com/98515262/193443008-2e0ab1f3-9b99-4960-9cbd-b853297cea7e.png)
- 쓰레기소각장<br/>
![그림4](https://user-images.githubusercontent.com/98515262/193443017-39da43ec-e002-4770-a624-4e843d61b004.png)
- 철도차량<br/>
![그림5](https://user-images.githubusercontent.com/98515262/193443032-6437d4e7-9581-473c-ba5f-431bb47b600d.png)

<br/>

## YOLOV5와 YOLOV7 이상치 탐지 비교

**RGB 데이터를 사용한다는것이 밝혀졌고 모델을 확인해보겠다.**

- 변전소<br/>
![그림6](https://user-images.githubusercontent.com/98515262/193464481-906f5d5e-9fb3-4328-b3be-3f9966fbd5ef.png)
- 쓰레기소각장<br/>
![그림7](https://user-images.githubusercontent.com/98515262/193464487-8f70c369-738c-4339-a9ee-46061c3f936b.png)
- 철도차량<br/>
![그림8](https://user-images.githubusercontent.com/98515262/193464494-39f2bf89-f924-4c66-b4e9-7015a39542b4.png)

<br/>


## 최종 데이터 선정
![그림6](https://user-images.githubusercontent.com/98515262/193443049-55ee49e1-b0d5-477d-b04f-52cf8d07dec2.png)
- 산업 시설별로는 철도차량이 가장 우수했음 파란 바운딩 박스는 mAP는 높지만 loss가 안정적이지 못했음<br/>
- 5class 학습은 여러데이터를 합쳐 사용하였기 때문에 특정 산업시설 이상치 탐지 부적절</br>
- 기차 데이터만 사용하겠음</br>

<br/>


## 모델 경량화 성능 비교
- v5m 구조에서 conv 레이어를 ghost conv 레이어로 바꾸어서 실험해봄

![그림7](https://user-images.githubusercontent.com/98515262/193443155-fee75b0b-ecfd-47fa-8405-f0facae6bbe1.png)

<br/>

## 최종 모델 선정

최종 모델은 다음과 같이 선정함
- 모델 : V5 경량화 모델
- class : 2개(철도차량)
- epochs : 300
- batch_size : 16
- image_size : 256


<br/>


## 최종 결과
- 철도차량(베어링) 이상치 탐지<br/>
![그림9](https://user-images.githubusercontent.com/98515262/193443232-71d76849-5322-41c4-b010-cd089a5473db.gif)

- 철도차량(기어박스) 이상치 탐지<br/>
![그림11](https://user-images.githubusercontent.com/98515262/193443377-0f84d37a-2041-4d9e-8710-185b65ea41b7.gif)

