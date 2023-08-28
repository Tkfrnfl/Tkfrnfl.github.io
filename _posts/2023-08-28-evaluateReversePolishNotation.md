---
layout: post
title: Evaluate Reverse Polish Notation
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제요약: 역폴란드식 계산방법으로 주어진 연산을 수행하는 문제이다.<br>


해결방법: 입력받는 수를 stack에 저장해나가면서 연산자가들어올 경우  역폴란드식 계산을 수행하였다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/evaluate-reverse-polish-notation/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
    public int evalRPN(String[] tokens) {
        Stack<Integer> nums=new Stack();

        for(int i=0;i<tokens.length;i++){
            if(isNumeric(tokens[i])){                   //숫자일경우
                nums.add(Integer.parseInt(tokens[i]));
            }
            else {                                      //연산자일경우
                int a=nums.pop();
                int b=nums.pop();
                int c=0;
                if(tokens[i].equals("+")){
                    c=b+a;
                }
                if(tokens[i].equals("-")){
                    c=b-a;
                }
                if(tokens[i].equals("*")){
                    c=b*a;
                }
                if(tokens[i].equals("/")){
                    c=b/a;
                }
                nums.push(c);                       //계산값을 push;
            }
        }
        return nums.pop();
    }
    public static boolean isNumeric(String s) {
        try {
            Double.parseDouble(s);
            return true;
        } catch (NumberFormatException e) {
            return false;
        }
    }
```