# 항공사 고객만족도 분석
**프로젝트기간 : 2022.11.30 ~ 2022.12.05**

**사용 언어 : python**

**개발환경 : macOS Ventura 13.1, visual studio code**

**사용모델 : 랜덤포레스트, XGBoost**

***
### 프로젝트 개요
- 항공사를 이용한 고객들의 만족도 조사를 통해 '만족'과 '불만족'인 이유를 분석하여 개선해 나갈 서비스 파악 

### 프로젝트 배경
- 항공사는 고객들이 원하는 욕구를 충족시켜 우리 항공사를 이용할 수 있도록 하고, 단골고객의 이탈 방지를 위해 노력해야 함
- 항공 서비스에 대한 만족도를 항상 조사하고, 분석하여 개선해야 함

   
## 프로젝트 내용
### 1. 리커트척도(1점~5점)로 평가 된 항공서비스에 대한 만족도를 분석
- 데이터소개
<img width="1077" alt="스크린샷 2023-08-11 오후 4 48 16" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/8998ad8d-367b-48a8-998b-5308a0179023">

- EDA 및 데이터 전처리
<img width="1058" alt="스크린샷 2023-08-11 오후 4 48 28" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/8b691160-61e5-4eaf-bce4-b559ee57128a">

### 2. 데이터 시각화를 통해 가설검증
<img width="1036" alt="스크린샷 2023-08-11 오후 4 49 31" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/f1839667-5db8-4b32-ab30-dd3ae12ebfdd">
<img width="1032" alt="스크린샷 2023-08-11 오후 4 49 54" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/daa8e728-a3b0-4981-acb1-b7ae2f50ef4f">
<img width="1033" alt="스크린샷 2023-08-11 오후 4 50 07" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/8a579446-9cfe-4df0-b720-9b4671e790aa">
<img width="1042" alt="스크린샷 2023-08-11 오후 4 50 22" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/4c0ba2ec-8f9f-4fba-9298-a35342c1bcf8">

**가설 결론**

- 성별, 편리한 출발/도착시간, 게이트위치, 출발/도착지연시간은 만족도에 영향을 주지 않는다.
- 그 외 다른 서비스는 만족도점수가 높을수록 '만족'으로 이어진다.
- 나이, 비행거리, 좌석(class), 여행유형, 고객유형도 항공사 만족도에 영향을 미친다고 분석할 수 있다.

### 3. 랜덤포레스트, XGBoost 모델 학습 / 순열 중요도 / Feature Engineering을 통해 중요도가 낮은 특성 제외
- 이 가설들을 통해 만족도를 예측하는 모델 생성
- 만족도에 영향을 미치지않는 특성과 중요도가 낮은 특성을 제거해 학습
<img width="1034" alt="스크린샷 2023-08-11 오후 4 52 55" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/da01def2-e189-4654-913d-761ca4321a1d">
<img width="1035" alt="스크린샷 2023-08-11 오후 4 53 08" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/d90f841d-befb-4668-9ccf-8da1dc232bad">

### 4. SHAP 이용 모델 해석
- 기내와이파이서비스, 여행유형, 청결도 순으로 만족도에 긍정적 영향
- 기내엔터테인먼트에서 부정적인 영향을 주었지만 아주 적은 부분
- summary plot으로 확인해보면 만족도 예측에 영향력이 컸던 순으로 위에서부터 나열되어있고, 만족도에 중요한 특성들이기때문에 항공사에서 우선순위로 두고 관리해야 할 서비스라고 할 수 있음.
<img width="1037" alt="스크린샷 2023-08-11 오후 4 53 17" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/b27995d3-2573-43b4-8964-e45304de5127">

**결론**
- 기내 와이파이서비스, 온라인탑승, 수화물관리가 만족도에 큰 영향을 주기때문에 우선순위를 두고 관리해야함.
- '불만족'인 고객들의 낮은 서비스 점수들을 분석하여 해당 서비스를 개선할 수 있도록 조언함.

### 프로젝트 평가
- 데이터 선정과 전처리/EDA부터 머신러닝 예측모델을 통해 모델성능을 판단하고, 인사이트 도출, 해석하는 과정을 모두 진행
  
### 프로젝트 한계 및 개선방안
- EDA를 통해 데이터의 특징을 잘 살펴보고 가설을 검증하는 과정이 구체적이었으나 많은 가설 설정.
  
  -> 문제를 해결하기위한 핵심적인 가설 두, 세 개를 구체적으로 설정하고, 검증과 인사이트까지 도출하는 것이 더 좋을 것 같음. 
- 중요한 특성이 무엇이었는지 확인하는 것을 넘어 PDP를 통해 어떤 특성이 어떻게 영향을 주었는지 보면 만족도 개선을 위한 인사이트 도출에 더 도움이 되었을 것 같음. 
