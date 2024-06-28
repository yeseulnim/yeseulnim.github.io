---
layout: post
title:  "깃헙 블로그 제작 오류 해결"
date:   2024-06-28 12:45:24 +0900
categories: 잡담
tags : [블로그,잡담]
---
깃헙 블로그 제작은 아래 글을 참고했다. 

https://wlqmffl0102.github.io/posts/Making-Git-blogs-for-beginners-1/

제작 도중 "An error occurred while installing wdm (0.1.1), and Bundler cannot continue." 란 에러가 있었다. 이건 다음 링크로 해결했다. 

https://talk.jekyllrb.com/t/newbie-problems-with-wdm-errors/9233 

맨 아래를 보면 gemfile을 수정하라는 내용이 있다. 참고하여 해당 라인을 주석처리했다. 