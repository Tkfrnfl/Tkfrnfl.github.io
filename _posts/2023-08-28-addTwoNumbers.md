---
layout: post
title: Add Two Numbers
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제요약: 주어진 2개의 노드리스트를 각각 수의 자리수로 보고 덧셈을하여 노드리스트에 그 값을 저장하는 문제이다.<br>


해결방법: 두개의 노드 값을 가져와서 더하면서 10 초과시 up을 조정하는 방식으로 구현하였다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/add-two-numbers/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
    ListNode before;
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {

        ListNode ans= new ListNode();
        ListNode next= ans;
        int up=0;
        while (l1!=null||l2!=null){

            if(l1!=null&&l2!=null){         //2개다  null 아닐시
                int sum=l1.val+ l2.val+up;
                if(sum>=10){
                    up=1;
                }
                else {
                    up=0;
                }
                next= insertNode(sum%10,next);
            }
            else if(l1!=null){
                int sum=l1.val+up;
                if(sum>=10){
                    up=1;
                }
                else {
                    up=0;
                }
                next= insertNode(sum%10,next);
            }
            else {
                int sum=l2.val+up;
                if(sum>=10){
                    up=1;
                }
                else {
                    up=0;
                }
                next= insertNode(sum%10,next);
            }
            if(l1!=null){               //각각 null 아닐때만 다음거로 재할당
                l1=l1.next;
            }
            if(l2!=null){
                l2=l2.next;}

        }
        if(up==1){                      //맨 마지막 다음 자리수로 넘어갈 경우 노드 추가
            next=insertNode(1,next);
        }
        before.next=null;
        return ans;
    }
    public ListNode insertNode(int data, ListNode now){
        before=now;                                 //바로 직전노드 기억
        ListNode newNode = new ListNode(data);    // 새로운 노드 생성
        now.val=data;
        now.next=newNode;

        return  newNode;
    }
```