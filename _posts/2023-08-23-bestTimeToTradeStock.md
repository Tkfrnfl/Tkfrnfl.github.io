---
layout: post
title: Best Time to Buy and Sell Stock
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


시간순으로 주어진 주가 가격 배열 값에서 가장 큰 이윤을 구하는 문제이다<br>

배열을 역순으로 보면서 가장 큰값을 계속 업데이트하고 만약 이보다 작을시 이윤값을 저장하여 최대값을 얻어낸다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/?envType=study-plan-v2&envId=top-interview-150"> 문제 링크

```java
    public int maxProfit(int[] prices) {

        int ans=0;
        int maxPrice=0;
        for(int i=0;i<prices.length;i++){
            if(prices[prices.length-i-1]>maxPrice){     //역순 순회하며 max값보다 큰지 체크
                maxPrice=prices[prices.length-i-1];
            }
            else {
                ans=Math.max(ans,maxPrice-prices[prices.length-i-1]);   //작다면 이윤 최대값 저장
            }
        }
        return ans;
    }
```