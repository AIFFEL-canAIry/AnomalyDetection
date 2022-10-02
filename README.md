# AIFFELTON canAIry(열화상 CCTV)
- Step1. Data EDA<br/>
- Step2. Object Detection<br/>
- Step3. Anomaly Detection<br/>
- Step4. Model Improve<br/>

## Files
EDA
: 모델 작업전 데이터 EDA

anomaly_detection
: 이상치 탐지

object_detection
: 객체 탐지 모델 학습과 경량화

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
- 경량화 모델 학습 과정<br/>
![화면 캡처 2022-09-27 142913](https://user-images.githubusercontent.com/98515262/192439957-36d76b04-0240-4816-aef3-6d887076e0b6.png)

## Anomaly Detection Model - PatchCore
![화면 캡처 2022-09-27 143118](https://user-images.githubusercontent.com/98515262/192440233-db8bb2f3-eada-4f44-ac61-573d95044c84.png)

## Anomaly Detection Model - PatchCore(학습과정)
![그림1](https://user-images.githubusercontent.com/98515262/193442493-c485c599-54c1-4d16-a126-308c1bede693.png)

