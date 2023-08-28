---
layout: post
title: Merge Two Sorted Lists
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제요약: 주어진 오름정렬된 노드리스트 2개의 값을 비교하여 하나의 노드리스트로 병합하는 문제이다.<br>


해결방법: 각 노드 의 값을 비교하여 작은값을 먼저 넣고, 큰 값을 노드를 먼저 넣은 노드.next보다 작을때까지 넣어주었다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/merge-two-sorted-lists/"> 문제 링크

```java
   ListNode before;
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode ans= new ListNode();
        ListNode next= ans;

        if(list1==null&&list2==null){           // new ListNode();를 생성하면 val 0이 자동으로 들어가므로 미리 분기
            return null;
        }

        while (list1!=null&& list2!=null){          //양쪽 노드가 다 순회끝나지 않을경우
            if(list1.val<=list2.val){
                next=insertNode(list1.val, next);
                while (list1.next!=null&&list2!=null&& list2.val<list1.next.val){
                    next=insertNode(list2.val, next);
                    list2=list2.next;
                }
                list1=list1.next;
            }
            else {
                next=insertNode(list2.val, next);
                while (list2.next!=null&&list1!=null&& list1.val<list2.next.val){
                    next=insertNode(list1.val, next);
                    list1=list1.next;
                }
                list2=list2.next;
            }
        }
        while (list1!=null){                        //한쪽이라도 순회가 끝난경우 나머지 노드를 차례로 넣어준다.
            next=insertNode(list1.val, next);
            list1=list1.next;
        }
        while (list2!=null){
            next=insertNode(list2.val, next);
            list2=list2.next;
        }
        if(before!=null){
            before.next=null;
        }

        return ans;
    }
    public ListNode insertNode(int data, ListNode now){
        before=now;
        System.out.println(data);
        ListNode newNode = new ListNode(data);    // 새로운 노드 생성
        now.val=data;
        now.next=newNode;

        return  newNode;
    }
```