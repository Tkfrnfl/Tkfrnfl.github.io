---
layout: post
title: Two Sum II - Input Array Is Sorted
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제요약: 주어진 숫자배열에서 두 수의 합이 target이 되는 숫자 인덱스를 찾는 문제이다.<br>


해결방법:오름정렬되어있으므로,for문 그 다음인덱스를 start 마지막 end  중간을 mid 로 두고 이진탐색을하여 target 과의 비교를 진행한다.<br>

이때, 테스트 제출시  System.out.println 포함되면 time limit 걸리므로 주의!!<br>

<a class="btn btn-default" href="https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
    public int[] twoSum(int[] numbers, int target) {
        int[] ans=new int[2];

        for(int i=0;i<numbers.length;i++){

            int start=i+1;
            int end=numbers.length-1;
            int mid= (start+end)/2;

            while (start<=end){                 //end와 작거나 같을때 동안
               // System.out.println(mid);              // time limit 주의!!
                if(numbers[mid]+numbers[i]<target){
                    start=mid+1;                        /// start 를 mid 보다 크게 설정
                    mid=(start+end)/2;
                }
                else if(numbers[mid]+numbers[i]==target){
                    ans[0]=i+1;
                    ans[1]=mid+1;
                    return ans;
                }
                else {
                    end=mid-1;              //end를 mid보다 작게 설정
                    mid=(start+end)/2;
                }
            }


        }
        return ans;
    }
```