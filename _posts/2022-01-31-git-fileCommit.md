---
layout: post
title: Github 원하는 파일만 Commit & Push 하기
description: "Github 원하는 파일만 Commit & Push 하기"
tags: [github, 공부]
comments: true
---

### **[Git] 원하는 파일만 Commit & Push 하기**
<br>

작업한 파일 중 원하는 파일만 Commit & Push 하기

## 사용할 명령어 정리

<br>

```
// git status 명령어를 이용하여 파일 목록 확인하기  
git status  

// git diff 명령어를 이용하여 기존파일의 변경내역 확인하기  
git diff  

// git add 명령어를 이용하여 원하는 파일 추가하기  
git add <경로 및 file명> <경로 및 file명> <경로 및 file명> ...  

// git reset 명령어를 이용하여 add된 파일 취소하기  
git reset HEAD <경로 및 file명>  
```