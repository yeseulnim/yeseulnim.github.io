---
layout: post
title:  "Lesson 14. 신경망 어텐션 모델 (Neural Attention Models)"
date:   2024-06-28 12:45:23 +0900
categories: 공부
tags : [딥러닝,필기]
---
조지아텍 OMSA 과정 중 CS7643 '딥 러닝' 수업을 수강하며 필기한 내용을 일부 남긴다. 
아래는 14강 '어텐션'의 필기 내용이다. 


<html>
<h3>
  <strong style="background-color: transparent; color: rgb(67, 67, 67);">Lesson 14. 신경망 어텐션 모델 (Neural Attention Models)</strong>
</h3>


<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">관련 자료</strong>
</p>
<p>
  <a href="https://arxiv.org/pdf/1706.03762" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">Attention is All You Need 논문</a>
</p>
<p>
  <a href="https://arxiv.org/pdf/1810.04805" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">BERT 논문&nbsp;</a>
</p>
<p>
  <a href="https://jalammar.github.io/illustrated-transformer/" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">The Illustrated Transformer (블로그 글)</a>
</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">1. 소프트맥스 / 어텐션 미리보기&nbsp;</strong>
</p>
<ol>
  <li> 어텐션!</li>
  <ol>
  <li class="ql-indent-1"> “어텐션” : 컴퓨테이션 상태와 인풋에 따라 인풋에 가중치 혹은 확률분포를 부여하는 것</li>
  <li class="ql-indent-1"> 어텐션은 최소한의 구조적 전제하에 원거리의 컴퓨테이션 노드 간에 직접적으로 정보가 전파되도록 해준다</li>
  <li class="ql-indent-1"> 현재(2020년) 신경망에서 가장 널리 사용되는 어텐션의 형태는 소프트맥스와 함께 시행된다.&nbsp;</li>
  </ol>
  <li> 소프트맥스 리뷰</li>
  <ol>
  <li class="ql-indent-1"> 모든 x_j ∈R 인 {x_1 … x_n} 가 있을 때</li>
  <li class="ql-indent-1"> 소프트맥스 ({x_1 — x_n}) = {(e^x_1)/Z … (e^x_n)/Z} (* Z = Σ^n (e^x_j)&nbsp;</li>
  <li class="ql-indent-1"> 모든 인풋에 대해 소프트맥스는 확률분포를 반환한다</li>
  <li class="ql-indent-1"> 소프트맥스는 순열변경(permutation)에 대해 equivariant하다. 즉 인풋의 순열을 변경해 소프트맥스돌리면 아웃풋도 원 아웃풋의 순열을 변경한 값이 나온다.</li>
  <li class="ql-indent-1"> 소프트맥스는 선형함수가 아니다 : 인풋을 전부 x2하면 아웃풋에서 max값의 비중이 높아진다. (아래 그림 참고)</li>
  </ol>
</ol>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdpfuGq9FbuApbnaB9fUWKfEIb3Ephos3zsQs1EqaqMnc2X6bbAzCqfbNg5TGGXN5nyT8G36UUU5ZFIW-Cme5Y8r3sB3m1MHkNsZTO75zrFvPdWqKMQP-caayNbONZfIvhUEPHg9ca7yyUEK9Hkb7qj8fE?key=80SjqRecUP0TcEWfrVrriw" height="340" width="602">
</p>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeFoMg-esYueRbTNiaVeHz0DHc_OIFzajc9PzPLJUD3BCsuCMjrbyprT7mHATRoaIaFRW_SINro0xGIhSnlG47BfYEBBvaDpl7C3sN7CrgEr_1ESYXW5M8ZWSx-_qCxjx8N4X3_aBnnUMxJp1ECKwD41g?key=80SjqRecUP0TcEWfrVrriw" height="351" width="602">
</p>
<ol>
  <li> ‘소프트맥스’ 는 사실 ArgSoftmax라고 불러야 한다. 2개의 분포를 합친 것이라서.&nbsp;&nbsp;</li>
  <ol>
  <li class="ql-indent-1"> 인덱스를 균등하게 랜덤으로 선택하는 분포</li>
  <li class="ql-indent-1"> Argmax 인덱스를 1의 확률로 선택하는 분포</li>
  </ol>
  <li> 소프트맥스는 미분가능하다</li>
  <li> 인덱스 선택이란?&nbsp;</li>
  <ol>
  <li class="ql-indent-1"> 소프트맥스 분포 (0~1)에서 랜덤 샘플링을 하면 각 항목의 원래 값의 크기에 따라 샘플링 확률이 정해지는 샘플링을 할 수 있다.&nbsp;</li>
  <li> 어텐션에서의 활용</li>
  <li class="ql-indent-1"> 세트에서 벡터 선택하기</li>
  <ol>
  <li class="ql-indent-2"> {u_1 … u_n} 벡터와 “쿼리” 벡터 q 가 있다.</li>
  <ol>
  <li class="ql-indent-3"> 어텐션 레이어에 대한 인풋은 벡터 세트로 주어지며 이 중 벡터 하나를 선택하게 된다. 이 때 역전파가 가능하도록 미분가능한 방식으로 골라야 한다.&nbsp;</li></ol>
  <li class="ql-indent-2"> 미분 불가한 방법 :&nbsp;</li>
  <ol>
  <li class="ql-indent-3"> q와 가장 비슷한 벡터는 j_hat = argmax(j) u_j · q 와 같이 선택할 수 있다.</li>
  <li class="ql-indent-3"> 이는 p = p_hard 분포로서 j_hat 을 제외한 모든 인덱스에서 mass가 0이다.&nbsp;</li>
  </ol>
  <li class="ql-indent-2"> 미분 가능한 방법 :&nbsp;</li>
  <ol>
  <li class="ql-indent-3"> q와 가장 비슷한 벡터는 p = Softmax(Uq)로 구할 수 있다.&nbsp;</li>
  <li class="ql-indent-3"> U 는 벡터들을 행렬의 행들로 배열한 것이다.&nbsp;</li>
  </ol>
  <li class="ql-indent-2"> 이게 “소프트맥스 어텐션”이다!</li>
  </ol>
</ol>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXe9jFkv002J44A3p87tU7QuntzfXBlbRPlMmahyFjswQQML9wTYAnemf7WiBpkkZOvwZf8KxFp5mrj8kky9k36Vjs1U8ZBNf0Y3Hr1pzVZTrNj5r3Knl7QtJE3UqRiayibMWVOJOMNOEDDEWMMjNKXPWog?key=80SjqRecUP0TcEWfrVrriw" height="333" width="602">
</p>
</ol>
<ol>
  <li> 소프트맥스 어텐션과 MLP 아웃풋</li>
  <ol>
  <li class="ql-indent-1"> 소프트맥스가 MLP의 마지막 레이어에 적용될 때</li>
  <ol>
  <li class="ql-indent-2"> q : 마지막 hidden state. {u_1 … u_n} : 클래스 라벨의 임베딩</li>
  <li class="ql-indent-2"> 확률분포로부터의 샘플링은 라벨링(아웃풋)에 상응함</li>
  </ol>
  <li class="ql-indent-1"> 소프트맥스 어텐션:</li>
  <ol>
  <li class="ql-indent-2"> q = 내부적 hidden state. {u_1 … u_n} : ‘인풋’ (즉 이전 레이어)의 임베딩.</li>
  <li class="ql-indent-2"> 확률분포는&nbsp; {u_1 … u_n} 를 요약한 것에 상응함.&nbsp;</li>
</ol></ol></ol>
<p>
  <br>
</p>
<p> 2. 어텐션</p>
<ol>
  <li> 어텐션이란?&nbsp;</li>
  <ol>
  <li class="ql-indent-1"> 머신비전 문제에서 시작하자.&nbsp;</li>
</ol></ol>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXd2H3kbMs7vesZPazE89_vauRRSFvuA66rI_lGe66NmKGweQ4ywavFwmo1udS7E1jJTtiC2tMqycfepkAyVKnIHLci7aUVEfa_P_H7F-WqoSEaWmhnY_Yfey2Ez0PaJu0mNe_m_8qF1vvvoV8ogMVeLtw?key=80SjqRecUP0TcEWfrVrriw" height="353" width="485">
</p>
<p> ‘왼쪽에 텐트가, 오른쪽에 식탁이 있는 사진’을 두고, ‘테이블의 왼쪽에 무엇이 있지?’ 라고 물었다. 이 때 시스템은 우선 질문에 언급된 유일한 객체인 ‘테이블’에 집중한다. 그리고 나서 그 왼쪽에 있는 물건인 ‘텐트’에 집중하고, 이를 정답으로 대답할 것이다.&nbsp;</p>

  <li> “어텐션”이란, 인풋에 대한 확률분포로서, 컴퓨테이션 상태와 인풋 자체에 따라 달라진다.&nbsp;</li>
  <li> 어텐션은 ‘하드’ ‘소프트’ 어텐션이 있다.</li>
  <ol>
  <li class="ql-indent-1"> 하드 어텐션 : 인풋에 대한 확률분포로부터 샘플링</li>
  <li class="ql-indent-1"> 소프트 어텐션 : 확률분포에 따른 가중평균값이 직접 사용됨.&nbsp;</li></ol>
  <li> 현재 신경망에서 가장 널리 쓰이는 어텐션은 소프트맥스로 시행된다.&nbsp;</li>
  <ol>
  <li> 머신비전(Machine Vision)에서의 어텐션</li>
  <ol>
  <li class="ql-indent-1"> 컴퓨터 비전 분야에서 긴 역사가 있다. 원래 도약안구운동(saccade)에서 영감을 받았다. (96년 Rajesh et al 등등)</li>
  <li class="ql-indent-1"> 이 연구들에서, 어텐션은 한 이미지 안의 공간적 장소들의 세트에 대한 것이다.&nbsp;</li>
  <ol>
  <li class="ql-indent-2"> 현재 상황과 glimpse의 역사를 볼때, 향후 어떤 곳에 대해 어떤 scale로 살펴보아야 할까?&nbsp;</li></ol></ol>
  <li> MLP와 어텐션</li>
  <ol>
  <li class="ql-indent-1"> 기계번역에서의 정렬 (alignment) : 타겟언어의 각 단어에 대해, 소스언어의 단어 확률분포를 구한다. (93년 Brown et al 등등)</li>
  <ol>
  <li class="ql-indent-2"> 예시: 독어 -&gt; 영어 번역.&nbsp; 각 영단어에 대해 매핑되는 독단어들 찾기</li>
  <li class="ql-indent-2"> input은 소스 문장이고 computational state는 문장에서 번역중인 부분</li></ol>
</ol>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdJwSJL_zKAxSibJ_pSB1DGhHWbKEUMLf3bGuv85ByK4Va8rVz7iqWr6geYVrKnhG3RJcSM4w2MpAWLA8tZaukTfQU1a-x-AzVW0D7_xyFBURbEtNSltemKvcpUNB6K921wDQIU8xoPVPVBGpu6HiivA9o?key=80SjqRecUP0TcEWfrVrriw" height="319" width="426">
</p></ol>
<ol>
  <li> 신경망 계층으로서의 어텐션</li>
  <ol>
  <li class="ql-indent-1"> (2021년 기준) 상대적으로 ‘최근’ 개발되기 시작. 아마 하드웨어 등의 이유로?&nbsp;</li>
  <ol>
  <li class="ql-indent-2"> 위치 기반, 손글씨 생성 : [Graves 2013]</li>
  <li class="ql-indent-2"> 콘텐츠 기반, 기계번역 : [Bahdanau et al 2014]&nbsp;</li>
  </ol>
  <li class="ql-indent-1"> (소프트)어텐션에 대한 일반적 접근방식 :&nbsp;</li>
</ol>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdPVI1k9AKfO7FhRRj3TU3XmNdQNM-1FYPd-ZyaEkumNvBEIB1R-knFbgvcxgcID4JWKYum4zHOxOHereZ8xko9vBXSHVWZCctT3u_sQF7xJxUWvsTP5odOyknTQ3DI4qjZBTx7B7y4S23uyTuMFNTV2Ys?key=80SjqRecUP0TcEWfrVrriw" height="396" width="602">
</p>
<ol>
  <li> 다른 레이어와의 차이점</li>
  <ol>
  <li class="ql-indent-1"> 완전연결계층 (FCL) : 고정된 인풋, 고정된 아웃풋</li>
  <li class="ql-indent-1"> RNN : 비고정된 인풋, 고정된 아웃풋&nbsp;</li>
  <li class="ql-indent-1"> 소프트맥스 : 인풋에 따라 hidden state가 커짐. 이것이 소프트맥스의 특장점 중 하나임.</li>
  </ol>
  <li> 다층 소프트 어텐션 (Multi-Layer Soft Attention)</li>
  <ol>
  <li class="ql-indent-1"> 예시: hidden state 가 controller 인 q임. q를 업데이트할때 softmax를 사용.&nbsp;</li>
</ol>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXenbZbswC-GzQBBZi5WQlPZNLJyTVnNg_VYbkMuBzXAUrWupXzlYTIan7BJbh3WItbECwwJrDHMMkNx1hp9P-uPlSLw7xGHW7ylerYDP0iiVu6hmSH7gcwcr67Pw0y8l0mCT4dHM31OqaZlXbzEfyET5uM?key=80SjqRecUP0TcEWfrVrriw" height="213" width="602">
</p>
<ol>
  <li> 모델을 사용한 추론의 예시</li>
</ol>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeVgplF3UH7YSq-bwJCkzdY2VPig_ZNMMSAcj7TEL6LdqjkcbOgp6j2lW-GpynDtCkjCtOeY-Yg10rFS52N-lr0U2qKsets-PhJO4CazQEKZaZ2aCRcR4IbQ5-4BwUkB9JBCCgGik1gjYS7-doBjIHHu9w?key=80SjqRecUP0TcEWfrVrriw" height="131" width="447">
</p></ol>
<ol>
  <li> 인풋의 기저에 깔린 기하학적 구조가 있다면, 이에 대한 정보를 가중치 ‘bag’에 포함시킬 수 있음. (예: 문장의 어디에 위치한 단어이냐 등)&nbsp;</li>
  <ol>
  <li class="ql-indent-1"> 중요 예시 : 포지션 임베딩 (position embedding). 순서가 있는 데이터 (sequential data)의 경우, 위치 인코딩 (position encoding)을 사용. 해당 인풋 시퀀스에서의 위치를 알려줌.&nbsp;</li>
  <ol>
  <li class="ql-indent-2"> 각 인풋 m_j에 대해, 이를 벡터 l(j)에 추가함.</li>
  <li class="ql-indent-2"> l(j)는 훈련중에 수정될수도 있고 학습될수도 있음</li>
  <li class="ql-indent-2"> 예시: 각 지점마다 frequency가 다른 사인곡선 (sinusoid)</li>
  </ol>
  </ol>
</ol></ol>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">3. 트랜스포머 (Transformers)</strong>
</p>
<ol>
  <li> 트랜스포머란?</li>
  <ol>
  <li class="ql-indent-1"> 다층 어텐션 모델. 현재 (2021) 대부분의 자연어 관련 과업에서 실제 사용되는 기술</li>
  <li class="ql-indent-1"> 기존의 어텐션 기반 아키텍쳐들보다 유능함. 비결은 :&nbsp;</li>
  <ol>
  <li class="ql-indent-2"> Multi-query hidden-state propagation (“self-attention”)</li>
  <li class="ql-indent-2"> Multi-head attention</li>
  <li class="ql-indent-2"> Residual connections, LayerNorm</li>
  <ol>
  <li class="ql-indent-3"> 대부분의 아키텍쳐가 이를 활용하지만 트랜스포머가 특히 도움받음</li></ol></ol></ol>
  <li> 키와 값 “Keys” and “Values”</li>
  <ol>
  <li class="ql-indent-1"> 아래에 각각 u와 v로 표기함. 요새 대부분 어텐션 소프트맥스를 표현할때 인풋 표현을 이와 같이 둘로 나누어 함.&nbsp;</li>
  <li class="ql-indent-1"> 키는 소프트맥스 가중치를 찾는데 사용. 값은 아웃풋 계산에 사용.</li>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcvWAVf8ijLtA4fPQY86ZQ2ediyv2JXIaq7hSDY_4cWcLiInvNCtHFQnXlIfb8kfYya46ilmUWPyy8aMBpeBNv3eN7ZY2n98yqA_9U7S0y70Sk8Bd2VeClQirq05uLdhOm0Vkq6D1fnWYYtgjr1Jy6ekrI?key=80SjqRecUP0TcEWfrVrriw" height="332" width="602">
</p></ol>
  <li> 셀프 어텐션 (Multi-query hidden-state propagation (“self-attention”))</li>
  <ol>
  <li class="ql-indent-1"> 앞서 다층 어텐션이 어떻게 작동하는지 살펴봤음. 셀프어텐션은 인풋의 크기가 커짐에 따라 Controller state의 크기가 커짐.&nbsp;</li>
  <li class="ql-indent-1"> 각 인풋에는 controller state가 있음. (u_j) 각 controller state는 소프트맥스 어텐션으로 업데이트됨.&nbsp;</li>
  </ol>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfDXIaB5w0-m6J49ADvpMB-642i7Dgm8rCpODM2XiDVUbwTLVMzh8g6aex6rXCeskdtG0NVAPYXMrYrMiVqsfdGSZpeyNb2S8VH7k497M2qZhqJrOZ8ZWa8yxgIsENbCWYLC5BXXpoPtlmd5kU1rK-vYr8?key=80SjqRecUP0TcEWfrVrriw" height="215" width="602">
</p>
  <li> 멀티-헤드 어텐션 (Multi-head attention)</li>
  <ol>
  <li class="ql-indent-1"> 각기 다른 가중치 행렬을 갖고 같은 데이터에서 같은 방식으로 훈련된 여럿의 어텐션 ‘헤드’를 합침.&nbsp;</li>
  <li class="ql-indent-1"> 총 L개의 어텐션 헤드는 모두 각 토큰에 대해 값을 내놓음. 이 값은 훈련된 파라미터에 곱해진 뒤 서로 더해짐.&nbsp;</li>
  <li class="ql-indent-1"> 아래 그림에서 G는 투영(projection), F는 완전연결. 각 점들은 feature dimension임.&nbsp;</li>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcZ_nmmJdw9p55CrUG9peMAX9CDPJlOReIPovwNRp6OVvwhz__lEQPpjQcYI_VGKZKNH-OSy1WADtvoU6d8KeSFR5NlCVqhxJN-fA36u3zeth3s2tu5TiKvyw65IN9VL8pmgCU5yP0fpQPJodDoeovcJA?key=80SjqRecUP0TcEWfrVrriw" height="295" width="602">
</p>
<p>
  <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfKVaIOR8K3Is_JQR-QJnZdM3L_cJWFDaPev8eBYnfssK9AB7Bmy0YB7aPRMZfxjUKjDNvOg905tLzDrW8LtPJ6ZyBv8lWXSoUkvy8u9LRokr8IIg1_o2q-ZkP1lid3rEH7QkH8EEx_BCCBBwEjTiavG_Q?key=80SjqRecUP0TcEWfrVrriw" height="309" width="602">
</p></ol>
  <li> Residual connections, LayerNorm : 앞서 논의되었으므로 자세한 설명은 생략하나, 이 기법이 고안됨으로서 트랜스포머 모델의 훈련이 가능해졌음.</li>
<p>
  <br>
</p>
  <li> 트랜스포머와 텍스트</li>
  <ol>
  <li class="ql-indent-1"> 트랜스포머는 벡터(혹은 그래프)의 세트에 대해 작동하나, 처음 소개될땐 텍스트 관련으로 소개됨.&nbsp;</li>
  <li class="ql-indent-1"> 텍스트에 대한 트랜스포머의 특기 일부</li>
  <ol>
  <li class="ql-indent-2"> 텍스트에서 토큰의 위치(location)에 따라 위치(position) 인코딩</li>
  <li class="ql-indent-2"> 언어 모델 관련 : “causal attention”</li>
  <li class="ql-indent-2"> 훈련 코드가 각 토큰에 대해 동시에 예측을 출력함 (그리고 동시에 각 토큰에 대해 그래디언트를 계산) =&gt; 훈련 속도가 전체 문맥량만큼 빨라짐</li>
  </ol>
</ol></ol>
<p>
  <br>
</p>
</html>