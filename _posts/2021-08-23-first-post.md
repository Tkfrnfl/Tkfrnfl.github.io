---
layout: post
title: 몰랐던 html태그들의 기능
categories: [html]
tags: [html]
fullview: true
comments: true
---




첫 포스트입니다. 프론트 작업을하며 몰랐던 태그들과 기능들을 정리
해보았습니다.

### select
<div>드롭바를 만들어주는 태그입니다. 내부에 option  태그를 포함합니다.</div>

### option
<div>드롭바 항목들을 만들어주는 태그입니다.</div>

**example**

<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>
 <script>hljs.initHighlightingOnLoad();</script>



<pre><code class="HTML"> 
 <select id="select" className="form-control">
            <option >Site</option>
            <option>Site2</option>
</select>

 &lt;select id="select" className="form-control"&gt;
            &lt;option &gt;Site&lt;/option&gt;
            &lt;option&gt;Site2&lt;/option&gt;
&lt;/select&gt;
</code></pre>

### svg
<div>svg 형식의 도형을 만들어주는 태그입니다.<br>view box 기능을 활용하여 도형내의 위치를 지정할 수도 있습니다.</div>

**example**

<pre><code class="HTML"> 
  <svg width="100%" viewBox="0 0 300 50">
    <text x="10%" y="70%" fill="#ffffff" font-family="'Arial', cursive">텍스트
    </text>
  </svg>

   &lt;svg width="100%" viewBox="0 0 300 50"&gt;
     &lt;text x="10%" y="70%" fill="#ffffff" font-family="'Arial', cursive"&gt;텍스트
     &lt;/text&gt;
   &lt;/svg&gt;


</code></pre>





