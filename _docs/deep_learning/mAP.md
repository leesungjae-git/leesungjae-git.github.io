---
title: 2021-01-18_mAP
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

||Pred.(+)|Pred.(-)|
|**G.T(+)**|True Positive|False Negative|
|**G.T(-)**|False Positive|True Negative|

### 2. Precision / Recall
#### 2.1 Precision == TP/(TP+FP) == TP/(분류기가 P로 예측한 것)
Precision은 분류기가 P로 예측한 sample 중에서 맞게 예측한 것의 비율.
> 검출된 정보(TP+FP) 중에서 적절한 것들(TP)의 비율을 Precision이라고 함.


#### 2.2 Recall == TP/(TP+FN) = TP/(Ground Truth P의 숫자)
TP : 예측한 값과 G.T 값이 동일한 경우.  
FN : Negative로 예측했는데, 틀린 경우. => G.T가 Positive인 경우.  
TP + FN = 전체 G.T의 수.  
Recall은 G.T의 총 positive sample 중에서 positive로 맞게 예측한 것의 비율.
> 전체 정보(TP+FN)중에서 검출된 것(TP)의 비율을 Recall 이라고 함.


### 3. mAP 구하는 방법
[The PASCAL Visual Object Classes(VOC) Challenge](http://homepages.inf.ed.ac.uk/ckiw/postscript/ijcv_voc09.pdf) 수식
#### 3.1 recall-precision 그래프 그리기
1) Treshold를 0으로 정해놓고 detection 알고리즘을 모든 test image에 돌려본다.  
2) bounding-box에 해당하는 confidence score(객체일 확률)과 true positive/false positive 여부를 pair로 저장한다.  
3) (prob.) pair를 확률값에 따라 내림차순으로 정렬한다.  
[그래프 그리는 과정](https://www.youtube.com/watch?v=yjCMEjoc_ZI)

#### 3.2 Intepolated recall-precision 값 11개 구하기
위 수식에 따라 11개의 recall 값에 대한 precision 값을 구한다.  
11개의 recall 값 : [0.0, 0.1, …, 1.0] 의 evenly-spaced 11-values  

#### 3.3 AP 구하기
11개의 precision 값을 평균 낸다.  

#### 3.4 mAP 구하기
여러개의 object에 대해 AP 평균 내기.  

### 3. python 코드
[python 코드](https://github.com/penny4860/object-detector/blob/master/object_detector/evaluate.py)