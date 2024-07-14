---
layout: post
title:  "Lesson 17. 강화학습 (Reinforcement Learning)"
date:   2024-07-14 12:45:23 +0900
categories: 공부
tags : [딥러닝,필기,공부]
---

조지아텍 온라인 석사과정 CS7647 '딥 러닝' Lesson 17 필기 내용

[전체 필기 링크 (구글독스)](https://docs.google.com/document/d/1_xd0n3O7GMBT9WNWLzyCKq7-PMLgz2GzvYObZuGAKfo/edit?usp=sharing)


* 워낙 방대한 내용을 빠르게 다루고 있다 보니, 강의만으로는 이해가 어려운 부분이 많았다.
이에 [David Silver의 구글 딥마인드 강의 시리즈](https://www.youtube.com/watch?v=2pWv7GOvuf0)를 참고했다. 


<html>
<h3>
  <strong style="background-color: transparent; color: rgb(67, 67, 67);">Lesson 17. 강화학습 (Reinforcement Learning)</strong>
</h3>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">1. 강화학습 소개</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 강화학습 소개&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">과업 : 연속적 의사결정</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">‘보상(Reward)’ 형식으로 평가 피드백 수령</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 강화학습의 개념들</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Agent : 의사결정의 주체</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Environment&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">State : Agent에게 주어지는 Stimulus, Situation. 예: 로봇의 시각적 인풋.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Action : Agent가 Environment에 대해 취하는 행동.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Reward : Environment로부터 Agent에게 주어지는 보상. Gain, Payoff, Cost로 나뉨. (즉 비용도 Reward에 포함됨)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Evaluative Feedback (평가 피드백) :&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">action을 취하고 보상을 받음 (negative 즉 음의 보상도 있음)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">지도학습에서와 달리, “올바른”행동에 대한 지도가 없음</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Sequential Decisions (연속적 의사결정) :&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">연속된 state에 대해 action을 계획하고 취함</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">보상이 지연될 수도 있음. 그러므로 장기적인 누적 보상을 고려한 최적화, 즉 장기 계획이 필요함.</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 강화학습의 도전과제</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">평가 피드백 : 올바른 action을 찾을 때 까지 trial-and-error 방식으로 가능한 모든 action을 검토해야 함.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">피드백 지연 : action이 즉각적인 보상으로 이어지지 않을 수 있음.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">유동성 (Non-stationarity) : Policy가 변경되면 이미 방문한 state에 대한 데이터 분포 또한 변경됨</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">온라인 데이터는 모두 흘러가는 데이터임. 시간도 마찬가지임. Agent는 해당 state를 단 한번만 보게 될 수 있음. 과거의 실수에서 학습하기가 어려움.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 강화학습 API</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Agent는 각 시간 스텝 t마다 :&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">관찰내역 o_t를 수령함</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">액션 a_t를 실행함</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Environment는 각 시간 스텝 t마다:</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">액션 a_t를 수령함</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">관찰내역 o_t+1 을 발산함</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">보상 r_t+1을 발산함. (스칼라값)</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) 예시 : 아타리 게임 플레이하는 AI</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">목표 : 가장 높은 점수로 게임을 끝내라</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">State : 게임 상태에 대한 raw pixel input</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Action : 게임 조작 (예: 위아래 왼오른)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Reward : 각 시간 스텝 별 점수</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">2.마르코프 결정 과정 (Markov Decision Process)</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) MDP 소개</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">MDP는 강화학습 기저에 깔린 이론적 프레임워크이다.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">정의 : 튜플 (S, A, R, T, γ)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">S: 가능한 State의 집합</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">A: 가능한 Action의 집합</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">R(s,a,s’): Reward의 분포</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">T(s,a,s’): Transition 확률분포. p(s’ | s,a)라고도 씀</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">γ: 할인 계수 (Discount Factor)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">순서 : … s_t, a_t, r_t+1, s_t+1, a_t+1, r_t+2, s_t+2 …&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">마르코프 속성: 현 state가 Environment의 state를 온전히 규정한다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">전제 : 가장 최근의 관측내용이 기존의 역사를 모두 함축하고 있다</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcIfxx4znfkKurzaxn1mB88CZHtkKD-Dkc5RZvQLI3YalAJqgQW_GS1s6Xf-yUYwtiyf0RrTCPaHQTAoWnHyD5dbGodYJzaUdmNBEdLvFovZM9kMQf6D_1ptNlpkDmzl0giOFp9au5h35DNkJOOc7FVsXs?key=80SjqRecUP0TcEWfrVrriw" height="51" width="1050">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 강화학습에서의 MDP</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">강화학습에서 우리는 기저에 MDP가 깔려있다고 가정한다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">이 MDP에서 R과 T는 미지의 속성이다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">그래서 피드백이 주어지며, trial-and-error 가 필수적이다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">다만, 이 강의에서는 우리가 R과 T를 안다고 가정하고 MDP를 푸는 알고리즘, 즉 최적의 Policy를 찾는 방법을 알아본다. 아래 항목들이 전제된다.&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Rewards : 모든 상태에서의 보상 알고있음. 평가핏백 없음</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Transition : Environment가 어떻게 작동하는지, 즉 모든 transition을 완전히 알고 있음</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 예시 : 그리드에서의 MDP</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Environment : 2d 그리드&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">State : Agent(세모)의 2d 좌표</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Action : 동서남북</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Reward : 우측상단에 기재된 +1, -1&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">복잡요소 : Agent가 동작의 왼쪽/오른쪽으로 drift할 확률 20% 존재</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">Policy를 어떻게 짤 수 있을까?</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">한 가지 방법은 맵과 동일한 2d행렬을 구현하는 것이다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcWRbY-dH9OPro_LZgs7rihlNUVEQPLfpuSb4yh6NTNK_y_kRKdh6ZBzZLifnX3b7B4JwdIYsz3T8neAEHM6-UHA2XmPSEV6HWRDQJvRwUiNiVNWC9yKksgYF6FRn_7o7ZkNbH-cwPg_ECyCCppSeypfmM?key=80SjqRecUP0TcEWfrVrriw" height="499" width="480">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 최적의 Policy 찾기</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Policy : State -&gt; Action 매핑.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Deterministic : π(s) = a</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Stochastic : π(a|s) = P(A_t = a | S_t = s)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">어떤 Policy가 좋은 Policy인가? 가까운 reward를 최대화하는것? 모든 미래의 reward를 동일하게 합하는 것?</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">답은 ‘할인된 미래 보상의 총합’이다.</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">policy에 대한 할인계수 * 보상의 총합의 기대값이 최대인 policy.</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXd4lncMv6BU-0bR6I1Hcu8OPdbI9fr6ni-4UcuyEbMMQylmbGlcx3RliBw4cay3Ly96nLQnCLiBIUfvPNmIJB8-Nd9S6XISyjUzA7znwJFRdR14lXfSx06piu6M7i9dKQyYLJeUu_a-WzG7tbop18F3ruk?key=80SjqRecUP0TcEWfrVrriw" height="482" width="908">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) 최적 Policy 예시&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">그리드 맵을 다시 살펴보자. 모든 non-absorbing state에 대해 reward 값을 설정해 주자.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfcaHAfCjFinWUbrXhKSOvA2RtoFQE41ty5esOOrH7pSw1c5GWV8wosYNppPf5hmjnQEUb4PqBCdj01njN7ff8gvmM-wb4837eLGp1x1yYElT1dULb766whNlxQ8oWiA7Dnm4-OsERJJpQmmRWnfA510w?key=80SjqRecUP0TcEWfrVrriw" height="532" width="1082">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">6) 가치 함수 (Value Function)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">가치 함수 : 미래 보상의 합에 대한 예측</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">State 가치함수 : V-함수. V : S -&gt; R</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이 State의 가치는?</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이 State에서 내가 이길/질 가능성은?</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">State-Action 가치함수 : Q-함수. Q : S*A -&gt; R</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이 State-Action 쌍의 가치는?</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이 State에서 이 Action이 내 미래에 미치는 영향은?</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXc_CoDyy-GUcmTm-hRi_bCCqW5r_aQewmUo-5trOsZN4fTV_jLkrdu0Hiq0NrsBORCvusRZ4K6upmkgXTFxYyET-8JDRUuUdczixQ_bsEE8tstcvbdFF2hbLCKgRp3CWoqHveHON0mEJzh84PLfjRWcTxg?key=80SjqRecUP0TcEWfrVrriw" height="421" width="1033">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfxBNgeFVt9FvKqWGDn-VQM2hnIhLXD9tgZjaQHxZ3UiCV1Ob0MBcb-fWqWVMgi1ylo7Fg43zLRi7JVhUjYlpl3PPgPNYN4WtC7refOh9VFJnXZKnBgzDsOOARiX3ht2SFp-MDXi_sSKMtJO_1nXPv2dWo?key=80SjqRecUP0TcEWfrVrriw" height="438" width="1047">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">3. MDP 해결 알고리즘</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) Recursive Bellman Expansion</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Q의 정의에 Recursive Bellman expansion을 적용하면 Q와 V를 아래와 같이 바꿀 수 있다.</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcc7CSkk3U1z-SJPRKQjaSGGKWdrMY2O6BRsteAuExo7p5t0BpC7BfFBK5bebf7Je5Vi0m8iQzAbEHIu7tyNDlw-268eYYAZH2infiRRXnkakwwD8xXT8mcGHfLd2e-OHx0KTzt5F5oYSrcnCzPIBlkOQ?key=80SjqRecUP0TcEWfrVrriw" height="412" width="750">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이는 Value Iteration이라는 dynamic programming algorithm의 근원이 된다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) Value Iteration&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">알고리즘 단계:</span>
  </li>
