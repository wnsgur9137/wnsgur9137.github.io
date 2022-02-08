---
layout: post
title: 블로그 게시글 공유 만들기
description: "Github 명령어 정리"
tags: [블로그, 공부]
comments: true
---

블로그 게시글 하단에 공유 링크(버튼)만들기  

**facebook**
```
<a href="https://www.facebook.com/sharer/sarer.php?u={{ site.url }}{{ page.url }}" title="Share on FaceBook><span class="count"><i class="fa fa-facebook-square"></i> Like</span></a></li>>
```

**twitter**
```
<li class="twitter"><a href="https://twitter.com/intent/tweet?text={{ site.url }}{{ page.url }}" title="Share on Twitter"><span class="count"><i class="fa fa-twitter-square"></i> Tweet</span></a></li>
```

이 블로그에 공유 기능 넣을 땐 아래 코드를 입력
```
<div class="social-share">
  <ul class="socialcount socialcount-small inline-list">
    <li class="facebook"><a href="https://www.facebook.com/sharer/sharer.php?u={{ site.url }}{{ page.url }}" title="Share on Facebook"><span class="count"><i class="fa fa-facebook-square"></i> Like</span></a></li>
    <li class="twitter"><a href="https://twitter.com/intent/tweet?text={{ site.url }}{{ page.url }}" title="Share on Twitter"><span class="count"><i class="fa fa-twitter-square"></i> Tweet</span></a></li>
  </ul>
</div>
```
