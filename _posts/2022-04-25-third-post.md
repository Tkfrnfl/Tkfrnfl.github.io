---
layout: post
title: React type submit
categories: [react,javascript]
tags: [react,javascript]
fullview: true
comments: true
---




프론트 작업을 하다보면 cors 오류가 발생할 때가 있다.<br>
이럴땐 크게 2가지 이유가 있을수 있는데,<br>
1.실제로 서버에서 cors 오류가 발생한경우<br>
2.프론트 혹은 백엔드상 로직 오류<br> <br>

1번의 경우, vue 에선 vue.config.js 파일을 다음과 같이 수정해주면 된다.



<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>
 <script>hljs.initHighlightingOnLoad();</script>


<pre><code class="HTML"> 

module.exports = {
  transpileDependencies: ['vuetify','vuetify-dialog','vuex-persist'],
  lintOnSave : false,
  assetsDir: process.env.BASE_URL,


  devServer: {
    proxy:'https://api.com',
    proxy:'https://api2.com'
  },}

</code></pre>

2번의 경우 대부분 백 쪽의 오류인 경우가 많으며,<br> 
백을 직접 건드리는 경우 단순오류조차 cors에러로 response될수 있으니 로그를 확인해보는것이 좋다.