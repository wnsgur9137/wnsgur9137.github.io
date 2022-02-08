---
layout: post
title: AI School(머신러닝) 05 [Regression Algorithm]
description: "AI School(머신러닝) 05 [Regression Algorithm]"
tags: [공부, AI]
comments: true
---

## **Regression Algorithm**  
<br>

회귀 문제를 의미하는 리그레션이 어떤 알고리즘을 활용해서 풀 수 있는지를 알아본다.  
<br><br>

### - Regression Algorithm

![Regression](/images/Regression/regression.png)  

Regression은 우리말로 회귀 문제라 한다.  
키에 따른 신발 사이즈, 시간에 따른 커피 소비량 등 의 문제를 Regression으로 풀 수 있다.  
즉, **어떤 특정한 숫자 값을 예측**하는 문제를 풀 수 있다.  
<br><br><br>

## **Simple Regression  **

![SimpleRegression](/images/Regression/simpleRegression.png)  

y = ax+b라는 간단한 수식에서 y는 <u>Dependent Variable</u>이라고 해서 종속변수를 의미한다. y는 계속 변하게 된다는 것이다.  
여기서 y가 변하게 하는 가장 큰 요소는 x로 <u>Independent Variable</u>라고 한다.  
a는 x의 <u>기울기</u>를 의미하고, x가 0일 때 <u>초깃값</u>을 의미하는 b의 값이 함께 영향을 미치게 된다.  
이 간단한 식이 바로 Simple Regression이다.  
<br>

![SimpleRegression2](/images/Regression/simpleRegression2.png)  

노란 점인 데이터들이 주어졌을 때 머신러닝은 데이터를 학습시키는 것이기에 이 점들을 다 어느 정도 만족시키는 그래프를 그릴 수 있다. 이렇게 그래프가 그려졌을 때 기울기와 y절편을 이용해서 y = ax + b 라는 함수를 구해 낼 수가 있다.  
<br>

![SimpleRegression3](/images/Regression/simpleRegression3.png)  

함수를 구해냈을 때 기울기의 변화에 따라 y절편이 달라질 수 있기 때문에 그 중에서 최적의 값을 찾는 과정이 필요하다.  
최적의 모델을 만들기 위해서는 a와 b의 최적의 값을 찾아야 한다.  
이를 계산하기 위해 위 사진과 같이 계산하게 된다.  
<br> 
기존에 가지고 있던 데이터와 모델이 예측한 값을 비교하여 주황색 동그라미(데이터)와 파란색 동그라미(모델이 예측한 값)의 차이가 얼마나 나는지를 비교하는 것이다.  
차이가 작으면 작을수록 모델이 예측을 잘 한 것이기에 모델이 예측한 값을 뺀 차이가 작아지는 경우를 계속해서 찾아가면서 a와 b의 값을 찾게 되는 것이다.  
그런데, 최적의 값을 찾다보면 음수가 나올 경우도 존재한다. 하지만 음수가 절대로 나와서는 안 되며, 음수 값이 나오게 되면 음수라서 차이가 작은 것인지, 아니면 정말 그 값에 차이가 커서 작은 것인지 구별하기 힘들기 때문에 다음과 같이 절댓값을 씌워준다.  

![절댓값](/images/Regression/simpleRegression4.png)  
<br>

혹은 절댓값을 씌우지 않고 제곱을 한 다음 루트를 씌우는 방법도 있다.  

![루트](/images/Regression/simpleRegression5.png)  

### - MLStudio에서 제공하는 Regression Algorithms  

Regression를 활용하기 위해서는 Supervised Learning이기 때문에 정답과 문제가 함께 데이터로 준비되어야 한다.  

![algorithmMap](/images/Regression/map.png)  

25개의 알고리즘 중 어떤 것을 사용해야하는지 선택해야한다.  
위 사진에서 스타드 동그라미에서부터 시작하게 되는데, 어떤 카테고리를 예측하거나 아니면 구조를 발견하거나, 이상한 점을 찾는 것이 아닌 **특정한 값을 예측하고 싶은 것**이기에 네모박스의 알고리즘을 보면 된다.  
화살표를 따라가게 되면 다음과 같은 여덟 개의 알고리즘을 볼 수 있다.  
<br>

![RegressionAlgorithms](/images/Regression/Algorithms.png)  
<br>

![RegressionAlgorithms2](/images/Regression/Algorithms2.png)  
<br>

![RegressionAlgorithms3](/images/Regression/Algorithms3.png)  

