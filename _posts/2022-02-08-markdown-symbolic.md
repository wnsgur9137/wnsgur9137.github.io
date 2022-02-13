---
layout: post
title: MarkDown 특수문자/내부링크 Symbolic/Inernal Links
description: "MarkDown 명령어 연습"
tags: [markdown, 연습]
comments: true
---


# Markdown Syntax 마크다운

[1. 특수문자](#1-특수문자)  
[2. 기호](#2-수식)  
[3. 테이블](#3-테이블)  
[4. 내부링크](#4-내부링크)  
[5. 체크리스트](#5-체크리스트)  

<br>
<hr>
<br>  

## 1. 특수문자

* 아래 내용은 특수문자를 어떻게 하면 특수문자로 입력 가능한지를 보여주는 표이다.
* 이 표에 나와있는 문자 그대로 입력하면 특수문자를 마크다운에서 자유롭게 사용할 수 있다.
* \를 이용하여 문자를 출력할 수 있다.  
  ex(\\> $\rightarrow$ >)  


<br>

Symbol|HTML Number|HTML Name|Description
:---:|:---:|:---:|:---:
!|\&#33;|   |exclamation point
"|\&#34;|&quot\;|double quotes
#|\&#35;|   |number sign
$|\&#36;|   |dollar sign
%|\&#37;|   |percent sign
&|\&#38;|&amp\;|ampersand
'|\&#39;|   |single quote
(|\&#40;|   |opening parenthesis
)|\&#41;|   |closing parenthesis
*|\&#42;|   |asterisk
+|\&#43;|   |plus sign
,|\&#44;|   |comma
-|\&#45;|   |minus sign - hyphen
.|\&#46;|   |period
/|\&#47;|   |slash
:|\&#58;|   |colon
;|\&#59;|   |semicolon
<|\&#60;| \&lt; |less than sign
=|\&#61;|   |equal sign
\>|\&#62;| \&gt; |greater than sign
?|\&#63;|   |question mark
@|\&#64;|   |at symbol
[|\&#91;|   |opening bracket
\\ |\&#92;|   |back slash
]|\&#93;|   |closing bracket
^|\&#94;|   |caret - circumflex
_|\&#95;|   |underscore
`|\&#96;|   |grave accent
{|\&#123;|   |opening brace
\| |\&#124;|   |vertical bar - pipe
}|\&#125;|   |closing brace
~|\&#126;|   |equivalency sign - tilde
–|\&#8211;|   |en dash


<br><br>  

## 2. 수식

* 기본적으로 $ $ 사이에 정의된 값을 넣으면 된다. 여러개를 넣고 싶다면 아래와 같이 사용하면 된다.
```
$ \Alpha \rightarrow \Omega $
```

<br>

### 산술기호

이름|사용법|반환
:---:|:---:|:---:
크다|>|>
크거나 같다|\geq| $\geq$
작다|<|<
작거나 같다|\leq| $\leq$
같지 않다|\neq| $\neq$
<<|\ll| $\ll$
\>> |\gg| $\gg$
교집합|\cap| $\cap$
합집합|\cup| $\cup$
곱하기|\times| $\times$
나누기|\div| $\div$

<br>

### 그리스 알파벳

이름|사용법|반환
:---:|:---:|:---:
알파|\alpha| $\alpha$
베타|\beta| $\beta$
감마|\gamma| $\gamma$

<br>

### 화살표

이름|사용법|반환
:---:|:---:|:---:
위쪽 화살표|\uparrow| $\uparrow$
아래쪽 화살표|\downarrow| $\downarrow$
오른쪽 화살표|\rightarrow| $\rightarrow$
왼쪽 화살표|\leftarrow| $\leftarrow$
양옆 화살표|\leftrightarrow| $\leftrightarrow$
위아래 화살표|\updownarrow| $\updownarrow$
두 줄 위쪽 화살표|\Uparrow| $\Uparrow$
두 줄 아래쪽 화살표|\Downarrow| $\Downarrow$
두 줄 오른쪽 화살표|\Rightarrow| $\Rightarrow$
두 줄 왼쪽 화살표|\Leftarrow| $\Leftarrow$
두 줄 양옆 화살표|\Leftrightarrow| $\Leftrightarrow$
두 줄 위아래 화살표|\Updownarrow| $\Updownarrow$

<br>

### 숫자

이름|사용법|반환
:---:|:---:|:---:
3분의 2|_3^2| $_3^2$
2의 10승|2^{10}| $2^{10}$
2의 3분의 2승|2^{_3^2}| $2^{_3^2}$

<br>

그 외 기호는 다음 링크에서 참고  
[위키백과:Tex 문법](https://ko.wikipedia.org/wiki/위키백과:TeX_문법)


<br><br>

## 3. 테이블

* 헤더와 셀을 구분할 때 3개 이상의 hyphen/dash 기호가 필요하다.
* 헤더 셀을 구분하면서 :(Colons) 기호로 (열/칸) 안에 내용을 정렬할 수 있다.
* 가장 좌측과 가장 우측에는 \|(vertical bar) 기호는 생략이 가능하다.

<br>

### Syntax 마크다운 사용법  
```
테이블 생성

헤더1|헤더2|헤더3|헤더4
---|---|---|---
셀1|셀2|셀3|셀4
셀5|셀6|셀7|셀8
셀9|셀10|셀11|셀12

테이블 정렬

헤더1|헤더2|헤더3
:---|:---:|---:
Left|Center|Right
1|2|3
4|5|6
7|8|9
```

### Demonstration 실행결과  

테이블 생성

헤더1|헤더2|헤더3|헤더4
---|---|---|---
셀1|셀2|셀3|셀4
셀5|셀6|셀7|셀8
셀9|셀10|셀11|셀12

테이블 정렬

헤더1|헤더2|헤더3
:---|:---:|---:
Left|Center|Right
1|2|3
4|5|6
7|8|9

<br><br>  

## 4. 내부링크  

```
[보여지는 내용](#이동할 헤드(제목))
괄호 안의 링크를 쓸 때는 띄어쓰기는 -로 연결, 영어는 모두 소문자로 작성
```

### Syntax 마크다운 사용법  
```
[1. 특수문자](#1.-특수문자)
[2. 수식](#2-수식)
[3. 테이블](#3-테이블)  
```  

### Demonstration 실행결과  

[1. 특수문자](#1.-특수문자)
[2. 수식](#2-수식)
[3. 테이블](#3-테이블)  

<br><br>  

## 5. 체크리스트

### Syntax 마크다운 사용법
```
- [x] this is a complete item
- [ ] this is an incomplete item
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (anyunordered or ordered list supported)
```

### Demonstration 실행결과  
- [x] this is a complete item
- [ ] this is an incomplete item
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (anyunordered or ordered list supported)
