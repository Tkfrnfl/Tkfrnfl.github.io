---
layout: post
title: IE(익스플로러)에서 vue 프로젝트가 안돌아갈때
categories: [vue,javascript,typescript]
tags: [vue,javascript,typescript]
fullview: true
comments: true
---




그동안 일이 많아서 포스팅 해야지 하고 주제만 적어둔 글들이 많다.<br>
이전 커밋들 보면서 복습도 할겸 폭풍 포스팅<br><br>
vue 로 배포한 프로젝트가 크롬에선 잘 되지만 ie 환경에서 먹통이었다.(아예 흰화면만 뜸)<br>
ie는 개발할때도 볼일이 없어서 아예 생각도 안했는데 몇가지 설정을 해주면 대응 가능하다.<br><br>

참고 링크: <link href="https://realmojo.tistory.com/358"><br>
만약 babel, pollyfill이 생소하다면?<br>
<link href="https://bravenamme.github.io/2020/02/12/what-is-babel/"><br><br>
이렇게 세팅 하고도 안되는 기능들이 몇가지 생기는데<br>
1.나의 경우엔 'daumpostcode' npm 패키지가 ie에서 안되었다.<br>
    => 직접 cdn 불러와서 스크립트 작성으로 해결<br>
2.css 단에서 추가설정 해줘야할때<br>

<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>
 <script>hljs.initHighlightingOnLoad();</script>


<pre><code class="HTML"> 

@media screen and (-ms-high-contrast: active), (-ms-high-contrast: none) {
  html,
  body,
.forIe{
  margin-left: 80vw;
}
}
</code></pre>
이렇게 forIe를 따로 명시해주면된다.<br>
필자는 이렇게 했음에도 완벽하게 크롬과 동일하게 뜨지는 않았다..
