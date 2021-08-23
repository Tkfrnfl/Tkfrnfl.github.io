---
layout: post
title: 몰랐던 html태그들의 기능
categories: [html]
tags: [html]
fullview: true
comments: true
---

<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css"></link> <script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script> <script>hljs.initHighlightingOnLoad();</script>


첫 포스트입니다. 프론트 작업을하며 몰랐던 태그들과 기능들을 정리
해보았습니다.

### select
<div>드롭바를 만들어주는 태그입니다. 내부에 option  태그를 포함합니다.</div>

### option
<div>드롭바 항목들을 만들어주는 태그입니다.<div>

**example**


<pre><code class="HTML"> 
<select id="select" name="family_site" className="form-control" onChange={this.handleFamilyState} defaultValue="">
            <option value="" disabled>Family Site</option>
            <option>Themusio</option>
</select>
</code></pre>





