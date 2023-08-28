---
layout: post
title: Valid Palindrome
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제 요약: 주어진 문장이 회문인지를 판별하는 문제이다. 회문이란 특수문자를 제외하고 영문자+숫자로 앞,뒤로 읽어도 같은 문장을 뜻한다.<br>

해결방법: 처음엔 char로 일일히 검사하려했으나 비효율적이여서 정규식을 사용하여 문장을 정리하고, 회문여부를 체크하였다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/valid-palindrome/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
    public boolean isPalindrome(String s) {
        boolean ans=true;
//        for(int i=0;i<s.length();i++){
//            char c= s.charAt(i);
//            if (!(c >= 'A' && c <= 'Z') && !(c >= 'a' && c <= 'z')&&!(c>='0' && c<='9')) {
//                s=s.substring(0,i)+s.substring(i+1);
//            }
//        }
        s=s.replaceAll("[^a-zA-Z0-9]","");  //정규식 사용하여 특수문자 정리
        s=s.toLowerCase();
        s=s.replaceAll(" ","");
        System.out.println(s);
        for(int i=0;i<Math.floor(s.length()/2);i++){        //회문판별
            if(s.charAt(i)!=s.charAt(s.length()-1-i)){
                ans=false;
            }
        }
        return ans;
    }
```