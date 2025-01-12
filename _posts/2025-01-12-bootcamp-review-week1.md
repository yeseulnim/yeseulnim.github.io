---
layout: post
title:  "SK Networks Family AI Bootcamp 1주 정리"
date:   2025-01-12 12:45:23 +0900
categories: 공부
tags : [부트캠프]
---




<h1>
  <span style="background-color: transparent;">부트캠프 1주차 정리</span>
</h1>
<p>
  <span style="background-color: transparent;">&lt;한 일&gt;</span>
</p>
<p>
  <span style="background-color: transparent;">필요 프로그램 설치</span>
</p>
<p>
  <span style="background-color: transparent;">Python 초급 내용 복습</span>
</p>
<p>
  <br>
</p>
<h1>
  <span style="background-color: transparent;">1/7 화</span>
</h1>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">Python 설치</strong>
  </li>
</ol>
<p>
  <a href="https://www.python.org/downloads/" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">Download Python | Python.org</a>
</p>
<p>
  <span style="background-color: transparent;">*Add Path에 체크해줌</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXf6DN92IvOSYdSODDb6vRRbgznYd-IsFv012HLQfOqYPOGjmHB-lH4KRNHIPK953uYsOEIF2ttJkOEpSlHCYfrNvbJ3J02goJh1xzZaYFEfHyjq9NZiGMslHuXW5fdLEsVdDAlY?key=to9HlrSQY1kzOedF1cidXD5v" height="315" width="516">
  </span>
</p>
<p>
  <br>
</p>
<ul>
  <li>
    <span style="background-color: transparent;">설치후 실제 설치여부 확인 (*프로그래밍시에도 검증로직을 작업해야 함)</span>
  </li>
  <li class="ql-indent-1">
    <span style="background-color: transparent;">‘시스템 환경 변수 편집’-&gt;’환경 변수’-&gt;’Path’에 파이선 경로 추가되었는지 확인</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXckY37kA8SCuKpX8RCtQZ8fKseXBZeKF96gB4HJFgMJBFWIv8qs4mY5V7cDSnTpLhaONGbAhUoy5xf4I-3D0IEJxBg0IhKd8a340UweeZvr4jLWSWtGHLNabpfqH4nTJfjJO2Y?key=to9HlrSQY1kzOedF1cidXD5v" height="97" width="564">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">* 경로 복붙 -&gt; Python 폴더로 이동 가능</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">*구버전 설치 : download -&gt; </span>
  <a href="https://www.python.org/downloads/windows/" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">Windows </a>
  <span style="background-color: transparent;">-&gt; 원하는 버전 설치 (예: 11, 12버전)</span>
</p>
<p>
  <span style="background-color: transparent;">향후 구버전 사용할 때도 있을것</span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">Python 실행하기</strong>
  </li>
</ol>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">Powershell 관리자 권한으로 실행</span>
</p>
<p>
  <br>
</p>
<ul>
  <li>
    <span style="background-color: transparent;">Python 버전확인</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdOwhsEOsHHfd_CHJ9RiqcKqXHXO88jdhqU-lA8hCItyt7pdTNCHSIdCshaHVXOlZblK4rgK5XKGWpp4drrBsePb4OJctwT-pde0121QuHjS47-_YHk6f3VLI4mOluNtVDpuIFE?key=to9HlrSQY1kzOedF1cidXD5v" height="48" width="422">
  </span>
</p>
<p>
  <br>
</p>
<ul>
  <li>
    <span style="background-color: transparent;">파워셸 권한</span>
  </li>
</ul>
<p>
  <strong style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdXE99bGXDun5Z205ezMOWN9paJhqWYQxG8jKTyxxUMf8jKe7uAPLPwd6Kjh2itxkGYNpYfr7MJpc_zGDPWxMJyTzzV1_14w242zzbA8YPxipAJRt0eRCj8R77BYjA2-TkZXOn1?key=to9HlrSQY1kzOedF1cidXD5v" height="44" width="462">
  </strong>
</p>
<p>
  <br>
</p>
<ul>
  <li>
    <span style="background-color: transparent;">권한 바꾸기 (외부에서도 파워셸 접속할 수 있도록)</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeSo1bXzZ49ycgr4KTKYgUtiGKKlHDjayX8XSwP8hYX2mgV_1H7LbX8_8pYMQRHj4ly0rH31Q9gZuXdOOihIPB9za8HWLwl3Us9zyIvurjazI9LSY4IRJAnSfVkc-To_2vzadg?key=to9HlrSQY1kzOedF1cidXD5v" height="73" width="602">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">IDE 설치</strong>
  </li>
</ol>
<p>
  <span style="background-color: transparent;">IDE란 : 요리사의 도마나 칼과 같은 것. 개발을 위한 개발환경도구.</span>
</p>
<p>
  <span style="background-color: transparent;">설치할 툴은 VSCode</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfj6S93GKnJERoh-rEjCeeFERuOw5AO5jmhJpJegAFB_NSRdCMbiLY4C712oTgE_WsT8QseGXk-ncjHHh4ctdrN2apjPWMYzLbW5G5jOyKaviAqMJ_mj3lFmdzNtn005AXQbEyW?key=to9HlrSQY1kzOedF1cidXD5v" height="388" width="477">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">Visual Code가 좋은 이유 : Extensions.&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent;">좌측 Extensions 메뉴 -&gt;&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent;">python, jupyter, material icon theme 설치 (theme은 설치후 선택도 해줘야 함)</span>
</p>
<p>
  <span style="background-color: transparent;">indent rainbow 설치 (python 개발시 indent에 따라 색상을 다르게 표현해줌)</span>
