---
layout: post
title:  "Lesson 15. 신경망 기계번역 Neural Machine Translation"
date:   2024-06-29 12:45:23 +0900
categories: 공부
tags : [딥러닝,필기,공부]
---

조지아텍 온라인 석사과정 CS7647 '딥 러닝' 15강 필기 내용

[전체 필기 링크 (구글독스)](https://docs.google.com/document/d/1_xd0n3O7GMBT9WNWLzyCKq7-PMLgz2GzvYObZuGAKfo/edit?usp=sharing)


<html>

<head>
  <style>
    .ql-indent-1 { padding-left: 3em; }
    .ql-indent-2 { padding-left: 6em; }
    .ql-indent-3 { padding-left: 9em; }
    /* ... other styles ... */
  </style>
</head>

<h3>
    <strong style="background-color: transparent; color: rgb(67, 67, 67);">Lesson 15. 신경망 기계번역 Neural Machine Translation</strong>
  </h3>
  <p>
    <br>
  </p>
  <p>
    <strong style="background-color: transparent; color: rgb(0, 0, 0);">1. 신경망 기계번역 (Neural Machine Translation)</strong>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 번역은 어려운 문제다</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">통상적인 인풋 문장 1개에 대해 다양한 올바른 번역이 존재할 수 있다.</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">언어는 모호하다. (‘The professor said on Monday we’d have an exam’에서 Monday는 무엇을 수식하는가? 교수가 말한 때인가, 시험을 보는 때인가?)</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">언어는 문맥에 좌우된다. (동음이의어)</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">언어는 서로 매우 다르다. (어순 등 구조적 차이, 암시/명시 차이)</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 기계번역 모델</span>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">
      <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfnLUtBrP81G9nZDHpbEkcAEjn40eC_EcrZLMcaqcR7UiV9suo36eeqOBejSq7N25-Vq2dHApakLWq1KcwbIkBXIIrKVZmVolLPs1LmXYYKNC3uAikph47AXIwKsM69UcA07r0WfjU6g9HIZk8CWTriYw?key=80SjqRecUP0TcEWfrVrriw" height="304" width="602">
    </span>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 시퀀스 생성은 자기회귀식(autoregressive)</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">번역은 주로 조건부 언어 모델로 모델링된다.</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">p(t|s) = p(t_1|s) * p(t_2|t_1,s) * … * p(t_n|t_1, …, t_n-1, s)</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">각 아웃풋 토큰의 가능성은 아래 내용에 기반해 좌-&gt;우 순서로 개별적으로 계산된다</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">전체 인풋 문장 (인코더 아웃풋)</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">이전까지의 모든 예측 토큰 (디코더 “상태(state)”)</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">argmax p(t|s)는 처리가 어렵다.</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">가능한 시퀀스에 대한 지수 검색 공간 (exponential search space)</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">빔 검색 (beam search)로 계산</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">통상적 빔 크기는 4~6</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 빔 검색&nbsp;</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">빔 서치(beam search)란?</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">지수공간을 선형시간(O(n))으로 검색</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">빔 크기 k는 검색의 ‘너비(width)’를 결정한다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">각 단계에서, k개 요소 각각을 1개 토큰만큼 늘린다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">이후 전체중 상위 k개 요소가 다음 단계의 빔 크기 k (= 가설(hypothesis))가 된다.&nbsp;</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">빔 서치 (추가 설명)</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">각 빔 요소는 다른 상태(state)를 보유한다. (트랜스포머 디코더의 경우 이는 이전 단계에서의 셀프-어텐션 인풋이다)</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">총 계산수 (total computation) 는 빔 너비와 선형으로 증감한다.&nbsp;</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">하지만 빔 전체에 걸쳐 계산을 병렬처리할 수 있다. 그래서 GPU에서 효율적이다.&nbsp;</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">
      <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXe1e2g_amwPN4X4q9XQcmH-P8XxFLOI9vHOdj2wQoh9Q2RDch43f0uYvy6CB5a_NvxQxsg7oqwKlv-Q3_J30lBcIBSATZ1updgxCRm8dIIsNGShLJRWkvFAAAJ_iSHQcUjRpI-RRaz0bvxVs01RpJzdVA?key=80SjqRecUP0TcEWfrVrriw" height="180" width="602">
    </span>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">5) 신경망 기계번역 아키텍쳐들 (인코더/디코더에 사용)</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">RNN(주로 LSTM)</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">양방향 인코더</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">중대 돌파구 : 인코더-디코더 어텐션 (Bahdanau et al 2014)</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">합성곱</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">너비고정 합성곱 연산에 기반한 인코더/디코더</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">단순 활성화 함수&nbsp;</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">트랜스포머</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">대부분의 최신 연구에 사용되는 아키텍처</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">처음엔 기계번역을 위해 제안되었음</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">최근엔 BERT 및 그 부류들로 잘 알려짐</span>
    </li>
  </ul>
  <p>
    <br>
  </p>
  <p>
    <strong style="background-color: transparent; color: rgb(0, 0, 0);">2. 효율적 추론 (Inference Efficiency)</strong>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 추론이 연산비용을 좌우한다 - 모델 대부분은 한번 훈련시키고 수만번 사용된다</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">무엇이 비용을 차지하는가?</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">단계별 연산 (자기회귀식 추론 (autoregressive inference))</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">아웃풋 투영 : Θ (|단어| * 아웃풋 길이 * 빔 크기)</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">모델 깊이</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">전략</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">아웃풋 단어집합 (vocabulary) 축소</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">보다 효율적인 연산</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">깊이를 얕게 하고 병렬성을 높임</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 단어집합 축소 (Vocabulary reduction)</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">단어집합이 크면 아웃풋 투영의 비용이 증가한다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">하지만 모든 인풋 시퀀스에 대해 모든 토큰이 똑같이 사용 가능성이 높은건 아니다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">IBM 정렬모델 (IBM alignment model)은 통계적 기술을 사용해 한 단어가 다른 단어로 번역될 가능성을 모델링한다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">어휘 사용 가능성 (lexical probability) 을 통해 주어진 인풋에 대해 가능성 높은 아웃풋 토큰들을 예측할 수 있다.</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">60%까지 속도 증가에 성공했다</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 바이트-페어 인코딩 (Byte-Pair Encoding)</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">문제: 사용 확률이 낮은 단어 모델링</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">글자별 모델링을 할 경우, 실사용시 너무 느릴 수 있다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">서브워드 (subword) 모델은 단어를 빈도별로 잘라냄으로서 이를 해결한다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">널리 사용되는 알고리즘 중 하나는 바이트-페어 인코딩 (BPE)이다.&nbsp;</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">
      <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXf70j6CPVW641sg8Oy6Ih_-L1BmduxDhyIZO0HR3w_c6nSXSe1Wp2Z2enItwCynTx24KvadtWic1eXOgFy5mv9xk2mrda0gQEPUj8Gvq6uhZ2UfVCjempFOXZFE7sXKsC92lWEkT5KNPAQj9kmQD9aNcIk?key=80SjqRecUP0TcEWfrVrriw" height="331" width="326">
    </span>
  </p>
  <p>
    <br>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">바이트-페어 인코딩은 ‘압축(compression)’에서 유래했다. 이는 가장 자주 맞붙어있는 쌍을 재귀적으로 교체하는 작업이다. 아래 예시 참고.&nbsp;</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">
      <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeRNvtVN_bf3xVS3A6_q4ZguNdqKawbA_VqYqBeiiXOs0TXL1o8X-RnCu4fCmuGQNt8kdW5dFjTCdPBWOqvOsxhOmuYXUzZVX-oQNe7_CEOr5FhC3lXpLyla_oK_17zvKnc-ckhZ2TiX5w2qbht3x3DOlY?key=80SjqRecUP0TcEWfrVrriw" height="206" width="524">
    </span>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 레이어 드롭&nbsp;</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">‘드롭아웃’ 과 유사한 개념이다. 확률적으로 레이어를 가지치기(prune)하는 것이다.&nbsp;</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">
      <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcNqOoyLmWCd_NFTzQKQ0ShmGccYraF6mZ_Usw3WeSavF0SMJzy2LdbyYsQ2kYe8RjHXLtGcEXV579Jzs8lmJyqILTWxwnamcj8JFKKmpFP3i_wgIeamlWAUAareE3dOn82weqRAnwpqW1ZUeGQSjDOoqY?key=80SjqRecUP0TcEWfrVrriw" height="223" width="602">
    </span>
  </p>
  <p>
    <br>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">5) 하드웨어 고려사항</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">추론은 특수 하드웨어상에서 더 빠르다 (GPU, TPU 등)</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">배치(batch) / 온디맨드(on-demand) : 여러 개의 인풋을 한번에 번역함으로서 평균 효율을 높일 수 있다</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">GPU/TPU 등 사용시 특히 그렇다</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">하지만 실시간 시스템의 경우 적용이 어렵다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">병렬연산</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">GPU/TPU 사용시 특히</span>
    </li>
    <li class="ql-indent-1">
      <span style="background-color: transparent; color: rgb(0, 0, 0);">자기회귀 추론 시간은 주로 decoder에 쓰인다</span>
    </li>
  </ul>
  <p>
    <br>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">6) 양자화 (quantization)</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">계산시간은 행렬곱셈이 다 잡아먹고 있다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">lower precision domain에서 연산함으로서 추론 속도를 높일 수 있다</span>
    </li>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">훈련시에도 양자화가 가능하다 (예: NVIDIA GPU에서 F16)</span>
    </li>
  </ul>
  <p>
    <br>
  </p>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">7) 비-자기회귀적 기계번역 (Non-Autoregressive Machine Translation)</span>
  </p>
  <ul>
    <li>
      <span style="background-color: transparent; color: rgb(0, 0, 0);">현재 (2020년경) 시점 최신 연구분야</span>
    </li>
  </ul>
  <p>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">
      <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdWQFJi1-qW7YpwVuUyxrWAT9KgO_WedPq5qdXckKYpoOXSaRliILZnW3m9QIh5gKdvvb3MBeZC6WGitwNrXKgTM1z1f2T8DRNTNqcqhGMIeehzw288EDGZy0Y7zGIb0vfpxY0YwVzYBwZIjNjTZ6VGZTQ?key=80SjqRecUP0TcEWfrVrriw" height="341" width="586">
    </span>
  </p>
  <p>
    <br>
  </p>
  <p>
    <br>
  </p>
  <p>
    <br>
  </p>
</html>