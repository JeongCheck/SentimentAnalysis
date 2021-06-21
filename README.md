# SentimentAnalysis
대전광역시 주요관광지에 대한 구글 맵 리뷰 데이터를 감성분석한다.

## 모델 선택
1. Naver Sentimente Movie Corpus(NSMC)를 이용해 모델 성능 비교

|모델|BERT-base-multilingual|KoBERT|KcBERT|
|:---:|:----------------------:|:------:|:------:|
|정확도|0.86|0.90|0.90|

2. 다른 데이터로 fine-tuning
  (1) NSMC 데이터셋, 4 epochs, 0.90 acc
  (2) naver shopping review 데이터 셋, 5 epochs, 0.9738 acc 

3. fine-tuned 모델로 최종 데이터셋 (구글 맵 리뷰) 성능 비교

|모델|KcBERT|KcBERT-nsmc|KcBERT-shop|
|:---:|:----------------------:|:------:|:------:|
|정확도|0.60|0.80|0.79|
|RMSE|0.632|0.438|0.451|  

감성분석 데이터셋 두 가지를 사용해 fine-tuning한 모델들의 성능이 기존 KcBERT보다 좋음을 확인할 수 있었다.

## 감성 분석 점수 도출
- 파인 튜닝한 두 개의 모델을 이용해 15곳의 주요관광지에 대한 감성 분석 점수 도출
