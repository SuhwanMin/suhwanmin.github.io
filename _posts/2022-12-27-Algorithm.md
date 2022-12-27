---
title: Java 알고리즘 문제풀이
author: Suhwan
date: 2022-12-27 
categories: [Java 알고리즘 풀이, 프로그래머스]
tags: [typography]
math: true
mermaid: true
toc : true                  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. 
toc-sticky : true           # ture 로 해주면 포스트의 목차가 보이게 된다.
                            # 목차가 스크롤을 따라 움직인다.
# image:
#   path: /commons/devices-mockup.png
#   width: 800
#   height: 500
#   alt: Responsive rendering of Chirpy theme on multiple devices.
---
프로그래머스 문제풀이
===
크기가 작은 부분문자열
---

<br>

**문제 설명**

> 숫자로 이루어진 문자열 t와 p가 주어질 때, t에서 p와 길이가 같은 부분문자열 중에서, 이 부분문자열이 나타내는 수가 p가 나타내는 수보다 작거나 같은 것이 나오는 횟수를 return하는 함수 solution을 완성하세요.

> 예를 들어, t="3141592"이고 p="271" 인 경우, t의 길이가 3인 부분 문자열은 314, 141, 415, 159, 592입니다. 이 문자열이 나타내는 수 중 271보다 작거나 같은 수는 141, 159 2개 입니다.

<br>

**제한 사항**

> - 1 ≤ p의 길이 ≤ 18
> - p의 길이 ≤ t의 길이 ≤ 10,000
> - t와 p는 숫자로만 이루어진 문자열이며, 0으로 시작하지 않습니다.

**ex)**

|t|p|result|
|---|---|:---:|
|"3141592"|"271"|2|
|"500220839878"|"7"|8|

<br>

**소스코드**

```java
class Solution {
    public int solution(String t, String p) {
        int tleng = t.length();
        long pvalue = Long.parseLong(p);
        int pleng = p.length();
        int answer = 0;
        
        for(int i=0; i<=tleng-pleng; i++) {
            long tvalue = Long.parseLong(t.substring(i,i+pleng));
            if(tvalue <= pvalue) {
                answer++;
            }
        }
        return answer;
    }
}
```
