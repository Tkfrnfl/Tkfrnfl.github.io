---
layout: post
title: Remove Duplicates from Sorted Array
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---

문제요약: 주어진 nums요소중 중복되는것을 지우는 문제이다. <br>

해결방법: for 문을 돌면서 이전요소와 다를경우 nums를 바꿔주고  ans를 증가시켰다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int k=0;
        for(int i=0;i<nums.length;i++){
            if(nums[i]==val){
                nums[i]=999;
                k++;
            }
        }
        Arrays.sort(nums);
        return nums.length-k;
    }
}
```