</ul>
<ol>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">모든 State의 값을 초기화한다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Converge되지 않은 동안 모든 State에 대해 :&nbsp;</span>
  </li>
</ol>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXc3lRe368MCNs3IcGXnDJnRsOyt5DXIU28qP3hMk59SkfaqPMyNNeGvAxbSNtOKcMJkTbo7w4xfRkaFbKYWXhGA1Q17IQs5iU5Mo4GoVJkWK4NucW15d7ZuGMxrcdfFTyNbF9mJR8hHwA6nuwt4XOd9iA?key=80SjqRecUP0TcEWfrVrriw" height="90" width="698">
  </span>
</p>
<ol>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Convergence까지 반복한다. (Convergence = 값 변화 없음)</span>
  </li>
</ol>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Time complexity : O( |S|^2 |A| )</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) Q-Iteration</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfutgz2m2k6LAjD2oyFnCfl22ZFsqhmblOs4x0VvXUNz0oL3fAsWrPYmSXDFzW_zeIYmjHAV1ygTg9pTqeHMuyqGx76pKGvWyDDbIDqqQvU_pXpAXHebistM7cexraoD28n4c6qi9aW7Lw9B3YFCfPy7w?key=80SjqRecUP0TcEWfrVrriw" height="132" width="1062">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">Value iteration과 거의 같지만 state뿐만 아니라 action에 대해서도 반복된다.&nbsp;</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) Policy Iteration&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">랜덤한 policy π_0에서 시작하여 점차 개선해나간다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">2개 단계를 반복한다.</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Policy Evaluation : V^π 계산 (Value Iteration과 유사)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Policy Refinement : 그리디 방식으로, V^π에 따라 다음 state에서의 action을 변경함&nbsp;&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdVkGhfMQ6VFJNUZujLgPQ_SbIZl-Lj67dGx6-XgBughKucPvgd-x2uZmecimLPdpNgJ6QOeaGvFq8qjh_I8sRVKTe-4_g-N7Zq7-00XaQPU24wV3GmUzYw66u-4UWiYVSIBS2BdB6mHGnP73GTXMKDBpk?key=80SjqRecUP0TcEWfrVrriw" height="103" width="810">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">V^π_i 보다 π_i의 converge속도가 더 빠를 때가 많다. 그래서 policy iteration을 하는 것이다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) Space/Time complexity</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">앞서 봤듯 Value iteration의 time complexity가 매우 크다. 그래서 복잡한 상황이 될 수록 알고리즘을 조정할 필요가 있다.&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">4. Deep Q-Learning</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">매우 흔히 사용되는 Value 기반의 강화학습 방식이다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 예시: 아타리 게임&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">알고리즘은 2개의 작업을 하는 중이다.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Policy Refinement</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">수집한 데이터를 통해 Deep-Q Network를 업데이트, 보다 나은 전략을 알아냄. (예: 칼럼별로 적을 없애기)</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) Deep Q-Learning</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">요약 : 데이터로부터, 파라미터를 받는 Q-함수를 학습한다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">가장 간단한 선형함수 형태:&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">
      <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXf_6kFk_Z0v2TR4e_7dp3_Ap2wQraqlUT-nf9e8zjgFd-CTGB7VHQqmx_pDc2yMsHJ4ubo1LX2n0VAFjQ2cdomRz2vPu_zJxewkGbjXjjd9roDuxQ97ezUvFZFIYUWuBL0iE8OX0qef_WAbh-liqQprq_0?key=80SjqRecUP0TcEWfrVrriw" height="60" width="393">
    </span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">혹은 Deep 한 신경망 (Deep Q-Network : Q(s,a; θ))도 있다</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">실제로 잘 작동한다</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">RGB 이미지를 인풋으로 받을 수 있다 (합성곱 신경망)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXelzlJS83xd_EXYjBiHEeKWcsx1BmOSxfYJCFGM8Ie5xB9Gg65lm5eJKXBNpnIVctFwRY-IGNF-G41TgQWgY_Kl_ynAVly9KxgIPyQ6I95vllSjjwSS2FFHzRFa8PgjIAgv_PfsgQiN0c3mXknUETgO4Qo?key=80SjqRecUP0TcEWfrVrriw" height="310" width="440">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">손실함수는 아래와 같다. 다만, 실 적용시에는 안정성을 위해 두 단계로 나눈다.&nbsp;</span>
  </li>