</p>
<p>
  <span style="background-color: transparent;">기타 취향대로 설치</span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">개발 전용 폰트 설치 : </strong>
    <a href="https://github.com/naver/d2codingfont/releases" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">
      <strong>d2 coding&nbsp;</strong>
    </a>
  </li>
</ol>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">Visual studio -&gt; File -&gt; Preferences -&gt; Settings -&gt; font -&gt; font family 맨 앞에 D2Coding ligature 추가가</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdLzEoBPLQP3jCJRr7nYGo2XaUslgXAtGl930pm8je-nqYGi4v9ZCRA-WGvZmye7oZfoJ2C3Sq3VAyRxh1X6Zql35wciL1lhG3CWUUG7piFTaxEa01qm9bhSdji1EYx78hXresV?key=to9HlrSQY1kzOedF1cidXD5v" height="106" width="464">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">font ligature -&gt; json편집 -&gt; false를 true 로 수정 -&gt; ctrl +s (저장주의!!)</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXd7WheD-9Izn9gUh4Tdq_DSPRSflrYNqIw0d-WUz8JM_bQmduSViZFUtSqNcJHsQMLzoitMGznQZGDDySTgV2Oz3lwEziMPdIkv6-hwzS991y95WriVTnvUyyHSks1Lq3uF99l9?key=to9HlrSQY1kzOedF1cidXD5v" height="130" width="504">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">도커 설치</strong>
  </li>
</ol>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">*Windows Pro여야 함. 버전 : 20H1이상</span>
</p>
<p>
  <span style="background-color: transparent;">*MySQL도 도커 통해서 설치할것. (삭제편의, 백그라운드에서 돌아가지 않게 하기 위해)</span>
</p>
<p>
  <span style="background-color: transparent;">&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent;">파워셸 관리자 실행 -&gt; wsl –install&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent;">(윈도우에서 리눅스 설치하기 위한 프로그램)</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdgftri3ulI9R3LQbBH1mY39TapM1ZYETdHcueDY-1QgkKyU3MWEiTQPDiSjsYN2E-jMkkQL_Jrd8wA5ud5MSNy1r860R-hYhXopM1Sj5gEMN3km_3yXdNKVv0uoQpfYteuTRfq?key=to9HlrSQY1kzOedF1cidXD5v" height="142" width="585">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">-&gt; wsl --set-default-version 2</span>
</p>
<p>
  <span style="background-color: transparent;">(기본버전을 version 2로 변경)</span>
</p>
<p>
  <br>
</p>
<p>
  <a href="https://docs.docker.com/desktop/setup/install/windows-install/" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">Windows | Docker Docs</a>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">설치후 구글계정으로 로그인</span>
</p>
<p>
  <span style="background-color: transparent;">도커 settings -&gt; general -&gt; wsl, settings -&gt; resources -&gt; wsl integration 되어있는지 확인</span>
</p>
<p>
  <span style="background-color: transparent;">파워셸 실행 -&gt; wsl -l -v</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfqVPTb6MknN427L6fqm_IkjnepQccTaHllK_qWNqzk6KBCicWoLtRZo4-NewcF0S8HODj8WmW0bqJQ5OpzzpV-LWDoDonDdrypRIv8KA_pCSRPANUhEa7qUSZ35_CEcaxtXzEf?key=to9HlrSQY1kzOedF1cidXD5v" height="59" width="388">
  </span>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">MySQL 설치</strong>
  </li>
</ol>
<p>
  <span style="background-color: transparent;">강사님 제공 파일 다운로드</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">내컴퓨터 -&gt; C드라이브 -&gt; dev폴더 생성 -&gt; github, mysql, python 폴더 생성 -&gt; mysql 안에 mysql_installed, tutorial 폴더생성 -&gt; 강사님제공 파일을 mysql_installed에 넣음</span>
</p>
<p>
  <span style="background-color: transparent;">cd (폴더경로)</span>
</p>
<p>
  <span style="background-color: transparent;">명령어 : docker-compose up -d # mysql 생성 및 실행&nbsp;</span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">DBeaver 설치</strong>
  </li>
</ol>
<p>
  <a href="https://dbeaver.io/download/" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">https://dbeaver.io/download/</a>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">데이터베이스 -&gt; 새 데이터베이스 연결 -&gt; MySQL</span>
</p>
<p>
  <span style="background-color: transparent;">test connection</span>
</p>
<p>
  <span style="background-color: transparent;">* Public Key Retrieval is Not Allowed -&gt; 설정 수정 (</span>
  <a href="https://velog.io/@dailylifecoding/DBeaver-MySQL-connecting-error-Public-Key-Retrieval-is-not-allowed-solved" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">블로그 참고</a>
  <span style="background-color: transparent;">)</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeSQ9CXR82zMOcAefpuyMV1uo4XeFnYP26sVxsVjmwVKbvByxJObgHFe0Mz-qonxmCZ0K68GRos6gqWqFtbc6q_ayMiNO969veBG9F5S7P3L7srnwzbUc_CU_txupX57-al6m_A?key=to9HlrSQY1kzOedF1cidXD5v" height="132" width="205">
  </span>
</p>
<p>
  <span style="background-color: transparent;">MySQL과 연결됨 -&gt; 초록색 체크박스</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">* MySQL 중단시키려면 docker에서 일시중지 클릭</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfXplDAhFqD1VcadXGAFiTW7BJ47EP1D80GNYsbFhcjyqzGCqlIoZYGUNBVLDkgD883v2dDE4G9mTPYI2dbmcGed6PVH52dkKS3-IexTwBTmc_YYyDP9UEFm56XTKK0R7i2cmVh?key=to9HlrSQY1kzOedF1cidXD5v" height="71" width="211">
  </span>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">Git 설치</strong>
  </li>
