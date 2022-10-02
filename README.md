# AIFFELTON canAIry(열화상 CCTV)
- Step1. Data EDA<br/>
- Step2. Object Detection<br/>
- Step3. Anomaly Detection<br/>

## Files
EDA
: 모델 작업전 데이터 EDA

anomaly_detection
: 이상치 탐지 모델 구현 코드

object_detection
: 객체 탐지 모델(YOLOV5, YOLOV7)코드와 경량화 한 코드 포함

## Dataset
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


## Model pick - YOLO
- 기본적인 욜로 학습 과정<br/>
![2](https://user-images.githubusercontent.com/98515262/192439678-4a12bca1-42a9-4371-9916-89864b64b022.png)
- input에 열화상 데이터를 넣어서 학습 시킴_RGB 파일<br/>
![화면 캡처 2022-09-27 142010](https://user-images.githubusercontent.com/98515262/192438616-f02de0c4-f2e9-4004-9f8a-c3b6b5bf6b9d.png)
- input에 열화상 데이터를 넣어서 학습 시킴_RAW 파일<br/>
![화면 캡처 2022-09-27 142140](https://user-images.githubusercontent.com/98515262/192438835-4133af37-1650-4e0d-bbec-2251c1f6ccf5.png)

## Anomaly Detection Model - PatchCore
![화면 캡처 2022-09-27 143118](https://user-images.githubusercontent.com/98515262/192440233-db8bb2f3-eada-4f44-ac61-573d95044c84.png)

## Anomaly Detection Model - PatchCore(학습과정)
![그림1](https://user-images.githubusercontent.com/98515262/193442493-c485c599-54c1-4d16-a126-308c1bede693.png)


## 산업 시설별 이상치 탐지 평가지표
- 서부 발전소<br/>
![그림2](https://user-images.githubusercontent.com/98515262/193442919-d7346fa0-8d4a-4567-89a1-7db275c05e1d.png)
- 변전소<br/>
![그림3](https://user-images.githubusercontent.com/98515262/193443008-2e0ab1f3-9b99-4960-9cbd-b853297cea7e.png)
- 쓰레기소각장<br/>
![그림4](https://user-images.githubusercontent.com/98515262/193443017-39da43ec-e002-4770-a624-4e843d61b004.png)
- 철도차량<br/>
![그림5](https://user-images.githubusercontent.com/98515262/193443032-6437d4e7-9581-473c-ba5f-431bb47b600d.png)

## 최종 데이터 선정
![그림6](https://user-images.githubusercontent.com/98515262/193443049-55ee49e1-b0d5-477d-b04f-52cf8d07dec2.png)
- 산업 시설별로는 철도차량이 가장 우수했음 파란 바운딩 박스는 mAP는 높지만 loss가 안정적이지 못했음<br/>
- 5class 학습은 여러데이터를 합쳐 사용하였기  특정 산업시설 이상치 탐지 부적절</br>

## 모델 경량화 성능 비교
![그림7](https://user-images.githubusercontent.com/98515262/193443155-fee75b0b-ecfd-47fa-8405-f0facae6bbe1.png)


# 최종 결과
- 철도차량(베어링) 이상치 탐지<br/>
![그림9](https://user-images.githubusercontent.com/98515262/193443232-71d76849-5322-41c4-b010-cd089a5473db.gif)

- 철도차량(기어박스) 이상치 탐지<br/>
![그림11](https://user-images.githubusercontent.com/98515262/193443377-0f84d37a-2041-4d9e-8710-185b65ea41b7.gif)

