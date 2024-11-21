---
layout: post
title:  "CS7643 딥러닝 기말 프로젝트 후기 - 데이터의 중요성"
date:   2024-11-21 12:45:23 +0900
categories: 공부
tags : [딥러닝,공부]
---

<html>
<p>(앞서 올린 <a href="https://yeseulnim.github.io/2024-07-18-diary-dl-hap/" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">딥러닝 프로젝트 하소연</a>의 후기) </p>
<p>결론적으로 과제는 잘 마무리되었다! 해결 과정에서 흥미로운 요소들이 있었기에 글로 남긴다.</p>
<p>
  <br>
</p>
<p>앞서 나의 고민을 요약해 보자면 이렇다.</p>
<p>
  <br>
</p>
<p>운전자의 ‘졸림’ 상태와 ‘안졸림’ 상태를 사진으로 구분하기 위한 데이터셋이 있다.&nbsp;</p>
<p>(캐글 링크 : <a href="https://www.kaggle.com/datasets/ismailnasri20/driver-drowsiness-dataset-ddd" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">Driver Drowsiness Dataset (DDD)</a>) </p>
<p>이 데이터셋은 여러 사람들의 ‘졸린’ 상태와 ‘안졸린’ 상태 사진을 모아놓은 것이다.</p>
<p>이 데이터셋에는 유사한 사진이 여러 장씩 있는데, 이유는 모두 영상에서 캡쳐한 이미지들이기 때문이다. 즉 이미지는 몇 만 개지만 총 40여개의 영상에서 캡쳐되었기 때문에 수백개의 유사한 이미지들을 약 40세트 모아놓은 자료라고 할 수 있다.</p>
<p>
  <br>
</p>
<p>그렇다면 이 데이터를 갖고 ‘졸린’상태와 ‘안졸린’상태인 사람을 구분하도록 모델을 훈련시켰을 때, 이 모델은 무엇을 학습하게 되는가?</p>
<p>단지 ‘졸린’상태에 사용된 인물과 ‘안졸린’상태에 사용된 인물들의 얼굴 형태의 차이를 학습하게 될 수도 있지 않는가?</p>
<p>
  <br>
</p>
<p>이를 막기 위해서는 한 영상의 이미지가 훈련 데이터와 검증 데이터에 모두 사용되지 않도록 해야 할 것이다.&nbsp;</p>
<p>그런데 그렇게 하니 도저히 논문 원저자들이 얻었다는 좋은 결과를 재현할 수가 없었다.</p>
<p>무엇이 문제일까?</p>
<p>
  <br>
</p>
<p>-&gt; 결론적으로, 나는 <strong style="background-color: transparent; color: rgb(0, 0, 0);">틀렸지만 맞았다. </strong>아래에 자세히 설명하겠다.&nbsp; </p>
<p>
  <br>
</p>
<h2>1. 나의 오류</h2>
<p>
  <br>
</p>
<p>일단 내가 틀린 부분은, 이 데이터셋이 40여명의 인물을 각각 촬영한 데이터셋이 아니었단 점이다.&nbsp;</p>
<p>
  <br>
</p>
<p>이 데이터셋은 20여명의 인물들이 각각 ‘졸린’ 상태와 ‘안졸린’ 상태에서 찍은 2개의 영상 (즉 총 40여개 영상)에서 캡쳐한 것이었다.&nbsp;</p>
<p>따라서 이론상으로는 한 인물에 대해 각각 ‘졸린’상태와 ‘안졸린’상태 이미지가 모두 존재할 것이다!</p>
<p>그러므로 졸린 상태 구분 대신 인물의 얼굴을 학습하지 않을까 하는 우려는 할 필요가 없어야 한다.</p>
<p>
  <br>
</p>
<p>그런데 그럼 나는 왜 이 데이터셋을 오해했는가?</p>
<p>기본적인 데이터 살펴보기조차 하지 않았다는 것인가?</p>
<p>변명하자면 아니다. 나는 데이터셋 첫 부분의 인물들을 자세히 살펴보았다.&nbsp;</p>
<p>
  <br>
</p>
<p>이 데이터셋에서 ‘졸린’ 데이터와 ‘안졸린’ 데이터의 첫 부분에 있는 인물의 사진은 아래와 같다.&nbsp;</p>

<p>
  <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeifzAgbklGgm3ssqLRFjLdzDQsTc1H3eiI573SRDOUW05iTKTz8kIxqT_eKXTECqqftHtFtj3BYrZOZ8ixhiVlAi8Q0PefdlxV4HEULgt2Ey4GNH1MtMGf9qtkxMyNPxWT14o4?key=cCr1rTJTcBNYP_SeXPmQ2oj3" height="239" width="376">
</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">위 두 장이 같은 인물의 사진이다.&nbsp;</strong>
</p>
<p>
  <br>
</p>
<p>두 사진 (즉 두 영상)이 너무나 다른 환경에서 촬영되어, 나에겐 마치 다른 사람인 것 처럼 보였던 것이다.&nbsp;</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<h2>2. 잘못 구성된 데이터</h2>
<p>
  <br>
</p>
<p>그렇다면 여기서 의문이 든다.</p>
<p>
  <br>
</p>
<p>위 두 사진 (및 동일한 영상을 캡쳐한 유사 이미지 수백장)을 갖고 ‘졸린’얼굴과 ‘안졸린’ 얼굴을 학습하라고 명령했을때, 모델은 무엇을 학습할까?</p>
<p>졸음의 흔적을 학습할까?</p>
<p>아니면 이 두 영상을 쉽게 구분짓게 만드는 수많은 다른 요소들 - 얼굴 각도, 안경, 조명 - 을 학습할까?</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">당연히 후자일 것이다!</strong>
</p>
<p>
  <br>
</p>
<p>이것이 이 논문의 저자들이 놓친 부분이다.&nbsp;</p>

<p>모범적인 환경에서라면, 모든 다른 요소들이 컨트롤된 상태로, 피실험자의 얼굴에 졸음의 흔적이 있는지 없는지만 차이가 나는 상태의 영상이 사용되었어야 한다.</p>
<p>그런데 이 실험에 사용된 영상은 피실험자들이 직접 집에서 알아서 찍어온 영상들이었다.</p>
<p>그렇기에 각 영상에 담긴 화면각도, 조명 등 수많은 요소들에 차이가 나게 되었고, 이에 모델은 ‘졸린’상태와 ‘안졸린’상태의 구분법이 아닌 개별 영상들을 구분하는 방법을 학습하게 된 것이다!&nbsp;</p>

<p>그러니 알렉스넷과 같은 단순한 모델을 사용해도 좋은 결과가 나올 수 밖에 없다. 주어진 사진에 대해, 졸음 상태인지를 식별하는 것이 아니라, 지금까지 학습한 <em style="background-color: transparent; color: rgb(0, 0, 0);">모두 서로 다른 </em>영상 중 어느 영상에서 캡쳐된 이미지인지를 식별하면 되는 과제가 되었기 때문이다!&nbsp; </p>
<p>
  <br>
</p>
<p>결과적으로 비록 전제에 오해가 있었지만, 나의 첫 문제제기가 옳았던 것이다!&nbsp;</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">과적합이 발생한 것이니 말이다!&nbsp;</strong>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<h2>3. 진정한 논문 재현을 위해</h2>
<p>
  <br>
</p>
<p>단순하게만 보면 우리의 논문 재현 과제는 쉽게 성공한 과제였다.&nbsp;</p>
<p>논문 저자들이 사용한 모델 재현에 모두 성공했고, 90% 후반대의 높은 정확도를 뽑아냈기 때문이다.</p>
<p>하지만 위에 설명했듯, 단순한 모델로도 높은 정확도가 얻어진 것은 데이터에 큰 문제가 있었기 때문이었다.&nbsp;</p>
<p>그렇다면 여기서 재현실험을 끝내서는 안되었다.</p>
<p>과적합 요인을 탐구하고 이를 해결해야 한다는 것이 나의 생각이었고, 다행히 팀원들도 이에 동의해 주었다.&nbsp;</p>
<p>
  <br>
</p>
<p>실험은 다음과 같이 진행했다.</p>
<p>
  <br>
</p>
<p>우선 우리의 의심대로 실제 과적합이 일어났는지 확인하기 위해 Saliency Map을 사용했다. Saliency Map은 학습이 완료된 모델에 대해 사용할 수 있는 도구로, 각 이미지를 판별하기 위해 모델이 이미지의 어떤 부분에 집중하는지 시각적으로 보여준다.</p>
<p>
  <br>
</p>
<p>과적합이 의심된 모델에 대한 Saliency Map은 아래와 같았다.&nbsp;</p>

<p>
  <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeejDWBosj31Z2ntR3_bkiwvy00RPpVwuJuyPyGcsmr6PT-zhczIGOA_NJVRx_S22i05HViEmVJyVOgulp1ns2l-g81oKlf4NS8uQnGYoSfOFOC2QhQ-uS3-QJSIGBPhwOQx9ga?key=cCr1rTJTcBNYP_SeXPmQ2oj3" height="217" width="400">
</p>
<p>
  <br>
</p>
<p>이를 보면 두 가지 사실을 알 수 있다.</p>
<p>
  <br>
</p>
<p>우선 모델은 주로 눈 부위에 집중하는데, 눈은 흔히 우리가 졸음을 시각적으로 판별할 때 기준이 되는 부위이기도 하다. 따라서 이 부분에 모델이 집중한다는 것은 좋은 신호로 보인다.</p>
<p>
  <br>
</p>
<p>하지만 모델은 사진의 다른 부위들에도 집중하고 있다. 1번째, 3번째 사진에서는 머리카락이나 얼굴의 형태, 2번째 및 4번째 사진에서는 옷가지와 수염에도 집중하며 인물의 전반적인 모습을 판별에 이용하는 것을 볼 수 있다.</p>
<p>
  <br>
</p>
<p>
  <strong style="background-color: transparent; color: rgb(0, 0, 0);">우리는 이를 과적합이 일어났다는 신호로 해석하였다.&nbsp;</strong>
</p>

<p>
  <br>
</p>
<p>
  <br>
</p>
<p>다음으로 우리는 과적합을 극복하기 위해 훈련 데이터와 검증 데이터, 테스트 테이터를 재구분하였다.</p>
<p>
  <br>
</p>
<p>40여개의 영상에 대해, 한 영상에 사용된 자료가 훈련 데이터, 검증 데이터, 테스트 데이터 중 한 곳에만 들어있도록 하였다. 즉 영상의 특성을 학습해서 좋은 검증결과를 얻는 것이 불가능하도록 만든 것이다.&nbsp;</p>
<p>
  <br>
</p>
<p>다만 이렇게 할 경우, 모델은 완전히 처음 보는 사진에 대해 사진 속 인물의 졸음 여부를 판별해야 하는데, 이를 위해 우선 인물의 눈코입이 어디인지부터 판별해야 하는 등 과제가 늘어나게 된다.</p>
<p>모델의 짐을 덜어주기 위해 학습 데이터 다양화를 시도하였다. Data Augmentation을 통해 한정된 데이터라는 한계를 극복하고자 노력하였다.&nbsp;</p>
<p>
  <br>
</p>
<p>이러한 노력에도 불구하고, 실험 결과, Accuracy는 50%대로 크게 떨어졌다. 이조차도 일정하지 않았으며 학습과정에서 epoch에 따라 30%대, 70%대 등 Accuracy가 크게 요동치는 것을 볼 수 있었다.</p>
<p>다양성이 부족한 데이터의 한계를 Data Augmentation만으로 극복하는 데에는 무리가 있었던 것이다.</p>
<p>
  <br>
</p>
<p>재구분한 데이터를 통해 학습한 모델에 대한 Saliency Map 결과는 아래와 같다. 제대로 학습하지 못했음을 볼 수 있다.&nbsp;</p>

<p>
  <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeD52eStDhP0Spi0zgPBOI--9UgdEYJnRsVi03gUkVErc3h2x2nZtx4NamZScA7CiBHYLrgoOHqsPI6An2OuyiaVh2iJmERJ0TDiZFmDji1EMHRusSuesbekUApKPF_TQoZuEY?key=cCr1rTJTcBNYP_SeXPmQ2oj3" height="212" width="390">
</p>

<p>
  <br>
</p>
<h2>4.결론</h2>
<p>
  <br>
</p>
<p>우리는 이와 같은 연구사항을 보고서에 자세히 작성하였다. 특히 과적합의 발생과 그 원인에 대해 자세히 작성하였는데, 그 부분을 좋게 평가받은 것인지 높은 점수를 받게 되었다. (휴!)&nbsp;</p>
<p>
  <br>
</p>
<p>이번 프로젝트에서 정말 절실히 느낀 점은 <strong style="background-color: transparent; color: rgb(0, 0, 0);"> 잘 준비된 데이터가 그 무엇보다도 중요하다</strong>는 것이다. </p>

<p>학습에 걸맞지 않는 데이터를 사용한다면 모델링을 아무리 잘 해도 왜곡된 결과가 나타날 수 밖에 없다!</p>
<p>
  <br>
</p>
</html>