</ol>
<p>
  <br>
</p>
<p>
  <a href="https://git-scm.com/downloads/win" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">https://git-scm.com/downloads/win</a>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">git bash 실행&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent;">-&gt; git config –global user.name “내가 쓸 유저네임”</span>
</p>
<p>
  <span style="background-color: transparent;">-&gt; git config –global user.email 내가 쓸 메일</span>
</p>
<p>
  <span style="background-color: transparent;">잘 등록되었는지 확인하기 -&gt; git config –list</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXd-rdGajWwpeoUsfRwP26AXbLBK4OVWEfdl4kVeBh3OOTn17j_G1kosQ2FQ-ltyy91rSayESKnicLDab-ZocebNzdNa_FCv602Msx324ScE2lA_eKO3euGvJcU2YE8d5aCLt5U?key=to9HlrSQY1kzOedF1cidXD5v" height="47" width="332">
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
<h1>
  <span style="background-color: transparent;">1/8 수</span>
</h1>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">오늘할일 : Python 첫수업</span>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">Python이란 :&nbsp;</strong>
  </li>
</ol>
<ul>
  <li>
    <span style="background-color: transparent;">90년대에 개발된 인터프레터 언어</span>
  </li>
  <li>
    <span style="background-color: transparent;">‘가상환경’ 구축가능</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">Python 가상환경 구축</strong>
  </li>
</ol>
<p>
  <strong style="background-color: transparent;">**향후 프로젝트 제작시 매번 가상환경 만들기!!</strong>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">vscode에서 open folder로 python폴더 열기</span>
</p>
<p>
  <span style="background-color: transparent;">*vscode에서는 프로젝트 단위로만 열자!</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">new terminal로 터미널 열면 프로젝트 폴더에서 열림</span>
</p>
<p>
  <span style="background-color: transparent;">터미널 -&gt; py –version</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXd0W49U36fGC0ys3HnqSTHZ4-F_QO2NDRZsNSpRCBxvvLRQNip-AMwKPhnEM9vbMpmPJY_urK_a1jS9EPjp8NUwKNNvhxANGO14SOMwkoeW2n1tHmv1Fg9UXAZlfj9UAyhKnSPy?key=to9HlrSQY1kzOedF1cidXD5v" height="52" width="293">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">-&gt; py -3.11 -m venv .venv</span>
</p>
<p>
  <span style="background-color: transparent;">(가상환경 생성 - 이름 : .venv)</span>
</p>
<p>
  <span style="background-color: transparent;">아무 라이브러리 없이 python만 설치된 가상환경 만들수있음.</span>
</p>
<p>
  <span style="background-color: transparent;">*아나콘다로 만들경우 여러가지가 설치된 헤비한 가상환경이 만들어짐</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">좌측 Explorer란에서 폴더에 가상환경 생성된 모습 볼 수 있음</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkcI6vtC1y6aJYLwBTkNhgo5jRaN9dYnidWUj1geWTvn1n2XKlnV7AbjwKKl5715SDW97GWnb5dAQPZTreAc1ekG7uuYDhaCZbHzLbZ2CETxCIvc_4wNdoDPLyNoDFLZn8jVP6?key=to9HlrSQY1kzOedF1cidXD5v" height="60" width="129">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">삭제 : 우클릭후 쓰레기통에 버림</span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">python폴더에 가상환경 폴더 만듬 (python-venv)</span>
</p>
<p>
  <span style="background-color: transparent;">vscode에서 open folder -&gt; python-venv</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">가상환경 또만들기 (python 3.12버전으로)</span>
</p>
<p>
  <span style="background-color: transparent;">py -3.12 -m venv .venv</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXec__zLMo46RMUWOG5aymcv1VSZyE1upIylFoZ-BvhJNaMIORqnfBpuLBOXLw1fQduZszwBqBKI7pFQczsv7gacqt7zPxwiHZIzTzWM2QrROCAE5RxDIH7wbJT7IRWk3F1k_pQG?key=to9HlrSQY1kzOedF1cidXD5v" height="68" width="139">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">venv 안에 들어가서 작업하기 -&gt; .\.venv\Scripts\activate</span>
</p>
<p>
  <span style="background-color: transparent;">*경로는 그냥 tab 누르면 자동완성됨</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfXtiThl7Be8paykzU-Bj4zJ2_67bWuF560_yUQwOoYL__lPGQOQ5L8C5tQnDQhc8xxEm8_FnK7Qk0aiyyGq9JQNleoYDeJiIu2nJMj1Ekn_schqyUuYl9kgyGTdAvguzYTeBcf?key=to9HlrSQY1kzOedF1cidXD5v" height="50" width="429">
  </span>
</p>
<p>
  <span style="background-color: transparent;">여기서 py –version 하면 3.12라고 나옴</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">나가기 -&gt; deactivate</span>
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
<p>
  <span style="background-color: transparent;">&lt; 문제 &gt;&nbsp;</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent;">프로젝트 3개를 만들고 해당 가상환경도 구축하자</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent;">프로젝트 1</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent;">이름(폴더명): python-venv-3.11</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent;">프로젝트 2</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent;">이름(폴더명): python-venv-3.12</span>
  </li>
</ul>
<p>
  <span style="background-color: transparent;">프로젝트 3</span>
