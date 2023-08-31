---
layout: post
title: Hash Table 구현 Linear Probing 방식으로 Hash Table을 구현
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제요약: 해쉬 테이블을 선형 탐사식으로 구현해보는 문제이다.<br>


해결방법: 테이블을 가정한 배열을 만들고 순차탐색해가는 방식으로 구현하였다.<br>

```java
    int capacity=1000;
    int[] ht =new int[capacity];

    public void insert(int data){
        int index=data%capacity;

        for(int i=0;i<capacity;i++){
            index+=i;
            if(ht[index]==0){           //자리가 비었을시 삽입
                ht[index]=data;
                break;
            }
        }
    }

    public boolean search(int data){
        int index=data%capacity;

        for(int i=0;i<capacity;i++){
            index+=i;
            if(ht[index]==data){        //데이터가 같을시  true

                return true;
            }
        }

        return false;                   //다 돌고도 없을시  false
    }

    public void delete(int data){
        int index=data%capacity;

        for(int i=0;i<capacity;i++){
            index+=i;
            if(ht[index]==data){            //데이터가 있을시 삭제
                ht[index]=0;
            }
        }

    }
```