---
layout: post
title: Remove Duplicates from Sorted Array II
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---

주어진 배열에서 3개이상 중복된 요소를 제거하는 문제이다.<br>

count 수를 체크하여 3개이상 될시 값을 수정하고 아닐시 ans  값을 증가하여 요소개수 체크하였다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
 public int removeDuplicates(int[] nums) {
        int before= nums[0];
        int count=0;
        int ans=0;

        for(int i=1; i<nums.length;i++){
            if(before==nums[i]){

                if(count>0){     //3개 이상될시 큰값으로 수정
                    nums[i]=10001;
                }
                else{
                    count++;
                    ans++;
                }
            }
            else {
                count=0;
                before=nums[i];
                ans++;
            }
        }
        Arrays.sort(nums);
        return ans+1;
    }
```