</p>
<ul>
  <li>
    <span style="background-color: transparent;">이름(폴더명): python-venv-3.13</span>
  </li>
</ul>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">각자 폴더 만들고 vscode에서 가상환경 생성함</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcWcC0ABTZN2oFC9LNV_4tX8O00aBqBnqfVlRomkaNuHV5dwH9ComarVkmYmSARp1QARLRy2qrWdG79E-bt78KNI64KXOaNVzKhFZcRA5kwjoQOd7CKwrJpe0hPDjnoNH2Ardgq?key=to9HlrSQY1kzOedF1cidXD5v" height="165" width="159">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">python 파일 생성</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdEwyJg9sPCylGu1x6CIxqd3V6pNOQ25DoETAVQQRYz33TkqRfvM7pAlntCQd06i5KHjTgX32mBGFzU8mVMRP-VluhB5SFG2ZLD_bY6_hiRbqIhW8nKmNVKZL8qb6PdGxon4L4?key=to9HlrSQY1kzOedF1cidXD5v" height="88" width="149">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">예제 : Hello World! 프린트하기</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfni-aZ18cMGmdAjzveB9mpsIu2dZ0OgcXgZs1Yw7mOheui-Yvug0NdfTf6yKwmWO9pnY3R9Lr15ix-ctzcekFxeuAWEBvksgaZisFA2UXjXlALzX5TPFLTFZsZ-nnt57dmF7I?key=to9HlrSQY1kzOedF1cidXD5v" height="44" width="327">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">실행&nbsp;</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfGbz0sdSqaiudozvB8pqXcOtHQ9IpTr68K3DaLAylhEHMXrdOtTtRJdSudb7N7sxE18DPvbCSdgfGYxHW4Xo9bQAU0IDzkVvbNuj84E132SsxW3mFxbvu79ezBMFmaMPz25HWB?key=to9HlrSQY1kzOedF1cidXD5v" height="36" width="359">
  </span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">가상환경에 모듈 설치</strong>
  </li>
</ol>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">가상환경에는 Lib -&gt; pip 기본으로 설치되어 있음. pip 이용해서 모듈 설치.</span>
</p>
<p>
  <span style="background-color: transparent;">우선 업그레이드. 가상환경 켜고 -&gt; python -m pip install –upgrade pip</span>
</p>
<p>
  <span style="background-color: transparent;">*1개월만 지나도 pip 업그레이드가 필요해지므로 그냥 매번 업그레이드하는게 좋음</span>
</p>
<p>
  <span style="background-color: transparent;">이후 설치.&nbsp;</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">numpy : (가상환경 켜고!!!) pip install numpy</span>
</p>
<p>
  <span style="background-color: transparent;">잘 설치되었는지 확인 : ex02.py 파일생성 -&gt; import numpy</span>
</p>
<p>
  <span style="background-color: transparent;">가상환경 켜고 설치했으면, 가상환경 밖에서 python ex02.py 했을때 오류나야함!</span>
</p>
<p>
  <span style="background-color: transparent;">(*난 실수해서 가상환경 외부에서 설치함. 그래서 오류가 안났음…)</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">seaborn : (가상환경 켜고!!) pip install seaborn</span>
</p>
<p>
  <span style="background-color: transparent;">(*이번엔 가상환경에 잘 설치함. 그럼에도 불구하고 오류가 안남! vscode 기능이 ‘개선’된것같다는 강사님의 말씀. 가상환경으로 자동적으로 연결이되었음)</span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">requirements.txt</strong>
  </li>
</ol>
<p>
  <span style="background-color: transparent;">requirements.txt가 있으면 자동으로 동일한 세팅의 가상환경을 만들 수 있음!</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">아까 넘파이랑 시본 설치한 가상환경에서 진행</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">pip freeze (설치된 라이브러리를 보여줌)</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">pip freeze &gt; requirements.txt (pip freeze의 내용을 requirements.txt에 넣어줌)</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">python-venv2로 이동 (여기엔 새로운 가상환경 깔아줌)</span>
</p>
<p>
  <span style="background-color: transparent;">ex01.py 만들어서 import numpy, import seaborn 넣고 오류나는지 보기</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfN5s9dLTq6Zh8023qxzvSBqARpGN5xF8P7LYLAvB54AMhA0OWTRYR686c3pVQLWx5dPPOZAfsU7irhUo6s0r2wo8n82f6haQVpWS2_5XWvW7s0L6zvsADEZCjY2iTGS5zzI9s?key=to9HlrSQY1kzOedF1cidXD5v" height="94" width="463">
  </span>
</p>
<p>
  <span style="background-color: transparent;">(*이번엔 제대로 오류가 났다!)</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">그럼 이제 requirements.txt를 복붙해옴</span>
</p>
<p>
  <span style="background-color: transparent;">
    <img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXd9BOB_vOkirlpd-U1-i-xgP40dTKpf6EvqddYPULAQaOjKwe3Py7nq1jwvm7-QFWjnW1DkuXXFAw5p3cfKP1wQK-mQ281aclZOGiJGRZpXG3KgcSJVFDis6HehnhBS-eZDhjc?key=to9HlrSQY1kzOedF1cidXD5v" height="156" width="198">
  </span>
</p>
<p>
  <span style="background-color: transparent;">명령어 : pip install -r requirements.txt</span>
</p>
<p>
  <span style="background-color: transparent;">이러면 자동으로 requirements에 있는 모든 라이브러리가 설치됨~</span>
</p>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">이제 ex01.py 실행하면 잘 실행됨.</span>
</p>
<p>
  <br>
