---
layout: post
title:  "구글독스 글 깃헙 블로그로 포스트하기"
date:   2024-06-28 12:45:25 +0900
categories: 잡담
tags : [블로그,잡담]
---

우선 richtext to html 컨버터를 사용했다. 
[richtext to html 컨버터](https://www.lido.app/tools/rich-text-to-html-converter)

그 뒤 워드에 복붙하여 보기싫은 span 태그를 찾아 없애고, 이를 codebeautify에 가져가서 코드를 정리했다. 
[codebeutify html viewer](https://codebeautify.org/htmlviewer)

여기서 드러난 문제는 nested list, 즉 다단계 리스트가 보존되지 않는다는 것이다. 
즉 구글독스의 1) -> a) -> i 로 이어지는 형식의 리스트를 보존하고자 richtext to html을 이용한 것인데 이게 헛수고가 된 것이다.
태그에는 <li class="ql-indent-1"> 와 같이 인덴트가 표기되어 있는데 뷰어상에서도, 블로그상에서도 이게 적용되질 않았다. 

구글독스 필기를 그대로 html로 옮겨올 수 있다는 이유로 깃헙 블로그를 시작한 것이었기 때문에 매우 당황스러웠다. 

하지만 다행히도 구글독스 필기 옮김의 또 하나의 큰 장애물인 '이미지 보존'에는 문제가 없었다. richtext to html 컨버터가 이미지 링크를 잘 옮겨주었다. 

그래서 이번에는 눈물을 머금고 직접 인덴트를 달았다. 중간에 망가진 부분도 있지만 신경쓰지 않고...

이렇게 html정리를 끝내고, 마크다운 글 내부에 html태그를 달고 그 안에 html 코드를 복붙한 뒤 포스트했다.

그럼 이제 스택오버플로우에 html인덴트 질문 올리러 간다...

-> 검색해서 답을 찾았다. quill 을 사용한 html코드라는 점이 문제였다. 자바스크립트와 css에 퀼 에디터 사용을 표기해 주어야 한다는 것이다. 일단 해보겠다...

-> 클로드에 문의하여 보다 정확한 답을 찾았다.
html에 아래의 코드를 추가해 주기만 하면 되었다.

```html
<head>
  <style>
    .ql-indent-1 { padding-left: 3em; }
    .ql-indent-2 { padding-left: 6em; }
    .ql-indent-3 { padding-left: 9em; }
    /* ... other styles ... */
  </style>
</head>
```

문제는... 아래의 코드를 추가했을때 인덴트는 먹히지만 그렇다고 해서 네스티드 리스트가 되진 않았다는 점이다. 그냥 인덴트"만" 되었을 뿐이다.
그것도 번호는 인덴트되지 않고 번호 뒤에 붙는 텍스트 본문만 인덴트되었다...

그래도 이게 최선인 듯 하니 다음부턴 이걸로 인덴트 처리하고 넘어갈까 싶다.

+ 혹시나 해서 클로드에게 'quill형식의 인덴트를 평범한 html형식의 네스티드 리스트로 변경하는 코드를 만들어 달라'고 했는데... 실행해보니 꽝이었다. ㅋㅋㅋㅋ

