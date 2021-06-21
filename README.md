# 2021-DACON-Credit_Card
[2021 데이콘] 신용카드 사용자 연체 예측
> 결과: 최종 score 0.6864. 상위 32%로 마감

- 정호섭, 선우지훈, 이현호 팀의 2021 DACON Repository입니다.
- 본 프로젝트는 Python의 머신러닝 기법을 활용하여 신용카드 사용자 연체를 예측하는 프로젝트입니다.

## 1.개요
### 1.1 프로젝트 배경 및 주제
신용카드사는 신용카드 신청자가 제출한 개인정보와 데이터를 활용해 신용 점수를 산정합니다. 

신용카드사는 이 신용 점수를 활용해 신청자의 향후 채무 불이행과 신용카드 대급 연체 가능성을 예측합니다.

현재 금융업계는 인공지능(AI)를 활용하여 금융 서비스를 구현하고자 합니다. 

사용자의 대금 연체 정도를 예측할 수 있는 인공지능 알고리즘을 개발해 금융업계에 제안할 수 있는 인사이트를 발굴해주세요!

> 신용카드 사용자 데이터를 보고 사용자의 대금 연체 정도를 예측하는 알고리즘 개발

## 1.2 데이터

- index
- gender: 성별
- car: 차량 소유 여부
- reality: 부동산 소유 여부
- child_num: 자녀 수
- income_total: 연간 소득
- income_type: 소득 분류
- edu_type: 교육 수준
- family_type: 결혼 여부
- house_type: 생활 방식
- DAYS_BIRTH: 출생일
- DAYS_EMPLOYED: 업무 시작일
- FLAG_MOBIL: 핸드폰 소유 여부
- work_phone: 업무용 전화 소유 여부
- phone: 전화 소유 여부
- email: 이메일 소유 여부
- occyp_type: 직업 유형
- family_size: 가족 규모
- begin_month: 신용카드 발급 월
- credit: 사용자의 신용카드 대금 연체를 기준의 신용도

## 2. EDA
- EDA 커널 참고

### 2.1 파생변수 생성
- 일한 기간/나이 : DAYS_EMPLOYED / DAY_BIRTH
- 소득 / 일한 기간 : income_total / DAYS_EMPLOYED
- 소득 / 나이 : income_total / DAYS_BIRTH
- 가족 구성원의 인당 소득 : income_total / family_size
- 카드를 발급 받은 시점의 나이 : DAYS_BIRTH - begin_month

## 3. 인코딩
![image](https://user-images.githubusercontent.com/72376781/122714891-0a586700-d2a3-11eb-9edb-7cc090f2b1c9.png)

unique한 값이 2 이하인 gender, car, reality는 label encoding 방법을 채택하고, 2개를 넘는 변수들은 one-hot encoding 방법을 채택함.

## 4. 모델링
- 주활용모델 : LGBM
