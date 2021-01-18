---
title: 2021-01-18
category: Deep Learning
order: 2
---

# mAP란 무엇인가?
출처 :
https://eehoeskrap.tistory.com/237
https://better-today.tistory.com/1

mAP : mean Average Precision

### 1. Confusion Matrix
Binary Classifier의 Prediction 결과를 2x2 Matrix로 나타낸 것.
1) 첫번째 term : Prediction과 Ground Truth의 일치여부로 True/False 정함.
2) 두번째 term : Prediction 결과에 따라 Positive/Negative를 정함.

||Pred.|Pred.|
||+|-|
|+|True Positive|False Negative|
|-|False Positive|True Negative|

### precision
분류기의 성능평가지표로 사용하는 Precision-Recall에서의 Precision.
인식기(object-detector)가 검출한 정보들 중에서 Ground-Truth와 일치하는 비율

### AP(Average Precision)
Recall Value [0.0, 0.1, ..., 1.0] 값들에 대응하는 Precision 값들의 average.

### mAP(mean Average Precision)
1개의 object당 1개의 AP 값을 구하고, 여러 object-detector에 대해서 mean값을 구한 것.

#### 