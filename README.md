# 항공사 고객만족도 분석
**프로젝트기간 : 2022.11.30 ~ 2022.12.05**

**사용 언어 : python**

**개발환경 : macOS Ventura 13.1, visual studio code**

**사용모델 : 랜덤포레스트, XGBoost**

***
### 프로젝트 개요
- 항공사를 이용한 고객들의 만족도 조사를 통해 '만족'이나 '불만족'인 이유를 분석 

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

- 게이트 위치, 편리한 출발/도착시간, 출발/도착지연시간, 성별은 만족도에 영향을 주지 않는다.
- 그 외 다른 서비스는 만족도점수가 높은만큼 '만족'으로 이어진다.
- 나이, 비행거리, 좌석(class), 여행유형, 고객유형도 항공사 만족도에 영향을 미친다고 분석할 수 있다.

### 3. 랜덤포레스트, XGBoost 모델 학습 / 순열 중요도 / Feature Engineering을 통해 중요도가 낮은 특성 제외
<img width="1034" alt="스크린샷 2023-08-11 오후 4 52 55" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/da01def2-e189-4654-913d-761ca4321a1d">
<img width="1035" alt="스크린샷 2023-08-11 오후 4 53 08" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/d90f841d-befb-4668-9ccf-8da1dc232bad">

### 4. SHAP 이용 모델 해석
<img width="1037" alt="스크린샷 2023-08-11 오후 4 53 17" src="https://github.com/jinmyeonghee/Satisfaction-Prediction-ML/assets/114460314/b27995d3-2573-43b4-8964-e45304de5127">

### 프로젝트 평가
- 두번째 학습에서 데이터를 추가적으로 학습. 백그라운드 이미지를 활용.

  -> 해당 프로젝트는 클래스가 2개밖에 되지 않기때문에 confidence score가 (물체를 잡지 못 하는 것에 대해서) 학습이 잘 되지 않는 경우가 많은데, 백그라운드 이미지를 통해 어느 정도 학습할 수 있기 때문에 성능이 높아졌을 것으로 생각됩니다.

### 프로젝트 한계 및 개선방안
- 학습데이터에 <대형차>만 있었기때문에 소형차, 중형차에 대한 과적차량을 잘 인식하지 못함
  
  -> 소형차, 중형차도 같이 학습을 시키면 더 높은 성능을 낼 수 있을 것이다.
- 모델의 성능 평가 측면에서 클래스가 적으므로 mPA를 무조건적으로 신뢰할 수 없음
  
  -> 따라서 다양한 클래스 및 이미지를 추가하여 학습하는 것이 좋을 것이다.
