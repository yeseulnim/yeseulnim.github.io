---
layout: post
title:  "Lesson 19. 생성 모델 (Generative Models)"
date:   2024-07-18 12:45:23 +0900
categories: 공부
tags : [딥러닝,필기,공부]
---

조지아텍 온라인 석사과정 CS7647 '딥 러닝' Lesson 19 필기 내용

[전체 필기 링크 (구글독스)](https://docs.google.com/document/d/1_xd0n3O7GMBT9WNWLzyCKq7-PMLgz2GzvYObZuGAKfo/edit?usp=sharing)




<html>
<h3>
  <strong style="background-color: transparent; color: rgb(67, 67, 67);">Lesson 19. 생성 모델 (Generative Models)</strong>
</h3>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">1. 소개</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 소개</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이번 강의에서는 비지도학습 중 ‘밀도추정’ 과 관련된 부분, x에 대한 p(x)를 추정하는 부분에 대해 배울 것이다. 그리고 그 p(x)를 바탕으로 새로운 x를 생성하는 법을 배울 것이다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">딥러닝의 재부상 이전에도 이러한 관점은 존재했다. (예: 가우시안 혼합 모델 (gaussian mixture model))&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 판별 모델 vs 생성 모델 (Discriminative vs. Generative Models)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">판별 모델 : P(y|x)를 구하고자 함.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">예: 신경망, SVM 등</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">생성 모델 : P(x)를 구하고자 함.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">우리의 모델을 P(x,θ)로 파라미터를 설정하고, 최대우도법을 이용하여 라벨없는 데이터셋에 대해 파라미터를 최적화할 수 있다.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이를 통해 샘플을 생성할 수 있기 때문에 생성 모델이라 불리운다.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">예: multivariate gaussian with estimated parameters μ, σ</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이는 고차원 데이터일수록 어려운 작업이 된다.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">가장 흔한 방법 3가지를 살펴볼 것이다.&nbsp;</span>
  </li>
  <li class="ql-indent-2">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">PixelRNN: Joint distribution as explicit, tractable density</span>
  </li>
  <li class="ql-indent-2">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">VAE : Joint distribution as explicit, approximate density</span>
  </li>
  <li class="ql-indent-2">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">GAN: Implicit density</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdUK9GXvrH0uUHe8qEv8xDLHPGu5rQEOqIfEug63SVD_QWZqsyatQq7SZDnJNciXZ_Oj1axMWdBArd0MtV11iveHWgS39nHa95M7QY9-S1lsbS-fwbC9in7IVVxyMMzr_qhQNfCDIoCNoewbDI0Ximtjg?key=80SjqRecUP0TcEWfrVrriw" height="411" width="661">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">2. PixelRNN &amp; PixelCNN</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) Factorizing P(x) : 상황을 단순화하기 위해 연쇄법칙을 사용해 결합확률분포를 decompose할 수 있다.&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">결합확률분포를 여러 조건확률분포의 곱으로 factorize한다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">베이지안 네트워크, 언어 모델과 비슷하다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">변수들의 순서정리를 필요로 한다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이후 이 조건확률분포를 신경망으로 추정할 수 있다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 이미지용 모델</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">훈련시 픽셀단위로 이동하며 이를 시퀀스로 취급하고 언어모델처럼 훈련시킬 수 있다. teacher forcing을 사용한다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">단점 : 시퀀스가 순서대로 생성되므로 과정이 느리다. 각 픽셀에 대해 context pixel이 매우 적다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) Pixel CNN</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아이디어: 조건확률분포를 합성곱 계층으로 표현한다.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">보다 넓은 context를 고려할 수 있다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">실제 구현시, 마스크를 적용하고, 아직 고려대상이 아닌 픽셀은 0처리한다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">훈련 속도가 빠르지만 시퀀스 생성은 여전히 느리다 -&gt; 작은 이미지에만 적용가능하다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">예시: Image Completion, Image Generation</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">생성과정에서 sequence에 대한 assumption이 들어가므로, 디테일을 살폈을 때 실제와 거리가 먼 이미지들이 생성된다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">3. 적대적 생성 신경망 (GAN: Generative Adversarial Network)</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">파라미터가 있는 density function을 배우는 것이 아니라, 파라미터가 있는 생성 과정을 배운다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 암시적 모델 (Implicit models)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">암시적 생성 모델은 p(x)의 명시적 모델을 배우지 않고, p(x)로부터 샘플을 생성하는 법만 배운다.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">적절한 feature representation을 학습</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">data augmentation 시행</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">강화학습을 위한 world model을 배움 (시뮬레이터)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">어떻게?</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">신경망의 아웃풋에서 샘플링하는 법을 학습</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">적대적 훈련: 한 신경망의 예측으로 다른 신경망을 훈련시킴 (동적인 손실함수)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">안정적인 최적화를 위한 여러 트릭이 존재</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 샘플링 학습</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아이디어 : 단순한 확률분포 (가우시안)에서 샘플링 -&gt; 샘플을 신경망을 거쳐 p(x)로 변환</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">인풋 : 독립적인 가우시안 랜덤 숫자 벡터 -&gt; CNN으로 이미지 생성</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">처음엔 완전히 랜덤한 이미지가 생성될 것. 어떻게 사실적인 이미지를 생성하도록 학습시킬 수 있을까?&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">아이디어: 생성된 이미지를 ‘판별모델’ 네트워크에 통과시켜 진짜인지 거짓인지 구분하게 함. 판별모델도 생성모델과 동시에 학습하게 함.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) GAN 구조</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXd0CPfo3L1Yi2I_5EUiOWlrIlR4LzYHGsMFe80Re8BDhVf_KkV8D-_iNglMBGLbKn9K_Mq1s_k7N_dd16VzfrFA0HAAeXjoBb00Lg0e7uTf6RxhiSk6Advg4yAdj2gH2hPiBzkexCKSZwoI0v17TlHH2eI?key=80SjqRecUP0TcEWfrVrriw" height="400" width="885">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">2개의 경쟁하는 네트워크가 있으므로 min-max 2player 게임과 같음. 게임이론과 연관점 있음.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">min-max 목표 :&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">D(x): 판별기가 출력하는 실제이미지일 확률 [0,1]</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">x: 실제이미지. G(z): 생성된 이미지.</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXf62hB-CMEtIfemFSSvFbW-g8XvqDy5rlFtKhPFvqirxLBbsI4PWmbOAIu-g1fDD1pIB4aliV4nUSV08ZTvqSs7l7zc9hE0gm9ASmHnEiiwGY7nTWzheZFwFMs8Fhhl-OHOYhMDxXUjQto2n29r9MTnaZM?key=80SjqRecUP0TcEWfrVrriw" height="151" width="795">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfS0Tg3Is_aRBSSTDxxJSofSCBZ71kVP3RueDqclTbhzRTaO7zwoLw3kWMpVjz6WoPLfafjPowkGedUgpit4KH1X-IauaCZEtcMgg0_CJiKrS2Q6iyKrDv7yDMZ7wffHOUiKHDjPv-8T7w2gvETFxaSjq8?key=80SjqRecUP0TcEWfrVrriw" height="146" width="820">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">판별기 : D(x)와 1-D(G(z)) 를 모두 1로 올리고 싶어한다. 즉 D(x)는 1로, D(G(z))는 0으로 하려 한다.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">생성기: D(x)는 무관. 1-D(G(z))를 0으로 낮추고 싶어한다. 즉 D(G(z))를 1로 올리고 싶어 한다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXesIXKzqDur4qOLkr9pThv854M1R3qT8M7eXSI8q4-S-wUm72Sp5ZNNYBc2ejn8oIMhkZF9Q-nkTZu6P31hVH6-6svyB7Itch7qvbW8ifeZWqKluTfPHDm5_z_i1paUq_iXngqizZNXVWWcG3WMBiXORg?key=80SjqRecUP0TcEWfrVrriw" height="428" width="866">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) Max-Max game으로 변환</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">생성기 부분의 gradient가 좋지 않다. D(G(z))가 높을때, 즉 판별기가 틀렸을때 gradient가 높다. 우리는 샘플이 나쁠때 (즉 판별기가 맞을때) 생성기가 개선되기를 원한다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">따라서 생성기에 대해 다른 목표를 설정해줄 수 있다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfmc8Wb0bC9v_7igI94RWkKpg_SGFwzONcEayVH12XHwu8A6kkBH_FH2nzfsYkqsBAZ_gNUDbjFg2upSVtwGLAhd1q0dQwMZt2vAbY_KHP1wa5reJljG4HO8U3RPAamy65gD_wLONByYDyhxOJ2lLHwMZY?key=80SjqRecUP0TcEWfrVrriw" height="78" width="407">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) 전체 알고리즘</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcdYDQ4WC-D4EGIOOCByJKuxHwTbMGjf_bTDLj1mXHpsaDzU9w6Q8wCwiAPDJp5WsKwvbfko12XDGM5ZlT3kwlP2F1u3n1pqmj0j-30Ay7Jhf4evV6YVOjj1OPe18o-Ds_ONZOQyYTK7QcCoe58e-ZY5w?key=80SjqRecUP0TcEWfrVrriw" height="440" width="654">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) GAN의 단점 : 훈련이 어려움</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">mini-max 때문에 훈련이 어려움</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">그간의 발전사항 : 보다 안정적인 아키텍처, 최적화 개선을 위한 규제, 점진적인 훈련 및 스케일링</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">DCGAN : batch norm 사용, FCL 없앰, relu 사용 등.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">6) 규제</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">생성기가 훈련데이터를 그냥 외우거나, 아님 확률분포의 일부분만 생성한다면?</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">mode collapse: 훈련분포의 일부 mode 만 잡아낸다면? (예: 남성얼굴만 생성)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">간단한 규제방법 : 실제샘플에 노이즈를 추가함</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">4. 변분 오토인코더 (VAE: Variational Autoencoder)</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 생성 모델 (디코더 부분)&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">우리가 원하는 것은 임베딩 벡터가 이미지 생성에 필요한 여러 요소들을 갖추고 있는 것이다 (위치, 스케일 등)&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">
      <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfSyrlb6k86GMXeY5ujrDUUbDgC0TLo8XKqY39gbgXWe7JqyZ8rxiPi6m7X8mEZgzAq--KXdGyl5IeJMjLV7UPzjiR7_Iegct9tCTK23pBMgLunSYRbIs3DwUV2bsGujNiQ_wLYN21RHQfEkuZC5Lh1ePE?key=80SjqRecUP0TcEWfrVrriw" height="86" width="385">
    </span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">위의 P(X) likelihood는 적분때문에 최대화할 수가 없다. 대신 variational lower bound (VLB)를 최대화한다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 변분 오토인코더 : 디코더</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">확률적 관점, 샘플링, 오토인코더, 그리고 추정치 최적화를 모두 하나로 모을 수 있다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">보다 단순한 확률분포에서 샘플링된 Z가 있다. 이를 디코더에 통과시켜 ‘확률분포의 파라미터’를 출력한다. 예) 가우시안 분포의 μ와 σ&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 변분 오토인코더 : 인코더</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">확률적 관점, 샘플링, 오토인코더, 그리고 추정치 최적화를 모두 하나로 모을 수 있다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">주어진 이미지에 대해 Z를 추정한다.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이번에도, ‘확률분포의 파라미터’를 출력한다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXe4cfSqk_-9o8qM1GDlQ-JB5bk-OjMVLzD2JPzvgzTjJK8WJHTmL7Qq64Kg0h7LWuBwFLc4TqSeL3FYgrKgqhTsitHNZvLFcNk_X4_MXn8Xj1SpweVEFaRAWRnflJ4FDL8PLnggbX5zN-ZBDLUi9cYOtI4?key=80SjqRecUP0TcEWfrVrriw" height="298" width="625">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) Likelihood 최대화</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">어떻게 2개의 신경망에 대한 파라미터를 최적화할 수 있을까?&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">데이터의 log likelihood는 아래와 같다</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcRrms3n52jEpLVf4Io60e0tKtin4NECvqQLicvQNcrAxmUR1amLFfrPFieqRtJDZF4NY4mMibsL0MxtofpFXTGrorhBSxtd8LcWwEPzPNtB0noxA59xr_0t4sih7nCHrEzaw6KioCWunX37sDzZa79Kfw?key=80SjqRecUP0TcEWfrVrriw" height="337" width="901">
  </span>
