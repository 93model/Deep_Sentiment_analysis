## 파이썬을 사용한 딥러닝 감성 분석 (Sentiment Analysis) 모델 및 데이터셋 생성

## ❓ 데이터 소개

 많은 양의 데이터를 빠르게 확보하기 위해, 업로드되어 있는 데이터를 선택하였다. 

- 네이버 영화 리뷰 (https://github.com/e9t/nsmc/)  
   : 20만건
- 네이버 쇼핑 리뷰(https://github.com/bab2min/corpus/tree/master/sentiment)   
: 20만건
- 스팀(steam) 게임 플랫폼의 리뷰  (https://github.com/bab2min/corpus/tree/master/sentiment)   
  : 10만건
- AI hub 감성 말뭉치 (https://aihub.or.kr/opendata/keti-data/recognition-laguage/KETI-02-010)  
  : 8만건 -> 전처리 후 4만건

## 🛠 문제

현재도 많은 양의 리뷰 데이터를 비롯한 자연어가 매일 쌓이고 있지만, 별점 시스템으로 인한, 자영업자의 스트레스와 정확한 리뷰를 남기고 싶은 소비자 사이의 갈등은 계속되고 있다. 

➡ 별점이 아닌 자연어로 된 리뷰 및 대화를 기반으로 이를 감성 분석 하여,     **제시된 문장이 긍정적인지 부정적인지 그리고 그 확률은 얼마나 되는지 예측한다**. 

## 🧹 데이터 전처리

- AI Hub 감성 대화의 경우 6가지 감정을 긍정, 부정, None으로 나누어 분석했다. 

| 기존 | label | 의미 |
| --- | --- | --- |
| 불안 | 0 | 부정 |
| 분노 | 0 |  |
| 슬픔 | 0 | 
| 상처 | 0|
| 기쁨 |1 | 긍정
| 당황 |nan

-  중복 및, 결측치 제거
- 훈련, 테스트 데이터 분할
- KoNLPy Okt적용하여 형태소 분석, Toknize  
  : mecab보다는 느리지만, 오타를 수정해주고 품사를 알아보기 쉽다. (단어 사전 제작)

## 🧠 딥러닝 
- LSTM 
- GRU  : LSTM 구조 간략화
- Drop Out : 과적합 방지


## ✔️ 결과

| 모델 | loss | acc |
| --- | --- | --- |
| LSTM| 0.2237 | 0.5836 |
| GRU  | 0.0970 | 0.8670 |
| LSTM + GRU | 0.0993 | 0.8638 |
| LSTM + GRU + Drop Out  | 0.0983 | 0.8664 |
| LSTM + Drop Out + GRU + Drop Out| 0.0981 | 0.8662 |

![ex_screenshot](./image/test.png)

## 🔍 회고

- 빠른 진행을 위해, 직접 크롤링을 하지 않고 수집된 데이터를 사용했다. 직접 크롤링해서 더 많은 데이터를 입력해야 한다.
- 지금도 준수한 성능이 나오지만, BERT 모델을 활용해 성능 개선을 이루고 싶다. 


