---
layout: post
title: "target is undefined 오류"
date: '2021-02-22 09:30:00'
author: BBarkji
categories: javascript
tags: javascript,jquery
cover:  "/assets/instacode.png"
---



# target is undefined 오
<br/>
<br/>
<br/>
상황: <form:form>을 사용해서 데이터를 넘길 때 웹이랑 웹뷰(모바일)이랑 코드가 똑같은데 웹뷰에서만 target을 못찾는다는 오류가 계속 나왔다. 실제로 alert을 띄워봐도 못찾음. 
<br/>
아무리 아무리 봐도 코드에 다른 부분이 없는데 안되서 이 것 때문에 몇 시간을 날리고... 주말에도 계속 생각나고... 꿈에도 나오고...
<br/>
이것과 관련된 오류를 다 찾아봐도 내 이야기는 아닌 것 같고....
<br/>
<br/>
<br/>
그러다 오늘 우연히 발견한 오류의 찐 원인....
<br/>
<br/>
<br/>
<%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
<br/>
모바일 뷰에만 이게 빠져있었다. ^_^.................
<br/>
<br/>
<br/>
이런 어이없는 실수인 경우도 있으니 참고하시길... 
<br/>
<br/>
<br/>