</p>
<p>
  <br>
</p>
<ol>
  <li>
    <strong style="background-color: transparent;">자료구조</strong>
  </li>
</ol>
<p>
  <br>
</p>
<p>
  <span style="background-color: transparent;">변수, 상수, 계수 설명</span>
</p>
<p>
  <span style="background-color: transparent;">폴더명 : python-variable</span>
</p>
<p>
  <br>
</p>
<p>undefined<span style="background-color: transparent;">pip install jupyter</span>
</p>
<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">파일생성 : ex02.ipynb</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">Select kernel -&gt; python environments -&gt; .venv</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">+code 클릭하여 코드작성</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfCQSETHzdr518nB1frUdb_2TO_G1J2f6jTliKoHOFk4e6IrNdbERsd1Gvi9Yk_Sgpe_hX53y0dslwOLetAjlKbsTiEGxIRBvUZ3oDUHDYBtPXJffVPIG1zc549uFZWVQVNrQJs?key=to9HlrSQY1kzOedF1cidXD5v" height="98" width="271">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">기초 변수 지정법 배움 (x = 10 등)</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdAuhzxwNR4KHkBrK5X6lVpmk8w8cr4vtJuZUnt_rYmHMk7zTS8Zaj2uDgI3cEWfXWv0Om3f1_5VEsuMdjYhqjBrsuqGWOJVr4_EIfgxHe9JDovsRRNsRyUqqEoxGw-2ULuDM3C?key=to9HlrSQY1kzOedF1cidXD5v" height="151" width="458">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">*변수의 이름은 잘 지정해야 한다! (name, age 등 설명적인 표현 사용)</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">snake_case, CamelCase 배움</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">변수이름은 숫자로 시작할 수 없음</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">예제 : 구구단</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdmqpxrFsvmY6Ddeq3vaT1u6LygUA7e9rSYCOFQ6RJMWqQtEFvO20O0Gcfw4Wq1ZlXOXppUKdYtvRf0l_COdgEY-6JoGtj9tx9DT8EcvrUDOaTUwIXWYe9v4fWmVAnloaeki9Jh?key=to9HlrSQY1kzOedF1cidXD5v" height="91" width="207">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">비교연산자 배움</span>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">==, =!&nbsp; : 변수에 담긴 데이터를 비교</span>undefined</li>undefined<li>undefined<span style="background-color: transparent;">is : 변수 자체를 비교. id(num1)과 id(num2)가 같아야 함. ==보다 속도 빠름.</span>undefined</li>undefined</ul>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">변수 : 데이터 수정 가능</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">상수 : 데이터 수정 불가능</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">&lt;문제&gt; Python에서 상수 선언하기</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">참고: </span>undefined<a href="https://velog.io/@pm1100tm/Python-%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%97%90%EC%84%9C-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%83%81%EC%88%98%EB%A5%BC-%EC%A0%95%EC%9D%98%ED%95%98%EA%B3%A0-%EC%82%AC%EC%9A%A9%ED%95%A0%EA%B9%8C" target="_blank" style="background-color: transparent; color: rgb(17, 85, 204);">블로그</a>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeFwFyZoKz8oR0icIiBAr9WItupriNRTrbz7fllBcD20jrmBYLH1InjQSBsHZSpoP26tJcEd7k3m5zi4dhKMBkQxCrROxjk4vVike5R7lpTbpNiMKUNzyV1i59MktLslOTe0KXO?key=to9HlrSQY1kzOedF1cidXD5v" height="634" width="334">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">상수의 값을 지정해 주는 대신 매번 ‘함수’를 호출함으로서 문제를 피해가는 방법임.</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">*강사풀이 : enum 사용</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdDZlhQdXeyeG59nOiQdlNHtkASHTy0js8tqvXtf0vnEETpvpIlbaJ6-ytnnIJ966c7Dlc6QCbwl30Rpey1tD7-FBZQjGNB7um0zBbv_myo_9_9ytseUe5a4rm-LhDvHF4PxbIN?key=to9HlrSQY1kzOedF1cidXD5v" height="408" width="259">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">변수와 상수의 공통점 : 데이터 조회는 둘 다 가능하다</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeLx1bgwsoKQwWeNo9RUe0p8oUQO6vM7R9GY4ADzivwtjUoennggavKgcpKogNEeXilkuwG__j0QSSAvSKXeu0tSMvnlnWMBIIPelKBuVN53AhmhQvUNbvNpqWIlXg8rsZJHIIo?key=to9HlrSQY1kzOedF1cidXD5v" height="116" width="353">undefined</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdZrZ6CLLfCuUs6Qt4syQ7DTLOtnRJjWKakWcmQoEX1pVbSbU3iMTwhCnWv1sUvEfSIRdLposYwgNfAczdPE1PgASh_w341IvlfKjTSvYrd2OYzJWLLkLj5yYzjmqgx4mzsM74?key=to9HlrSQY1kzOedF1cidXD5v" height="94" width="200">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ol>undefined<li>undefined<strong style="background-color: transparent;">문자열</strong>undefined</li>undefined</ol>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">문제 : int와 float에는 없는 string의 값은?</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">답 : size</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">*주석을 잘 달자! 자신이 짠 코드를 잘 설명할 줄 알아야 한다</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXemF2CnEMv8C8AMwHLB6qL0MHlKNInxtosLysKgG21DrVWb7ua4HIPV4K3ftrrDvIT9ZEEO8rcnrXMG6_KSBVqdeAQtuxpdbxX_1EwYKCSt9v7GSg0qSK_xcn5D4fuTkIZuHsvW?key=to9HlrSQY1kzOedF1cidXD5v" height="278" width="290">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXev2zpfxHBV0d_4Cc6uxwo0OQZZPvwZJz002ApJdZk2bdrsXZpFHaroJACBc-E9O2fyiaj6c_uvUciGxC86rdo1hGBwPUy860UfliFdbQNzK9yFRH2ahjR-wdjVS4Ps4Vt3hmtl?key=to9HlrSQY1kzOedF1cidXD5v" height="357" width="390">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<h1>undefined<span style="background-color: transparent;">1/9 목</span>undefined</h1>undefined<p>undefined<br>undefined</p>undefined<ol>undefined<li>undefined<strong style="background-color: transparent;">Python 문자열</strong>undefined</li>undefined</ol>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">지난시간 복습 : 데이터 슬라이싱</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdIsX5bBxTdRpWQHnPUYNH4y9jHGgbzQy91BM0hAX_Q763raORRagAeTrknXBVCOJz8yOXF_mrXDq3klMnq6aTTVMnhody_tQcKiigQskZ6Azsc-KlZZyWc9Hm_99Ge6wi1igxE?key=to9HlrSQY1kzOedF1cidXD5v" height="108" width="253">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">포매팅 (f-string, 기타)</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXekTDJlmKhM2AVNpvGbsARtdcPmFb6O9X9jYXxcLt9yiywe6qKTRYMdPmuTctYmw8QRQU59d-AaGt9fxK6pAQSxmqFBWMCmcpf2Z5lnRPNgP-fwdcDnudoIu2hMe47c-6L1fr_E?key=to9HlrSQY1kzOedF1cidXD5v" height="203" width="303">undefined</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeFjQUNSQcSOC5glBWtr1mK_E3mpRvWLdemFkN01MVADOYgFip0yXo1l0B1MY8xw_Ei7ODnTUOK6aCsBi0GO9kN6QigJsw2nYVY6ra5b91qa33NmqTktq9i0YFGv95-8dW3laeT?key=to9HlrSQY1kzOedF1cidXD5v" height="97" width="293">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">replace</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcfS2Qp7eZFoC4YM3rAfYCmSJuHl06C1yp7cKWbEmSupn_EYPpR9i2iyec9-7Ig_kAg9nI4BFULZLM5nOvBrDIAx2pcXbSH6yxjLh2H3_qIGk7BWaIJAjWJz0SacBASaH8P6m-v?key=to9HlrSQY1kzOedF1cidXD5v" height="118" width="301">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ol>undefined<li>undefined<strong style="background-color: transparent;">Python 기초 자료구조</strong>undefined</li>undefined</ol>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">리스트/튜플/딕셔너리/집합</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">리스트와 튜플의 차이 : 튜플은 수정이 불가.</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">리스트와 딕셔너리의 차이 : 딕셔너리는 키-값 페어로 저장됨. 리스트는 위치로, 딕셔너리는 키로 값을 식별.</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">리스트는 size가 있음 -&gt; 인덱싱, 슬라이싱 할 수 있음</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">리스트 안의 리스트</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXf_aLPer2I9s93fE2Jt5meuVo7trOYGrWYloRhmUqezZiZNLYS_SEb03AU3Q4WtQMxM8HyYVocatYcJDKwG4J6TDTl8TNIcgVFn6gZFTj1zUxdK2JzIIAmTLdDCycCBcrFklLA?key=to9HlrSQY1kzOedF1cidXD5v" height="129" width="226">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">리스트 원소 추가 : append, extend</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe5mZVvo_QdW2F5H9F0xOPkLHdBInk6tj2-rMBzcfMvfAG28HDD10DPCbtWPUMVE6_dpX_gMYmEzQ71t_ElGKMLVrCogTDzBMP1GjEb9l8ZQC9p63nZWRcLEzDUEXtUjXtenBvu?key=to9HlrSQY1kzOedF1cidXD5v" height="194" width="170">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">딕셔너리 내부 접근</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXc3QS0Sn-p_CPV_1UqgdLnEG8WX8jWy8HJfJGQU1c74qoCJQe3vNpvt_r6hbTVRX1x8vaVRy0eMQvChDChndfdYn8MPvUNvd2e3nyUbnfdWbIgC0Ep7ERF_dkPjIn90oF2h0Ew?key=to9HlrSQY1kzOedF1cidXD5v" height="176" width="213">undefined</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdmK8rRq_MV2yvjTfHesR7xU5l4xWRAUrqFp1-YPXWPE-Q27aVMcHuMXkmHPO6CT4LG92ItRHO09p48zSKnG_u6I6iwWRS9rvqDg7MPPGYlkJOP1LxUhkIIww0L1UVgAu2VNfMK?key=to9HlrSQY1kzOedF1cidXD5v" height="96" width="231">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">집합 : 중복 제거됨</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXffkA3s02l7TuPvQ26zXcl43ib4nJNAvJFnNZ8A080dbyh_yd0byXJcrMT45nUlOk3xDx_p0DqheRNSniQI9b-iKey6CFmulqn4K2_eYUjQKjaZyc5SJMWvwmv0B-ymVSChogM?key=to9HlrSQY1kzOedF1cidXD5v" height="115" width="163">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">리스트의 중복데이터 제거를 위해, 집합 변환 -&gt; 다시 리스트 변환 의 방법을 사용할 수 있음.</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">집합 : 합집합, 교집합, 차집합</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">연산기호 사용하여 집합 연산 가능</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">Boolean 기호</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcDH9uDA-joYlyZs3LuvPnt8XIUDBA2MFw1nposUSb5MadwgcSPyMCS8E84uHiZti8Hwfn1KjzvfAG1x2eqFuGY_DpncydG-Sq-7-4pXqBV0QbqwX23GT0VCPsFWZ4bcTyLuhe7?key=to9HlrSQY1kzOedF1cidXD5v" height="203" width="271">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ol>undefined<li>undefined<strong style="background-color: transparent;">제어문</strong>undefined</li>undefined</ol>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfcLJomBY7p_84aDCbr6MorYxNMQumwda-Gjcp5F5os8o7OGRwbubkxiQQruzidStBtnNRiQFDE2phwtjF1Zz-3CMZFzABmXqLO9G0Mat6iPH2rsVfNH0BKLrTM6zNExmncH25j?key=to9HlrSQY1kzOedF1cidXD5v" height="131" width="224">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">&lt;문제&gt;</span>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">학생들 중 20대인 경우엔 ‘하이 20대’, 30대인 경우엔 ‘하이 30대’, 40대 이상인 경우에는 ‘안녕하세요^^’를 인쇄</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfnUQfYVq9Toa1QhQ9a4eToTmKp1tcLEZl6AfJMxkwumQf8HCVRNVnx9J_9f-PvDtijLpO0UwLBdZVpv7N-hFG3UOsNr1T6BBbs3YefE1ysgsNy5yp7oQ9zCK--9w3BDyjqQOQ?key=to9HlrSQY1kzOedF1cidXD5v" height="229" width="234">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">강사풀이 :&nbsp;</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcC7rjWwlPat3ummdBbbM3cHnXjfCXrryiwfHAuFahWOYbVNN_kjiBufGDDbB4HfQLoZay5gaB7lr4YVSW4AhM6_ohlwb-X7BgKaXAonL6hJenFj6d-qjJKOdGYkq3ap82dAl5w?key=to9HlrSQY1kzOedF1cidXD5v" height="195" width="214">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">(*강사 풀이가 깔끔하다! 난 항상 if문을 거꾸로 짜는게 좋다는걸 잊곤한다.)&nbsp;</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">for문, enumerate 등 배움</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">for문과 else문 사용하기</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXd6XcdQ7-yU0runDESI2puf_NVRr9CqSXjEI18zam2vRs8XvXoIzhgBlz7-Lx8EX0o1qt7g7xkcigucbckqYY7xhXAj1nFy2ZyMxxC98WZD7_na7t3fn7tYHBTeKWa9SJao-TI?key=to9HlrSQY1kzOedF1cidXD5v" height="254" width="389">undefined</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">for 문이 정상적으로 실행완료되어야 else가 실행됨</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">만약 break등을 넣어 정상완료되지 않는다면 else는 실행되지 않음</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<h1>undefined<span style="background-color: transparent;">1/10 금</span>undefined</h1>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">&lt;문제&gt; 가위바위보</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">두 명의 유저에게 ‘가위 바위 보’ 중 하나를 입력받아 가위바위보 승패를 가려주는 프로그램을 만든다다</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXc_K7t506qzkoTV3dJWgfiLMq5FRtLRtf_gZT4XJusEI7xjWqsdOcfEL-fj0lr-f-G16vpPrNxRXLtuzFh7YR4XcK-bcXUIp-R22vMUSsoTxZJXmmUJuwcIIOtLg9m4ybJEiyA?key=to9HlrSQY1kzOedF1cidXD5v" height="422" width="471">undefined</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">유의점 1. 잘못된 입력시 이를 처리한다 -&gt; 잘 처리했음</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">유의점 2. enum class 이용하기 (상수이므로) -&gt; 수정하기</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">강사풀이 :&nbsp;</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXccnOH1uFh-ybMW8Su9yu8Pnq_H4LTxTWy4Jy2btjgx-MT8i0rSoqdgJQ_eWWxsXyYh4cSU5T2kq0uPakje_nSSB4jzcR1R1c_yphw48bSX7P6wE66Uc5Kih2wOBS_nIV0nNNzZ?key=to9HlrSQY1kzOedF1cidXD5v" height="258" width="217">undefined</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfnnmoY-9lrtDqnu8PKslmacgUdfuBL_svipApdkyvnfMTcALNkqDAU1NN5cMRVb6L-uv5QUAQjxwgo0Z3sUdfe8n1F36A9YWhMl-9U0MRLyF1HUXZwmrDK5peU9NyhBW2TnTYI?key=to9HlrSQY1kzOedF1cidXD5v" height="323" width="439">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">(*강사코멘트: while을 넣었으면 더 간단했을것, 이프엘스가 너무 복잡해서 안좋은코드임)</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">(*내생각: enum 클래스를 저렇게 사용할수있구나!)</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ol>undefined<li>undefined<strong style="background-color: transparent;">while문</strong>undefined</li>undefined</ol>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXc-54_rUJsyS2lTRKmi7mS0YZAYau9_kQdL8JYhJ65tV-Ucbo4rrEBZPt6fOvzCI04CndgHHcEgChOeBoY-_xwhvTDthwCjLpA8UyRMnl2PMi_grIOnXhvZhmm3v-grscJbBqJj?key=to9HlrSQY1kzOedF1cidXD5v" height="276" width="197">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">&lt;문제&gt;</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">Hello</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">ello</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">llo</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">lo</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">o</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">이렇게 프린트되는 프로그램 짜기</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXedi4-KLPTf_ULJwD4fknHN_sVoC3M77m-WgRopQD5z-CZrcgM5cGnKVyojL6Zw-7EAYVm5opVm8vGFfV2E4yDIvWFeKZdWs5EvR7avqyOPBZSYSwBMSiHdLM31a94Bihfngvg0?key=to9HlrSQY1kzOedF1cidXD5v" height="253" width="194">undefined</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">(*첨에 쓸데없이 if-break를 넣는 바보짓을 함. 정신차리자!)</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">&lt;문제&gt;</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">원보 데이터: 정수로 이루어진 리스트(ex&gt; [1,2,3,4,5])</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">만약 짝수가 있으면, 짝수있어요!</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">만약 짝수가 없으면, 짝수없어요!</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXf0z0dFG3DbE5MJndteHGQbGaA5Ro1xfrCINb4KkMMHouoPunRngI44R0y-tBeGkxD_O6t1JqYX2ar6IDB31zAzN_Yix5mxvaUT0wQRWvI3opfWJxjx7mpJkGqok8_0xyBm8Vvk?key=to9HlrSQY1kzOedF1cidXD5v" height="250" width="251">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">강사칭찬코드 : contain_even 변수 없이 그냥 바로 프린트하는걸로 짠 코드</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">while 코드 사용법 추천</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXffWxNE_otSVuz6ciHiBH9I5jSY2u7B2hvW1lgkiKL4I7f2bx0Abf1H2Kit1pzwqTfhrHprr1OtUtd7um-9mPOpOd7HKuCxBDZg1XT6Wmab40opEhizmuJ1ExXsJKCAG5VHhmJ7?key=to9HlrSQY1kzOedF1cidXD5v" height="236" width="177">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ol>undefined<li>undefined<strong style="background-color: transparent;">Error</strong>undefined</li>undefined</ol>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">IndexError</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfvv5kRrwTbpwAGwhgb9iuN-rmBaHd67bJF6aCBSlRkycNIUZKHBjR9cVgySEp3kZBZxhbUsBKTjQGJ6SfRdm2VnlCy1VPPrKAhBRz9DVshSJsQkZVJfItmcKxJP3BZSsam9PiL?key=to9HlrSQY1kzOedF1cidXD5v" height="46" width="316">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">이후 여러 Error 배움 (NameError, TypeError, KeyError 등)</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ol>undefined<li>undefined<strong style="background-color: transparent;">예외처리 : Try ~ Except ~&nbsp;</strong>undefined</li>undefined</ol>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdztvVKEubAmiYK8QWfUnsOA-xdrWXZvnFcn3XY5RR7BzY9RG9YcskfDhX2l2kWqK27xfEvwLPx1RqnSF4vVmOYbYh6mJU6nSG2HlqFxDa911Xf4vuDXRHQPhXeArEhAMADUKFf?key=to9HlrSQY1kzOedF1cidXD5v" height="187" width="242">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">finally : 언제나 실행됨~</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">-&gt; try 이후 성공적 실행시 실행되도록 하려면 else 사용</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXc_14gow_VLwowCiOI7zSY5b5B5Z8dnvY9H2SP47aziivKE19mClT67-0Ej2EugRb7KAPC6yFW6qzkx2YmPjU98vP3my1PMg8LwSf7npVevolW3FP0Ss3AHcRaLYVNMWJk0H7-0?key=to9HlrSQY1kzOedF1cidXD5v" height="348" width="326">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">assert : 조건이 false일때 발생하는 오류</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXc5Z3bqKo8NRy-vaAMfB1vqPh1oWYFmtDMaLAIUNLyzOpSpJR97yRZ2liHaIQxzU919DjpLG6V_6FMEdU8GO6lZWRburTIMUK29N8-jIgG5NhoJzsyFPEoRzgWBJt8gSwOEtfg?key=to9HlrSQY1kzOedF1cidXD5v" height="270" width="312">undefined</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">오류 정의 : class 통해서 정의한 후 raise 클래스명</span>undefined</li>undefined</ul>undefined<p>undefined<br>undefined</p>undefined<p>undefined<strong style="background-color: transparent;">undefined<img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe8Yt3rAhk2orKgnV35posyAPOI7Ly8ryoFCwoxVmszcvAivdspM9mgJQEal4zV_tVNNHLY3c9hgr6bAUaJJpmRd_i3pwn8eBnWw86v6jK7mQI-_Whe6LtL6K8Dx4T4rm56MCdK?key=to9HlrSQY1kzOedF1cidXD5v" height="372" width="420">undefined</strong>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<br>undefined</p>undefined<ol>undefined<li>undefined<strong style="background-color: transparent;">토이프로젝트 기획</strong>undefined</li>undefined</ol>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">나는 ‘법률상담 AI’ 프로젝트에 합류했다.&nbsp;</span>undefined</p>undefined<p>undefined<br>undefined</p>undefined<p>undefined<span style="background-color: transparent;">이번주 할일</span>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">git &amp; github 사용법 공부</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">-&gt; 브렌치 &amp; 머지 &amp; 커밋 &amp; VScode 연동&nbsp;</span>undefined</p>undefined<ul>undefined<li>undefined<span style="background-color: transparent;">팀장님 계정으로 github의 레버지토리 생성 및 팀 초대</span>undefined</li>undefined</ul>undefined<p>undefined<span style="background-color: transparent;">-&gt; 생성된 레퍼지토리에 README.md 작성&nbsp;</span>undefined</p>undefined<p>undefined<span style="background-color: transparent;">-&gt; README.md 내용에는 팀명, 팀원, 팀장, 그리고 프로젝트 설명</span>undefined</p>undefined<p>undefined<br>undefined</p>