## lightGBM
모델장점
- LightGBM 모델은 소요 시간과 메모리 사용량이 적지만 예측 성능은 타 모델과 차이가 적다.
- 리프 중심 트리 분할 방식을 사용하여 불균형한 트리 분할 방식으로 예측 오류 손실을 최소화 할 수
있다.
- 10,000건 이하의 데이터 세트의 경우 과적합이 발생하기 쉽지만, 현재 데이터는 10,000건 이상의
 데이터이기 때문에 과적합에 큰 영향을 받지 않을 것으로 판단하여 모델을 선정하게 되었다.



## 모델링 분석

**AUC**
- ROC 곡선의 아래쪽 면적을 의미
- 값이 높을 수록 더 좋은 분류기이다.
- AUC = 1 이면, 1을 정확히 분류하는 완벽한 분류기를 의미



**SMOTE(합성 소수 과잉표본)**
- 불균형 데이터에서 예측 모델링 성능을 향상시키는 방법 중 하나
- 1) 업샘플링된 레코드와 비슷한 레코드를찾고 2) 원래 레코드와 이웃 레코드의 랜덤 가중 평균으로 새로운 합성 레코드를 만든다 3) 각각의 예측변수에 대해 개별적으로 가중치를 생성한다 4) 새로 합성된 업샘플 레코드의 개수는 데이터의 균형을 맞추기 위해 필요한 업샘플링 비율에 따라 달라진다

SMOTE 적용 전 학습용 피쳐/레이블 데이터 세트:  (2135712, 45) (2135712,)
SMOTE 적용 후 학습용 피쳐/레이블 데이터 세트:  (4177498, 45) (4177498,)




## ✅ 현재 코드에는 적용하지 않았지만, 알아두면 좋은 것!
실무적으로, 분류 규칙을 정할 때 AUC만으로 충분하지 않을 수 있다.
한다/ 안한다의 확률을 예측하는 것은 중간 단계이다.
이떄, 최상의 컷오프를 결정하려면 비용들을 종합적으로 고려할 필요가 있는데 이것을 '기대 수익'이라고 한다.

**기대수익** = P(Y =0) * R + P(Y=1)*C 

R: Y=0일떄 얻을 수 있는 수익
C: Y=1일때 얻을 수 있는 수익

즉, 결과를 한다/ 안한다 둘 중 하나로 결정하는 대신, 그것을 통해 얻을 수 있느 기대수익이 있는지 없는지로 결정하는 것이 더 말이 된다. 사업의 목적인 '기대 수익'을 결정하기 위해 상품의 전체 가칠ㄹ 얻어내야 한다.