</p>
<p>
  <br>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">참고 : KL-Divergence : 항상 0 이상인 값을 가짐</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXf9MppFgg4GcZpHdWtZYzRBm24kFZuf668FM6hymczsYGsLGZefkTFCMgtub-kPx4mAXE0r7YkNSVUKwOI3ME-lHDJVju-r3mtUxl0s0tvmRSUhoAj8SDbHjGDe_0p3UkB05pGoDypb1-vRyJcPlK-M4NA?key=80SjqRecUP0TcEWfrVrriw" height="291" width="741">
  </span>
</p>
<p>
  <br>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">따라서 log likelihood의 최종형태는 아래와 같다</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdZzVKNW7W2dbWCPsCma2mbgRHgLlsPIiw0LDBSnTdbJmINet4x8XpSfBnG_iEBujbdORO5geCFrz6zyYwEEHelF6gat0nBiezbAhWqAqhDD0v-Fwnb4VvjjnrhVRkdb1Crd4MXAfvEu-gHI_nbt2XuyQ?key=80SjqRecUP0TcEWfrVrriw" height="151" width="778">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">참고사항 : <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcpH7YQrmYOtgvXxAMCCgp_dI_ZGP1dpr5EW9UiLUxfO_GT05naTHaURpD2WtTCB2LgFvHwdP4cCc1KdOJ9cpqh8znUeKfg8qjC80vY8_hJ_Ofa4XB5_0_hxG5PKjqvRztB1Y2o7kOL5fyPF1tjlXjHQnM?key=80SjqRecUP0TcEWfrVrriw" height="181" width="860">
    </span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdZkBWACVvBdFarE58wkCoZGoAmbl1oUES4LOoMfCWkE-IhB3XmhgP27K5VYweegiUDhrVkvCOIHPDRTnsHbBY2l58K4bmTqbXwSTzMY5wFCqaNEmE868AzCQgZGuqpUVLchUrDnrXEsYeFil5omyBLp24?key=80SjqRecUP0TcEWfrVrriw" height="187" width="860">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) 변분 오토인코더 최종형태 정리</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXekdFP1AojVxM04YGx3kPA9WYXnKl22yHMj2UUWzBuTXLisHKa6zIAV61keDuyvBeoTsPGKILQgQxq8lZ9sIXcCIYAVTH9TB08MQiTtlsQedLmfZ0fA_0J-xEFkV4aju3nX8B3GLiqKZFXka2MGYGwcIIM?key=80SjqRecUP0TcEWfrVrriw" height="470" width="904">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">6) Reparameterization Trick</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">문제점 : 샘플링 함수에 대해서는 역전파가 불가하다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">해결책 : Reparameterization Trick&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">설명 : 샘플링시의 무작위성이 인코더 아웃풋으로부터 독립적이도록 한다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">가우시안 분포 예시</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">기존 : 인코더 아웃풋 = 랜덤 변수 z~N(μ, σ)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">바꾼뒤 : 인코더 아웃풋 = [μ, σ]</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">z = μ + ε*σ, ε~N(0,1)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">7) 요약</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">VAE는 approximate maximum likelihood optimization을 할수있는 원칙을 제공해준다. (단 몇 가지 전제가 필요하다. 예: 가우시안분포)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">VAE로 생성된 샘플은 대체로 GAN 샘플만큼 뛰어나지는 않다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">비지도학습으로 학습한 latent features 가 다른 과업 (downstream tasks) 적용시 효과적인 경우들이 있다.&nbsp;&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <br>
</p>
</html>