---
layout: post
title:  "Lesson 18. 비지도학습과 준지도학습 (Unsupervised and Semi-Supervised Learning"
date:   2024-07-15 12:45:23 +0900
categories: 공부
tags : [딥러닝,필기,공부]
---

조지아텍 온라인 석사과정 CS7647 '딥 러닝' Lesson 18 필기 내용

[전체 필기 링크 (구글독스)](https://docs.google.com/document/d/1_xd0n3O7GMBT9WNWLzyCKq7-PMLgz2GzvYObZuGAKfo/edit?usp=sharing)



<html>
<h3>
  <strong style="background-color: transparent; color: rgb(67, 67, 67);">Lesson 18. 비지도학습과 준지도학습 (Unsupervised and Semi-Supervised Learning)</strong>
</h3>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1. 소개</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 라벨링에 따른 분류</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">준지도학습 : 카테당 10+개 라벨있는 데이터 + 라벨없는 데이터</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Few-shot 학습 : 카테당 1~5개 라벨있는 데이터 + 보조적인 다른 데이터셋 (*Vanilla setting에선 라벨없는 데이터도 없음)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">자가지도학습 : 라벨 없음.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">비지도학습 : 라벨 없음. (클러스터링 등만 작업 가능)&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">위의 분류는 일반적인 분류일 뿐이며 혼합이 가능하다. (예: 준지도 few-shot 학습)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 무엇을 배울 것인가?&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">고전적 비지도학습 :&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">P(x) 모델링 (밀도측정)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">비교 / 그루핑 (클러스터링)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Representation 학습 (PCA)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">딥러닝도 대충 분류는 유사하다</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">P(x) 모델링 (Deep generative models)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">비교/그루핑 (Metric learning &amp; 클러스터링)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Representation 학습 (거의 모든 딥러닝 기법이 이에 해당)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">이번 강에서는 Feature Representation 분야에 대해서만 다룰 것임.</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 라벨 없는 데이터 다루기</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">어떤 손실함수를 사용할 것인가?</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">최적화 / 훈련 과정은?</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아키텍처는?</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">전이학습이 가능한가? (라벨 없는 데이터의 경우 특히 중요)</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 통상적인 핵심 아이디어들</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">라벨 없는 데이터에 대한 Pseudo-label 부착 (준지도학습)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">한계: Pseudo-label은 노이즈가 많을 수 밖에 없음</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Cross-View/Augmentation &amp; Consistency: 데이터에 변형을 2종류로 가한 뒤 약한변형 기반으로 pseudo-label을 붙이고 강한변형을 가한 데이터는 그 pseudo-label로 학습시킴</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">손실함수 : CE, (Soft) Knowledge Distillation</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">메타학습 (Few-Shot Learning) : 학습법을 학습함.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Surrogate Tasks (자가지도학습) : 예를들어 이미지를 회전시킨 뒤 회전된 이미지를 예측하게 함. 이처럼 자체로서는 무의미한 태스크들을 통해 feature representation 방법을 학습하게 하는것임.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">2. 준지도학습</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">라벨없는 데이터의 수집이 훨씬 쉬우므로 준지도학습의 필요성이 크다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">라벨있는 데이터의 양이 적을 경우 라벨없는 데이터를 통해 한계를 극복할 수 있을까?</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 우리가 원하는 이상적인 준지도학습 성과</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">highly-labeled 데이터를 능가하는 성능을 원한다!&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcDUz7ELZnivCXCbNk-phPY58_MKjbKnJy_yyBBpYrRhetBVo3BiQtKX1jzIBOKxCHWUUBscLho_WuBKLx-kZlqMOyxpGL7oGr_gDnpWxSkkTIJR_fejE3rk5wVXRjCssMTcKL_zg_xnkA66BG9t456Tnw?key=80SjqRecUP0TcEWfrVrriw" height="352" width="932">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 고전적 아이디어들 (pseudo-label)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">단순한 아이디어 : 라벨있는 데이터로 학습 -&gt; 라벨없는 데이터에 예측 -&gt; 새로운 훈련데이터로 추가함 -&gt; 반복</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Co-training과 합침 : 여러 view에 걸쳐 예측</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이는 1998년에 나온 아이디어임 (Avrim &amp; Mitchell) !&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">여기서 발전시켜, 앞서 이야기한 pseudo-label과 augmentation 활용을 할 수 있음.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) Pseudo-label 실제 활용&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">2단계에 걸친 훈련 (End-to-end로 한번에 훈련)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">미니배치 활용</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">라벨없는 데이터 배치 크기가 매우 큼 (이미지넷의 경우 라벨 데이터 1024 / 라벨없는 데이터 5120) -&gt; GPU 클러스터를 이용해야 했음</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdzEp2C-j2D_ZD3kIhBRYvoR66CAsKjEF-3gE-x8FRBqGcKpqZigpwI3iAWxzjnXPk0abVbQSBcCPidwlwCW0er-hp7pVOwSotjONMzeCDnJ6sfrxluu9XH53vJqgc4Z1wX_aO5_kTxtbEUUEb04BSuIg?key=80SjqRecUP0TcEWfrVrriw" height="536" width="1093">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 스케일링</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">라벨없는 데이터는 구하기 쉬우므로 scaling up이 쉽게 가능하다!&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">teacher/student model 구조를 사용할 수 있다</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) FixMatch 외의 다른 알고리즘들</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">MixMatch/ReMixMatch : FixMatch가 여기서 유래되었다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Virtual Adversarial Training : Adversarial 예시를 사용한 Augmentation</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Mean Teacher : Student/teaching distillation consistency with exponential moving average</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">6) Pseudo-label 외의 방법들 (FixMatch만큼의 효과는 없었음)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Label propagation : Pseudo-label과 유사</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">3. 퓨샷학습 (Few-Shot Learning)</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 퓨샷학습이란?&nbsp; : 카테고리별 라벨이 잘 갖춰진 데이터(base class data)에 기반하여, 라벨이 매우 적은 신규 카테고리들 (5-20개) 이 있는 데이터에 대해 학습하는 것.&nbsp;</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 베이스라인 파인튜닝 :&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">전이학습</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">분류기를 Base class에 대해 훈련시킴</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">(선택) freeze feature extractor</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">(‘query’ 할때) 약간의 라벨데이터를 사용해서 신규 클래스에 대한 분류 가중치를 학습함</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이 간단한 방법이 놀라울 정도로 효율적임.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">코사인 분류</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">FCL 대신 Cosine (유사성 기반) 분류기를 사용할 수 있음.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 일반적 방법의 단점</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Base class에서의 훈련은 과업이 무엇인지를 고려하지 않는다&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">우리가 N-way test를 할 것이라는 개념이 없다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">우리가 테스트때 보게 될 것을 시뮬레이션할 수 있을까? -&gt; 메타훈련</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 메타훈련 (Meta-Training)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">N-Way K-Shot Tasks : 테스팅때 하게될 과업과 유사하지만 보다 작은 과업들을 훈련중에 시뮬레이션한다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">(선택) 따로 떼어놓은 base class에 대해 pre-training을 할 수 있다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">테스팅은 이제, 방법은 동일하지만 새로운 클래스에 대해 행해지는 것이 된다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) 메타 학습 (Meta-Learner)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">학습알고리즘에게 어떤 파라미터를 줄 수 있을까?&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">메타 학습을 정의하는 2가지 방법</span>
  </li>
</ul>
<ol>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">기존의 학습 알고리즘에서 영감을 받는다</span>
  </li>
</ol>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">kNN/kernel machine : Matching networks (Vinyals et al. 2016)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Gaussian classifier : Prototypical Networks (Snell et al. 2017)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Gradient Descent : Meta-Learner LSTM (Ravi &amp; Larochelle, 2017), Model-Agnostic Meta-Learning MAML (Finn et al. 2017)</span>
  </li>
</ul>
<ol>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">블랙박스 신경망으로부터 유도한다.&nbsp;</span>
  </li>
</ol>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">MANN (Santoro et al. 2016)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">SNAIL (Mishra et al. 2018)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);"></span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">6) Gradient Descent에서 학습하기</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">배울것 : 파라미터 초기화. 갱신 규칙.&nbsp;&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아웃풋 : 파라미터 초기화. 파라미터를 어떻게 초기화할지 결정하는 메타학습자.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">혹은 초기화 방법만 배운뒤 일반적인 경사하강법을 사용할수도 있다 (MAML)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이 때 아웃풋은 그냥 파라미터 초기화 이다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">7) 메타학습 LSTM</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">경사하강법의 갱신 규칙은 LSTM의 갱신규칙과 상당히 비슷하다. LSTM을 아래와 같이 해석할 수 있다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfBqEuQBTQHKkqVHUbB0MnfdrX6gs-cl0GtPkNIF1xP22WW75S7QBekuDhybWHe-X-Wu7U14TyEpG7o1mguAl2pE4vWzqCFs9WGZRoqj7zittklJxZ9i4WMfTTWJTI0TI3vKH8qP-T1P5RcU7wEethgBw?key=80SjqRecUP0TcEWfrVrriw" height="417" width="847">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">경사하강법을 학습가능한 요소들이 여럿 있는 LSTM과 같이 해석함으로서 “경사하강법을 하는 방법”을 학습할 수 있다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">8) MAML (Model-Agnostic Meta Learning)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">LSTM을 훈련시킬것 없이 초기화 파트만 학습함. 어떤 초기화가 가장 효과적인지.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">매우 간단하므로 요새는 LSTM/RNN 기반 메타러닝보다 많이 사용된다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">4. 비지도 / 자가지도 학습 (Unsupervised and Self-supervised Learning)</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">라벨이 아예 없는 경우를 살펴보자.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">이번 강의에선 특히 연속적인 (이산적이지 않은) 데이터에 대한 차원축소 방법을 살펴볼 것이다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 오토인코더</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">인코더 : 이미지를 저차원 임베딩 벡터로 변환</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">디코더 : 저차원 벡터를 원 이미지로 복원</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">손실함수 : 인풋과 결과물 사이의 차이를 최소화 (MSE)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아이디어 : 네트워크가 정보를 저차원 임베딩으로 축소하도록 강제한다. 네트워크는 핵심 정보를 압축하는 방법을 학습한다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 오토인코더 파인튜닝</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">인코더가 잘 만들어지면 이제 인코더 끝에 선형계층을 붙여서, 라벨이 약간 있는 새로운 데이터를 분류하는 등의 과업에 사용한다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">새로운 데이터가 충분한 양이 아니면 인코더를 파인튜닝하지 않고 그냥 사용할 수 있다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 클러스터링 가정 (Clustering assumption)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">가정 : 밀도가 높은 곳은 클러스터를 형성하고 밀도가 낮은 곳은 클러스터를 분리한다. 여기에는 일관된 semantic 의미가 있다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이는 K-Means를 사용해 분리하고 t-sne등을 사용해 시각화할 수 있다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">딥 클러스터링 (Deep clustering) : 클러스터링을 통해 pseudo-label을 생성하고 이를 통해 분류한다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">엔지니어링을 통해 아래의 것들을 피해야 한다 :&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">빈 클러스터</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">무의미한 파라미터 (예: 모든 속성이 1개의 클러스터에 해당한다고 분류함)&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">클러스터간 심각한 불균형</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 대리 과업 (Surrogate Tasks) : 위의 내용을 일반화한 개념. 다양한 대리과업이 존재한다.&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">reconstruction</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이미지 회전 판별</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">colorization</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">relative image patch location (직소퍼즐)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">video : next frame prediction</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">instance prediction</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) Colorization</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">인풋 : 그레이스케일 이미지</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아웃풋 : 색칠된 이미지</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">손실함수 : MSE</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">6) 직소퍼즐</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">인풋 : 이미지 패치들</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아웃풋 : 개별 이미지 패치의 상대적 위치</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">손실함수 : CE (classification)</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">7) 회전 예측</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">인풋 : 다양한 각도로 회전된 이미지들</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아웃풋 : 회전각도 예측</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">손실함수 : CE (classification)</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">8) 대리 과업 평가 :&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">대리 과업으로 모델을 훈련시킴</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">ConvNet 혹은 인코더를 뽑아냄</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">실제 과업에 적용함</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">다른 지도학습 과업의 모델을 초기화할때 사용</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">다른 분류를 학습할 때 feature extraction을 위해 사용 (NN, SVM 등)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">보통 분류기는 선형계층으로 제한되고 feature들은 고정됨</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">9) Instance Discrimination</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Positive 예시(instance에 대한 augmentation)와 Negative 예시를 함께 집어넣음</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Positive 예시와 Negative 예시를 분류해야 함</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">손실함수 : Contrastive Loss (e.g. dot product b/w augmentation and pos &amp; neg examples)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Negative 예시는 어디서 가져와야 하는가?&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">고려사항: 효율, 특성 (너무 어렵거나 너무 쉽지 않아야 함).</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">메모리 뱅크 : 기존의 미니뱃치를 negative 예시로 사용하도록 queue에 넣음</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">메모리 뱅크 보강 : 모멘텀 인코더&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
</html>