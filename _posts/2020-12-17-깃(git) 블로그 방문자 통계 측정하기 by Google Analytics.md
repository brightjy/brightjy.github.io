---
layout: post
title: "깃(git) 블로그 방문자 통계 측정하기 by Google Analytics"
date: '2020-12-17 12:00:00'
author: BBarkji
categories: git
tags: 깃블로그, 깃페이지, 깃헙, git
cover:  "/assets/octoCat.PNG"
---



# 깃(git) 블로그 방문자 통계 측정하기 by Google Analytics  
  
깃 블로그는 정적인 페이지라 알아서(?) 방문자 수를 추적해준다든가 하지 못한다. 네이버 블로그를 주로 쓰다가 기술 블로그를 깃에 만들면서 유일하게 아쉬운 점.   
깃 블로그에서 방문자 통계를 추적하는 방법을 찾아보니 대부분 구글 애널리틱스를 이용하고 있었다. (다른 더 좋은 방법이 있으면 알려주세요~) 당장은 나도 구글 애널리틱스에 내 깃 블로그를 연동하여 방문자 통계를 얻어보기로.
  
  
  
### Step 1. 구글 애널리틱스 계정 만들기 
**라** 대학 **떼** 는 나름 구글 애널리틱스를 사용하는 게 막 붐이 일때라 그런지 계정이 이미 있었음. 
  
  
### Step 2. 계정 속성 설정하기  
관리 > 속성설정 > 기본 URL 에 깃 블로그 주소를 넣는다. 
![ga속성설정](/assets/ga.PNG)  
  
  
### Step 3. 깃 블로그 설정에 반영  
이 부분이 jekyll 종류에 따라 좀 다른 것 같더라. 어떤 사람은 _config.yml 파일에 **google-analytics: 추적ID** 만 넣어도 됐다는데 나는 이것은 되지 않았다. 대신 아래 방법으로 하니까 됐다.  
  
1) _includes 폴더에 ga.html 추가   
ga.html 안에는 관리 > 추적정보 > 추척코드 의 범용 사이트 태그(gtag.js)를 넣는다.  
```
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-50796696-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', '추적ID');
</script>
```
  
  
2) _layouts 폴더의 default.html 에 범용 사이트 태그(gtag.js) 추가  
이 때 <body> 여기에 </body> 넣어야 한다. 처음에 body 밖에 넣으니 안되었음.  



### Step 4. 잘 적용됐는지 애널리틱스 홈에서 확인한다.  
제대로 적용되었다면, 내 깃 블로그에 들어간 후, 애널리틱스 홈 화면을 보면 분당 페이지 조회 수치가 올라간다.   
![ga테스트](/assets/gaTest.PNG) 
  
  
  

