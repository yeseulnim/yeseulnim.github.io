조지아텍 온라인 석사과정 CS7647 '딥 러닝' 16강 필기 내용

[전체 필기 링크 (구글독스)](https://docs.google.com/document/d/1_xd0n3O7GMBT9WNWLzyCKq7-PMLgz2GzvYObZuGAKfo/edit?usp=sharing)

<html>
<h3>
  <strong style="background-color: transparent; color: rgb(67, 67, 67);">Lesson 16. 고급 토픽 : 페이스북에서의 번역 (Advanced Topics: Translation at Facebook)</strong>
</h3>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">*Automated Speech Recognition(ASR)은 필기 생략</span>
</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">1. 페이스북에서의 번역 (Translation at Facebook)</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 번역이 중요한 이유</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">번역은 사람들을 연결해 준다&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">페이스북(현 메타)은 1일 60억건 이상의 번역을 수행한다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 페이스북 번역 목표</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">모두가 페이스북을 각자의 언어로 이해하도록 한다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 어떻게?</span>
</p>
<ol>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">언어 인식 모듈: 게시물의 언어가 특정 언어일 가능성에 점수를 매긴다 (예: 터키어 0.99)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">사용자 언어 예상 모듈 : 사용자가 이해하는 언어가 특정 언어일 가능성에 점수를 매긴다. 사용자가 게시물에서 주로 사용한 언어 등에 기반한다. (예: 영어 0.99)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">번역 품질에 대한 확신이 높을 경우 자동 번역, 그 외의 경우에는 번역 버튼을 제공한다</span>
  </li>
</ol>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">2. 번역 도전과제 : 자료 부족 (Translation challenges: Low resource)</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 자료 부족 현상 :&nbsp;</span>
</p>
<ol>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">‘소셜 네트워크’라는 페이스북/인스타의 특성상 발생하는 현상</span>
  </li>
</ol>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">짧은 텍스트</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">노이즈가 많은 텍스트</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">실수가 많이 반영된 텍스트</span>
  </li>
</ul>
<ol>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">전세계를 대상으로 서비스하기 때문에 발생하는 현상</span>
  </li>
</ol>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">다양한 소수 언어에 대해 충분한 훈련 데이터가 부족함</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 소수 언어 문제</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">앞서 소개한 NMT 번역 시스템은 자료가 많은 언어에 대해서는 잘 작동한다 (영어, 불어 등)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">하지만 자료가 적은 언어는?</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">“NMT 시스템은 자료량에 대비해 가파른 학습곡선을 갖고있다. 그래서 자료 부족시 품질이 떨어지고, 자료가 많을 경우 품질이 상승한다.”&nbsp; - Koehn &amp; Knowles (2017)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">가장 자료가 많은 언어 5개에 대해선 훈련에 쓸 수 있는 예시 문장이 10억개가 넘지만, 200번째로 많이 쓰이는 언어의 경우 문장이 1만개 가량밖에 되지 않는다.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">전 세계적으로 6천여개의 언어가 있지만 현재 200개조차 학습시키기 어렵다.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 다른 문제</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">언어 유사성 문제 : 언어적으로 유사한 언어가 있는가 하면 멀리 떨어진 언어도 있음</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">도메인 :언어&nbsp; 데이터가 있더라도 페북에서 필요로 하는 분야의 데이터가 아닐 수 있음.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">평가 : 훈련 외에도, 테스트에 쓸 데이터가 부족함</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">4) 평가 문제 해결 : flores</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">강력한 벤치마크 세트가 필요했음.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">이를 위해 영어와 유사성이 적은 언어인 네팔어, 신할라어 에 대해 영문 번역 평가 자료셋을 구축.</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">과정 : 오픈소스 문서를 선택. 번역가 번역 -&gt; 자동 체크 2회 반복. 최종적으로 사람이 체크.&nbsp;</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">믿을만한 세트가 구성되면 이제 다언어 훈련이 가능함.&nbsp;</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">자료량이 많은 언어와 자료량이 적은 언어가 유사할 경우 전이학습 (transfer learning) 가능. (예: 우크라이나어 / 벨라루스어)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">5) 역번역(backtranslation)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">자료가 많은 언어에 대해선 매우 효과있음</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">자료가 부족한 언어에 대해선 적용 어려움</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">따라서 재귀적 역번역 (iterative backtranslation) 적용 (semi-supervised system)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">정방향/역방향 시스템을 병렬 데이터에 훈련시킴</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">6) 언어중립적 문장표현법 (LASR: Language Agnostic Sentence Representations)</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">weak supervision을 통해 추가적 훈련 데이터를 생성</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">방법: 인코더에서 언어특징적 요소들을 제거 -&gt; 다언어공간에 언어를 임베딩할수 있는 인코더.&nbsp;</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">7) 웹-스케일 마이닝을 통한 코포라 생성 : WikiMatrix, CCMatrix</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">이 모든 전략을 적용했을 때 그럭저럭 쓸만한 번역물을 만들 수 있음.&nbsp;</span>
</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">3. 번역 품질 다시 생각하기 (Rethinking Translation Quality)</strong>
</p>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">1) 번역 품질은 선형이 아니다.&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">목표: 사람레벨 번역은 아니더라도, 이해 가능한 좋은 번역을 제공하기</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">문제: 1,2개의 실수만 있어도 번역 품질이 끔찍한 품질로 바뀔 수 있음</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">2) 어떤 문제들이 있을까?&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">고유명사 번역 오류</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">대명사 번역 오류 (예: he,she -&gt; it)</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">부적절한 비속어 반영</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">어색한 번역</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">폭력적 단어 발생 (예: ‘good morning’ -&gt; ‘attack them’ 번역 오류로 실제 체포까지 발생)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent; color: rgb(0, 0, 0);">3) 발전방향 : 사용자 경험에 중심을 둔 번역</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">위의 재앙적 이슈들을 인식하는 번역 시스템</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent; color: rgb(0, 0, 0);">예) 비속어 감지시 사용자에게 경고문을 함께 보여줌</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">중요 실수여부를 반영하는 품질 측정 기준</span>
  </li>
  <li>
    <span style="background-color: transparent; color: rgb(0, 0, 0);">보다 투명하고 조정가능한 AI시스템</span>
  </li>
</ul>
<p>
  <br>
  </p>

</html>
