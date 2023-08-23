---
layout: post
title: Majority Element
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


주어진 배열 요소중 과반수를 찾는문제이다.<br>

정렬한후에 요소별로 개수를 체크하면서 과반수 될시 ans 리턴하였다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/majority-element/description/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
 public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        int count =1;
        int before=nums[0];
        int ans=nums[0];

        for(int i =1; i<nums.length;i++){
            if(before==nums[i]){
                count++;
                if(count>(nums.length/2)){
                   ans= nums[i];
                   break;
                }
            }
            else {
                count=1;
                before=nums[i];
            }
        }
        return  ans;
    }
```