ML 스튜디오에서는 여덟 개의 Regression 알고리즘을 제공하고 있다.  
 * Ordinal Regression
   * 전체 데이터 중에서 어떤 아이템의 순서나 랭킹을 예측할 때 사용하는 알고리즘
   * 음의 값, 소수점의 값을 가질 수 없다.<br>정확한 Integer 정숫값을 가져야 한다.
 * Poisson Regression
   * 어떤 이벤트가 발생할 횟수를 예측해주는 알고리즘
   * 음의 값, 소수점의 값을 가질 수 없고 정숫값만 가지게 된다.
 * Fast Forest Quantile Regression
   * 어떤 값을 정확히 예측하기 보다는 데이터의 전반적인 분포를 예측할 때 사용
 * Linear Regression
   * 선형회귀 알고리즘이라고 한다.
   * 말 그대로 Linear 선형의 regression 회귀 문제를 푸는 것이다.
   * 간단한 모델이기 때문에 학습하는 속도가 빠르고 굉장히 널리 사용되고 있다.
   * 어떤 알고리즘을 사용해야할지 모를 때 기본적으로 처음에 시도해 보는 알고리즘이다.
     * 빠르고 적절한 정확도를 제안해주기에 앙상블 모델, 복잡한 모델인 경우에는 예측률이 그렇게 좋지 않다.
 * Bayesian Linear Regression
   * Bayesian 접근법을 적용하여 Linear regression을 조금 더 발전시킨 형태이다.
     * Bayesian : 일반적으로 생각했을 때 어떠한 일이 일어나는 것은 전부 다 독립적이라서 앞에 일어났던 일에 영향을 받지 않는다고 생각하지만 또 완전히 영향을 받지 않는것은 아니다라는 주장
 * Neuarl Network Regression
   * 신경망 회로를 이용하는 방법이다.
   * 복잡한 데이터에서 굉장히 뛰어난 성능을 보이기에 비선형 문제에 활용한다.
   * 커스텀하기 좋은 모델이다.
 * Decision Forest Regression
   * 의사결정 트리 모델을 활용한 Regression
   * 이진 트리를 활용해서 만들었지만, 이진 트리에 비해서 메모리 효율이 좋다.
   * 비선형 문제에서 좋은 성능을 나타낸다.
   * 이진 트리 자체가 오버 피팅이 일어날 수 있는 가능성이 높기 때문에 오버 피팅이 일어나고 있는지 고려한 다음에 사용해야 한다.
 * Boosted Decision Tree Regression
   * 이진 트리를 활용한다.
   * 일반적인 이진 트리는 이 앞단에 있는 노드에서 일어난 것을 전혀 싱경 쓰지 않고 다음 노드에서 독립적으로 판단하지만, Boosted Decision Tree는 이전에 트리에서 일어났던 결과를 다음에서도 종속적으로 이어받아서 계산에 영향을 미치기 때문에 조금 더 정확도가 높다.
   * 이전에 일어난 결과를 계속 다음으로 가지고 와야 하기 때문에 메모리 사용률이 크기에 메모리가 충분히 확보되었는지 고려해야한다.
   * 정확도가 높고 앙상블 모델에도 활용이 잘 되기 때문에 최근에는 Decision Tree가 인기가 많은 편이다.  
<br>

테이블 끝에 숫자는 각 알고리즘에서 변화를 줄 수 있는 파라미터의 갯수이다. 예를들어 Bayesian Linear regression에서는 수정할 수 있는 파라미터의 값이 두 가지이며, Neural Network Regression에서는 9가지의 파라미터를 수정할 수 있다는 것이다.  
파라미터를 수정할 수 있는 유연한 모델은 어떻게 파라미터 값을 주느냐에 따라서 굉장히 다양한 성능을 보여주기 때문에 최적의 알고리즘이 될 수도, 아닐 수도 있다.  
<br>

![RegressionAlgorithms3](/images/Regression/Algorithms4.png)  

어떤 정확한 값을 예측하고 싶다면 위 사진에서 아래에 있는 다섯 개의 알고리즘을 사용하는 것이 좋다.  
<br><br><br>

## **Multiple Linear Regression**
<br>

![MultipleLinearRegression](/images/Regression/Multiple.png)  

이전에 학습한 Simple Linear Regression은 y = ax + b라고 해서 독립 변수가 하나만 있는 경우이다. 하지만 멀티플에서는 그 의미가 여러 개를 뜻하기 때문에 리니어 리그레션이 여러 개 합쳐져 있는 모델을 의미한다.  
<br>

![MultipleGraph](/images/Regression/MultipleGraph.png)  

그래프로 살펴보면 위와 같이 Simple Linear Regression이 여러 개 쌓여 있는 형식이다.  
<br>

![MultipleData](/images/Regression/MultipleData.png)  

Simple Linear Regression은 하나의 Feature만 가지고 있는 겨웅라면, Multiple Linear Regression은 여러 Feature를 가지고 있다는 것이다.  
위 데이터에서 근무 연수 뿐만 아니라 나이, 부서에 따라서 연봉이 바뀌는 것과 같이말이다.  
Simple Linear Regression을 여러 개를 놔둔 것이기 때문에 내부적인 개념은 동일하다.  
<br><br><br>

## **Polynominal Linear Regression**
<br>

![PolynominalLinearRegression](/images/Regression/Polynominal.png)  

Multiple Linear Regression은 여전히 x 변수가 여러 개 있지만, 차원이 달라지는 것은 아니다.  
하지만 Polynominal Linear Regression은 x의 차수가 늘어나는 것을 의미한다.  
아래 직선 그래프는 Simple Linear Regression이고, 곡선 그래프는 Polynominal Linear이다.

![SimpleLinearRegressionGraph](/images/Regression/SimpleGraph.png)  
<br>

![PolynominalLinearRegressionGraph](/images/Regression/PolynominalGraph.png)  
<br><br>

머신러닝에서는 리니어를 하냐 안하냐의 기준을 x의 차수가 아니라, 앞에 붙어 있는 상수의 차수로 본다. 그러힉에 상수와 계수가 1차원으로 이루어져 있으면 그건 전부 다 리니어 하다고 이야기 한다.  
만약 a, b가 a분의 a제곱 혹은 -b 와 같이 복잡하게 이루어져 있다면 논리니어라고 한다.

![Linear](/images/Regression/Linear.png)  
<br><br><br>

## **NonLinear Model**  
<br>

리니어하지 않은 모델은 SVR(Supported Vector Regression), Decision Tree, Random Forest, Neural Network라는 그 외 다양한 알고리즘을 통해서 문제를 해결할 수 있다.
