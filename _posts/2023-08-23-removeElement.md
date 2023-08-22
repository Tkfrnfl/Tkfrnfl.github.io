---
layout: post
title: Remove Element
categories: [leetcode]
tags: [leetcode]
fullview: true
comments: true
---


원티드 온보딩 과제로 푼 리트코드 문제<br>
주어진 nums요소중 val 과 같은것을 지워내는 문제이다.<br>
for 문을 돌면서 val 과 같을경우 해당요소를 바꿔주고 마지막에 정렬을 했다.<br>


<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>
 <script>hljs.initHighlightingOnLoad();</script>


<pre><code class="HTML"> 
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
</code></pre>
