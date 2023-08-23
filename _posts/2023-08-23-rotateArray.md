---
layout: post
title: Rotate Array
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


주어진 nums 배열을 우측으로 k만큼 이동시키는 문제이다.<br>

 k를 nums의 길이 만큼으로 나눈 나머지만큼 이동시켜서 해결하였다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/rotate-array/description/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
  public void rotate(int[] nums, int k) {
        k=k%nums.length;
        int[] temp=new int[nums.length];

        for(int i=0;i<nums.length;i++){
            int j=i+k;
            if(j>=nums.length){         //배열길이 초과시 그만큼    보정하여 temp에 저장
                j-= nums.length;
            }
            temp[j]=nums[i];
        }
        for(int i=0;i<nums.length;i++){
            nums[i]=temp[i];
        }

    }
```
