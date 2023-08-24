---
layout: post
title: Best Time to Buy and Sell Stock II
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


문제요약: 시간순으로 주어진 주가 배열에서 주식을 하나에 한번씩만 소유한채 거래하여 최대 이윤을 구하는 문제이다.<br>

해결방법: 맨 앞에서부터 주가가 이전보다 작은경우 before에 저장하고 before보다 큰경우 그 차익을 profit에 저장하여 최종이윤을 구했다.<br>

<a class="btn btn-default" href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/"> 문제 링크

```java
class Solution {
    public int maxProfit(int[] prices) {
        int before=prices[0];
        int profit=0;

        for(int i=1;i<prices.length;i++){
            if(before>prices[i]){
                before=prices[i];           // 이전보다 작을시 그 값을 before에 저장
            }
            else {
                profit+=(prices[i]-before);     // 이윤 계산하여 업데이트
                before=prices[i];
            }
        }

        return  profit;
    }
}
```