# 경기도 용인시 전기차 충전소 입지 분석 모델 개발
* 2022년 빅콘테스트 챔피언부문 __대상(과학기술정보통신부 장관상)__ 수상


## 1. 분석 목표
* 경기도 용인시 내 완속 충전기 설치에 적합한 최적의 거점을 확보하는 모델 설계
* 설계된 모델을 통해 분석된 최종 입지 결과 확인


## 2. 분석 배경
최근 __화석연료의 가격 상승과 환경 문제의 심화__ 로 인해 정부에서도 __전기차 보급 정책__ 을 마련해 실행하고 있고, 이에 따라 국내 전기차 보급대수는 2014년 1075대 판매를 시작으로 2022년 현재 누적 30만대를 돌파하게 되었다. 또한 xEV TREND KOREA 2022의 조사 결과에 의하면 전기차 구매 의향을 묻는 질문에 95%가 긍정적인 의사를 밝혔으며, 이 중 59%가 3년 이내에 구입하겠다고 응답했다. 하지만 __늘어난 전기차 보급과 수요에 비해 여전히 전기 자동차 인프라는 부족한 실정이다.__  특히 충전기 설치 속도가 전기차 보급 확산 추세에 따라가지 못하는 점이 내연기관 자동차 운전자들이 전기차 구매를 주저하는 주요 요인이 되고 있다. 따라서 정부의 전기차 보급 확대를 위해서는 무엇보다도 __적절한 장소에서 전기차 충전소를 설치할 필요__ 가 있다. 한편 경기도와 용인시 또한 정부의 정책과 유사하게 보조금 제공 등의 보급 정책을 시행하며 충전 인프라 확충에 나서고 있다. 이에 발맞춰 __전기차 이용자가 쉽게 접근 가능하고__ 이를 통해 __충전소 이용 빈도 증가를 유도__ 하여 충전 설치 업체에는 __최고의 수익성을 충족__ 할 수 있는 __최적의 전기차 충전소 입지 선정 모델__ 을 객관적이고 과학적인 방법을 이용하여 개발하고자 한다.

## 3. 분석 과정
![model_structure](https://user-images.githubusercontent.com/90170238/212653305-e0dd6ae7-3408-4f07-9717-da53af2f087b.jpg)

### 분석 개요
평균 충전시간이 7~8시간으로 긴 완속충전의 특성상, 효율적인 입지 선정을 위해서 주거지와 직장과 같은 생활거점에 집중적으로 완속 충전소를 설치할 필요가 있다. 따라서 입지는 아파트, 공동주택, 업무시설, 공공기관, 주차장 등으로 한정되어 있다. 각 목적지의 정확한 기종점 수요를 분석하기 위해 위 입지를 거주지, 활동지로 나누어 해당하는 유형의 건물로 특정했다. 또한 현재 전기차 보급이 많이 운행되고 있는 지역뿐만 아니라 신규 충전 인프라 구축에 따라 증가할 신규 전기차 수요에 대응하기 위해 각 입지의 수요를 현재수요와 잠재수요로 나누어 분석했다. 도출된 거주지/활동지의 행정동별 수요지수와 건물별 현재/잠재수요를 결합하고 최대수요와 비용의 최소화를 고려하기 위해 기설치된 충전기 수를 활용하여 최종 입지를 선정하였다.

### 데이터 분석 기법
데이터 분석 기법으로는 회귀분석 모델과 k-means 군집화 모델을 사용하였다.

* Random Forest 회귀분석 모델
  - Elastic Net, Lasso, Ridge, LinearRegression, LGBM, XGboost, Random Forest, SVM등의 모델을 검토하여 RMSE값을 비교하여 RMSE값이 가장 낮은 모델을 사용, 선정된 모델의 feature importance와 permutation importance를 추출하여 모델의 성능에 영향을 미치는 여러 변수 중 의미있는 변수를 선정, 그에 따른 가중치를 부여하여 최종 입지 지표를 산출하는 방식으로 진행 
* 군집화 모델
  - 지역별 특성을 활용한 군집화를 통해 충전소가 가장 필요할 것으로 예상되는 지역그룹을 선정. 현재수요와 잠재수요를 대변하는 4개의 변수를 선택. Elbow method와 NBClust지표분석을 활용해 최적의 군집개수를 탐색

## 4. 분석 결과
* 거주지 분석 결과
![거주지결과](https://user-images.githubusercontent.com/90170238/212661939-c8794075-a4de-4db0-8722-da3ce3922a26.PNG)
* 활동지 분석 결과
![활동지 결과](https://user-images.githubusercontent.com/90170238/212662057-8dc94f08-bfcd-4aa8-b18f-147e82f8fca3.PNG)

## 5. 시사점
- 구축된 입지 선정 모델을 용인시 뿐만 아니라 다른 행정구역에도 적용하여 타 지역의 최적 입지 선정에도 도움을 줄 수 있다.
- 최적의 전기차 충전소 설치 구역을 선정하여 전기차 이용 편의를 제공하고 더 나아가 전기차 수요 향상에 기여할 수 있다.
- 구축된 입지 선정 모델에 전기차 충전소 전문가의 의견이 반영된다면 더욱 합리적인 입지 선정이 가능할 것이다.

