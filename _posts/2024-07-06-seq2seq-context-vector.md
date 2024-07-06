---
layout: post
title:  "Seq2Seq 모델 컨텍스트 벡터 내용"
date:   2024-07-06 12:45:22 +0900
categories: 잡담
tags : [딥러닝, 공부]
---

Seq2Seq 모델 관련 헷갈렸던 지점이 있다.
인코더에서 디코더로 보내는 내역이 정확히 무엇무엇인지이다. 
어디에선 은닉 상태(hidden state)만을 보낸다고 하는데, 어디선 아웃풋도 보낸다고 하고... 
검색해 본 결과 잘 설명된 글을 찾았다. 
[인코더의 아웃풋에는 어떤의미가 있는가 (영어)](https://datascience.stackexchange.com/questions/118855/what-does-the-output-of-an-encoder-in-encoder-decoder-model-represent)

어텐션을 사용하지 않을 경우 최종 은닉 상태만을 전달한다.
어텐션을 사용할 경우 어텐션 계산을 위해 아웃풋을 함께 전달한다. 
