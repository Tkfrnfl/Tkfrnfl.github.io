---
layout: post
title: docker,ec2 연동시 주의점
categories: [docker,ec2]
tags: [docker,ec2]
fullview: true
comments: true
---




도커, EC2연동하면서 알게된 것<br>
1. jar파일로 배포를해주자<br>
    =>war파일로할시 별도의 web.xml이 생성되지않는다. <br>
    또한, docker-compose의 경우 tomcat과 합쳐서 쓰지않으면 별도의 docker 컨테이너 tomcat설정을 해줘야한다.
2. 인바운드 규칙설정시 TCP포트주의 <br>
    =>일반 TCP포트설정시 8080 포트가 안열리므로 사용자 지정을 해주어야한다.<br>
