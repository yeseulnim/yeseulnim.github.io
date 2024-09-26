---
layout: post
title:  "pyinstaller exe파일에 Qt Designer로 제작한 .ui 파일 포함시키기"
date:   2024-09-26 12:45:24 +0900
categories: 잡담
tags : [블로그,잡담]
---

pyinstaller로 .py 파일을 .exe 파일로 변환하는 작업을 할 때,  GUI를 Qt Designer로 제작해서 별도의 .ui파일로 만든 경우 이 .ui파일이 exe에 포함되지 않는 문제점이 있다.
검색하여 해결방안을 찾았다. 
[참고한 글](https://python-forum.io/thread-40235.html)


코드 안에 다음 내용을 포함시킨다 : 
{% highlight python %}
if getattr(sys, 'frozen', False):
    os.chdir(sys._MEIPASS)
{% endhighlight %}

그 뒤 아래와 같이 명령어를 넣어준다 : 
{% highlight powershell %}
pyinstaller -w -F pythonfilename.py --add-data='GUIfilename.ui:.'
{% endhighlight %}