</ul>
<ol>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Q_old를 그대로 두고 Q_new 의 파라미터들을 갱신한다</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">정기적으로 Q_old를 Q_new 값으로 세팅한다.&nbsp;</span>
  </li>
</ol>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdwudNlIfl4pwXYit2LAUzL6YTkheb3vlwP7nTpnJcVVrF-pMxcDhTGmWunIm2E7IhGj5paFV0XEL0hmL1DC6HCH5hCDS2pFEaHFify2I0Mijy3-KBczyJnv-dN8ztZYkhv1SAL8-C-xys_99LX6lPbhWY?key=80SjqRecUP0TcEWfrVrriw" height="187" width="899">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">실제 적용시 미니배치를 사용한다.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Forward Pass :&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXel206Z2pk5oFrxnMduUhMIxmRb26YBBZXOADcUdwiOev4OCZOlbbZVk5m_d7cvzcWa81tmI9YDSUOvrrPA8vkjmCb3MEA7tPtiM5Rib5q6XYq8gSsG450SLe-Y7RTJdEH4cKCOMipGiZZSu2dPa909VQ?key=80SjqRecUP0TcEWfrVrriw" height="64" width="363">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">손실함수 : 배치 평균 사용</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Backward Pass : Q_new parameters 에 대한 Loss의 derivative&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">고정 데이터셋에 대해 MSE 손실은 최적화될 수 있다. (Fitted Q-Iteration 알고리즘)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">하지만 ‘어떻게 경험/데이터를 축적할 것인가?’의 문제는 아직 해결되지 않았다. 이게 강화학습의 가장 어려운 부분이다!&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 어떻게 경험을 쌓을 것인가?</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">예시: 데이터 수집 정책 “π_수집” -&gt; Environment -&gt; Data -&gt; 훈련 -&gt; “π_훈련” -&gt;&nbsp; “π_수집” 갱신</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">문제점 1. Exploration vs Exploitation : Exploration 부분이 없음</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">문제점 2. 보상을 받을법한 방향으로만 움직인 데이터이므로 독립적이지 않고 correlation 이 높은 데이터임</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) Exploration 문제</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">단순 그리디 알고리즘을 구현할 시 Exploration 측면이 없음</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">대안 : ε-그리디 알고리즘&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcIb0qP2u-GyqcnHhElbH3Cu3uLCJRWn-HPaWkkQQvkdFmUHtl9Ydps0Sb_nDxP6KAcT1VXcqkRqYNKDg3ZKoTZQE3JkXB9OQcvBHd1KqMonXDGEDsZFr_RoAY2LO-KZImDJz1tUrcWAGZOtrbhlJYKwQ?key=80SjqRecUP0TcEWfrVrriw" height="111" width="704">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) Correlation 문제</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Correlation이 높은 데이터들만 축적되어 학습이 비효율적임.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">현재 Q-network의 파라미터가 다음 훈련 샘플을 결정지으므로 feedback loop에 빠질 수 있음.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">예: 아래 예시에서 모든 훈련 샘플이 일단 우측으로 향하게 되어 local minima에 빠질 수 있음.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdMds0ESYBuZbRAUufH73AFG3SxZTymHo8bFCvhThpfV_99F1HHuogNjaMMdcQX69MXJBCyz_-rt3RG-EQo2Sz_0NqfRh7W0rTTEntKNas1Z1xZoixxiWWm4DTOkXKQ-gfVsErL2vKNk2CkfbRGzm1EwCs?key=80SjqRecUP0TcEWfrVrriw" height="138" width="898">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">6) 해결책 : Experience Replay&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Replay buffer에 transition을 저장</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">경험이 쌓일때마다 replay buffer를 업데이트</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Q-network는 리플레이 메모리에서 추출한 랜덤한 transition 미니배치로 훈련시킴. (비연속적인 샘플)&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">버퍼가 클수록 correlation이 낮아짐.</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">지금까지 배운 내용을 종합하면 아타리 미니게임 논문에 사용된 알고리즘을 이해할 수 있다!&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfNvGuFmuj-I9I60IkSrvA4SRyf3oEOajer7kBTg85nCYXusJbPCmwsKPWB9-jsfch1cjyRvxXdAeKHYJmhrE0z7dP_vfWV_Kl2LKFOvZAILe9jmIuUETPiY7vBwFWtAXieD9xOpHSywZao9EGs1YONKLU?key=80SjqRecUP0TcEWfrVrriw" height="477" width="953">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">&nbsp;</span>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">5. Policy Gradients, Actor-Critic</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 파라미터를 받는 Policy&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">파라미터 목록 θ로 정의되는 Policy들 :&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeaf8Z1rVejlNZQz-Jw4JL5ZH_wJtft4sGAlP0x-deuL_virKqOx0CJ57SXr9xjTMbZzDIrLCHt5SSC8uK5A54thqiwC45aqW2UGA_JpOYbCRudusuG2-BMStlHkj3jkUDqgSCn2xj0aD8ss0ndvbqySEs?key=80SjqRecUP0TcEWfrVrriw" height="66" width="317">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">θ는 예를 들어 선형변환이나 딥 네트워크 등의 파라미터들일 수 있다</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">우리는 J(π)를 최대화하고자 한다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">* 여기서 감마는 1인것으로 처리한다.</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfVPsbhfuuHpY8Ao9kCTY0eWeWQIvaaBne7l5IbqPeD5Zv476_A4DPDwRnQjjWVEtZCbxhbQI_FAa48TpZX7hlFBgRZIBRUSvPkWF_zx58BANyP6wk0WjSqlCJ7H437JQ2T5es929va1fv2_Dl-dFyS9nM?key=80SjqRecUP0TcEWfrVrriw" height="128" width="438">
  </span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이제 최적의 Policy에 대한 공식을 아래와 같이 바꿔쓸 수 있다.</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXedVOzyN_OfSKUGXVrcvW2VOY09TVeclHV9GmBOBLqll4SwBDkJbO7yAfeUufLLAhkMOjUf0cT2mg6LxBrBbxCAREbUNfRef1QLXlEVy6bjw05pKqAhPVVkwuRJBV5skMvq1m9xgyxu3KtE2OkKUraIdeY?key=80SjqRecUP0TcEWfrVrriw" height="109" width="1030">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) Policy Gradient : 손실 함수</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">지도학습과 비교하면 아래와 같다.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeU3mgnv7UCpm5y4cTGcmhaSXlv9zgONWZWukgPjW9JQ7Ohy-ypCTfjR4ZFyCgWfwxq8VBFLgBwhgAugYYRx62Ke_YjV77CNd8dOXStrNnqav6pdgfpapDvah3LYx5-fnUBcRkJ8sCpcanukCCTE8SfmoE?key=80SjqRecUP0TcEWfrVrriw" height="523" width="987">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) REINFORCE 알고리즘</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">3단계로 진행된다</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Policy 실행 및 데이터 수집</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Policy gradient 계산</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Policy 갱신</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">그럼 Policy gradient는 어떻게 계산하는가?&nbsp;</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) Policy gradient 계산</span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXddWNPqNUE0jvEdUguUvZDCjUPzk-Ds8eN-NaxKv8vtSP2FqPa_ZXVnznq9pcVMgBJh87bWHOGgeLm3BW_M72BOsVz2yWeQpadvmJP0GRqG022p0v9iiZvgaJfq1IRQlmaop-F-Sk34HUA34Xma_eAh7yM?key=80SjqRecUP0TcEWfrVrriw" height="537" width="1111">
  </span>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeSw8Vag4wYFqE43z-biBnIxUts6LT1aocST9c_WzgT2LqVduOh9XgXuDRmIUjZktWonqwGaybi85jtSxUdfQCnRkcJ8n_9D30_cPT9EXwVAr8B7aw_IS-TL0y6HUFrXuI5b8oLhpCViC9MTpiK2z45xI8?key=80SjqRecUP0TcEWfrVrriw" height="483" width="1074">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) Policy Gradient의 단점</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">High Variance : 어떤 행동이 보상 증진으로 이어졌는지 정확한 파악이 어려워 high variance 나타남. 훈련 불안정.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">Variance 낮추기 : 보상으로부터, action과 무관한 baseline을 뺌.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXctJPlkjHuO8wyIU7_DHwvRQeIF90P_DP6IdLO4tdp46ZG3-NonopEGKMv1RwZ_g_HES82N3PIUwJZXmMVFm---7lKnDypW6UuYRKNUquuaewF0x_20N0JIVLIzvo2bUWmfD8_Pz7MWw2zcA6g9SIFzfiA?key=80SjqRecUP0TcEWfrVrriw" height="127" width="967">
  </span>
</p>
<p>
  <br>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이 Baseline을 무엇으로 하는지에 따라 알고리즘이 여러가지로 나뉨.</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">
    <img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeMDJh_AAUkdahb-IsUSGyBX32_ZXV6XWnBy-abDjIkT_naBzei_jSRYRUJ-tZ76JT5hLS1tPMqsNfNlUTCQVsTc94exoBzh2-09gxMIHLFeClBdEMon63--uCn_zYfefR811fHjnIJNL3NPzzHBa9ZNOQ?key=80SjqRecUP0TcEWfrVrriw" height="480" width="1040">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
</html>