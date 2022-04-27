---
layout: post
title: Dynamodb 항목 검색이 일부만 될때
categories: [dynamodb,python]
tags: [dynamodb,python]
fullview: true
comments: true
---


dynamodb에서 항목을 검색 할때(scan,query 등) 항목수가 많은경우 검색이 다 안되는 경우가 있다.<br>
이럴경우 다음과 같이 해주면 된다.<br>

<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>
 <script>hljs.initHighlightingOnLoad();</script>


<pre><code class="HTML"> 

    #1차 스캔
    email_list=table_orders.scan()
    data_after=email_list['Items']

    #1mb 초과 2차 스캔 반복
    while 'LastEvaluatedKey' in email_list:
        email_list=table_orders.scan()
        data_after.extend(email_list['Items'])
</code></pre>

scan시 다음 결과가 있다면 'LastEvaluatedKey'를 반환하는데,<br>
이때 스캔을 반복하여 저장해주면 전체 항목 리스트 검색이 가능하다.<br>
