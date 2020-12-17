---
layout: post
title: "cannot be resolved 외 JSP 이유 모를 에러 해결하기 (진행중)"
date: '2020-12-17 10:00:00'
author: BBarkji
categories: 에러
tags: 에러
cover:  "/assets/instacode.png"
---



# cannot be resolved 외 JSP 이유 모를 에러 해결하기 (진행중)


이번에 새로 시작한 프로젝트는 기존에 운영 중인 프로그램에 새로운 서비스를 더하는 것이다. 그런데 로컬에 셋팅 하고나니 JSP Problem 타입의 에러가 우수수수 (57개 쯤) 쏟아졌다. 프로그램을 구동하는데는 큰 영향 주지 않는 '무늬만 에러'인 것 같긴 한데 시간적 여유도 있고 해서 해결해보려고 폭풍 검색해 하나씩 적용해보고 있다. 하지만 인터넷에서 이야기하는 대부분의 해결책이 먹히지 않고 있는 상황. 


**아래는 내가 해보았지만, 내 경우는 효과가 없었던 방법들이다.**


### JRE 재설정  
Project > properties > Java Build Path > Libraries > 기존에 있던 JRE System Library 삭제 > Add Library > JRE System Library > Alternate JRE > 본인 버전에 맞는 jdk (e.g. jdk 1.8.0) 선택하여 추가


### Project Facets 톰캣 서버 추가  
Project > properties > Project Facets > Configuration : <custom> > Runtimes 탭 > 톰캣 서버 체크 


### Validation 설정 변경  
Project > properties > Validation > JSP Syntax > Custom actions > TagExtraInfo~ Ignore로 변경 (물론 여기서 모든걸 ignore로 바꾸면 안뜨겠지만...)



그 외 기타 등등 구글에서 검색한 글이 다 보라색이 되도록 찾고 있다. 해결되면 추가하것음...





