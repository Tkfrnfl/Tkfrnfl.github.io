---
layout: post
title: Longest Substring Without Repeating Characters
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제요약: 주어진 문자열의 하위배열중 문자가 안겹치는 가장 긴 하위배열을 찾는 문제이다.<br>


해결방법: 창문 슬라이싱 기법을 이용하여 int 형 char 인덱스 배열에  겹치지 않을때까지 end를 늘리고,<br>

친다면 end 가 다시 배열에 표시되지 않을때까지 start를 늘려가며 탐색을 하였다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/longest-substring-without-repeating-characters/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
   public int lengthOfLongestSubstring(String s) {
        int ans=0;
        int start=0;
        int end=0;

        int[] check=new int[999];

        while (end<s.length()){
            if(check[s.charAt(end)]==0){        // 겹치지 않는다면 배열에 표시
                check[s.charAt(end)]=1;
            }
            else {                              //겹친다면
                ans=Math.max(ans,end-start);
                while (check[s.charAt(end)]!=0){    //겹치지 않을때까지 start 늘려가며 탐색
                    //System.out.println(start);
                    check[s.charAt(start)]=0;
                    start++;
                }
                check[s.charAt(end)]=1;         // 탐색완료후 index에 표시
                end++;
                continue;
            }

            end++;
            ans=Math.max(ans,end-start);
        }
        return ans;
    }
```