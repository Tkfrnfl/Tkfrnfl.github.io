---
layout: post
title: React type submit
categories: [react,javascript]
tags: [react,javascript]
fullview: true
comments: true
---




리액트 등 자바스크립트 환경에서 여러가지 form 에서 type = "submit" 을 사용하는경우가 있다. 이럴때 submit 후 새로고침되는 경우가 있는데, 이럴경우  
form 의 onsubmit에서 따로 핸들러를 지정해주면 된다.


<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>
 <script>hljs.initHighlightingOnLoad();</script>


<pre><code class="HTML"> 

function handleSubmit(event) {
    event.preventDefault();
  } 

&lt;Form onSubmit={handleSubmit}&gt;
  &lt;Button className="continue" type="submit"  onClick={handlers.handleContinue2}&gt; 계속 &lt;/Button&gt;
&lt;/Form&gt;

</code></pre>



