# 제주도 도로 교통량 예측 AI 경진대회

|기간|Tags|역할|
|:---:|:---:|:---:|
|2022.10. ~ 2022.11.| DataAnalysis, ML Regression |팀장, 변수 생성 & 모델 개발|

#### 요구사항: 제주도민과 관광객의 증가로 인한 교통체증에 대비하도록 도로 교통량 예측 AI 알고리즘 개발
#### 1. 데이터 설명
외부데이터는 Train기간의 데이터만 사용해야 해 Test 기간의 데이터는 예측해야 한다. <br>
예측 task를 수행하는데 예측 변수를 사용함은 Noise가 되어 주어진 데이터만 사용한다.
<img width="259" alt="dacon" src="https://github.com/HASEOKYUNG/Dacon-JejuIsland-RoadTrafficPrediction/assets/104245855/cda95f16-468d-414e-84b9-1d7d6c30193d">

#### 2. 데이터 전처리
- 범주형 변수 중 특정 범주값의 비율이 0.95 이상이면 변수를 제거한다.
- 출발지점-도착지점(Edge)을 labeling하고 반대방향인 Edge는 음수 labeling한다.
- osmnx 패키지를 이용해 Edge 길이, 평균 속도, 소요 시간을 구한다. 추가적으로 haversine 거리를 구한다.

#### 3. 모델링
- 12개의 범주형 변수, 5개의 수치형 변수로 구성된 데이터로 피쳐 생성에 한계가 있고 과적합이 일어나기 쉬운 상황이다.
- LGBM과 CatBoost, Tabnet외 딥러닝 모델을 얕게 optuna, bayesian optimization하거나 수동으로 튜닝한다.
- 과적합되지 않은 LGBM, Catboost, Tabnet 모델을 Ensemble한다.

#### 배운 점
- Data Leakage를 확실히 인지하고 꼼꼼히 따져보며 모델을 개발한 기회였다.
- 주어진 데이터 특성에 맞게 전처리를 하여 모델 성능을 향상시켜 그 가치를 깨달았다.
- 분석 단계별 소요 시간을 계획하는 것의 중요성을 체감했다.
