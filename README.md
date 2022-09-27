# AIFFELTON canAIry
- Step1. Data EDA<br/>
- Step2. Object Detection<br/>
- Step3. Anomaly Detection<br/>
- Step4. Model Improve<br/>

## Files
01_make_dataset.ipynb
: YOLO 데이터셋 구축 (경로 설정, 라벨 생성, 데이터셋 분리)

02_run_yolov7.ipynb
: 학습 및 추론

03_display_result.ipynb
: 추론 결과 확인

## Dataset
[열화상 데이터](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=514)

|데이터 영역|재난 안전 환경|데이터 유형|이미지|
|---|---|---|---|
|데이터 형식|JPG, JSON|데이터 출처|열화상 온라인 시스템 구축을 통한 열화상 및 실화상 데이터, 휴대용 시스템을 이용한 설비 측정 데이터|
라벨링 유형|바운딩박스(이미지)|라벨링 형식|JSON|
데이터 활용 서비스|전기 설비 및 기계 설비의 결함을 미리 확인하고 설비의 문제로 인한 사고 예방|데이터 구축년도,데이터 구축량|21년,38.5만 장|
