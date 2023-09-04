---
layout: post
title: Search in Rotated Sorted Array
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제 요약: 정렬되었으나 옆으로 k만큼 움직여진 배열에서 주어진 target을 찾는 문제이다.<br>

해결방법:  우선 k를 이진탐색으로 찾은다음 target과 배열의 상태에 따라 2가지로 나누어 이진탐색을 추가로 하였다.<br>

대부분 통과하였으나 시간부족으로 세부 테스트 케이스 통과를 못하였다.<br>


<a class="btn btn-default" href="https://leetcode.com/problems/search-in-rotated-sorted-array/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
     public int search(int[] nums, int target) {
        int startk=0;
        int endk=nums.length-1;
        int midk=(startk+endk)/2;
        int ans=-1;
        int k=0;

        while (startk<=endk &&midk>=0){           //k찾기
            if(nums[midk]>nums[endk]){
                startk=midk+1;
            }
            else {
                endk=midk-1;
            }
            midk=(startk+endk)/2;
            k=midk;
        }
        if(k==0){
            k=nums.length-1;
        }
        System.out.println(k);
        if(target<nums[0]){         //k찾은후  target과의 비교
            int start=k;
            int end=nums.length-1;
            int mid =(start+end)/2;

            while (start<=end){
                if(nums[mid]==target){
                    ans=mid;
                    break;
                }
                if(nums[mid]<target){
                    end=mid-1;

                }
                else {
                    start=mid+1;
                }
                mid =(start+end)/2;
            }
            if(nums[mid]==target){
                ans=mid;
            }
        }else {
            int start=0;
            int end=k;
            int mid =(start+end)/2;

            while (start<=end){
                if(nums[mid]==target){
                    ans=mid;
                    break;
                }
                if(nums[mid]<target){
                    start=mid+1;

                }
                else {
                    end=mid-1;
                }
                mid =(start+end)/2;
            }
            if(nums[mid]==target){
                ans=mid;
            }
        }
    return ans;
    }
```