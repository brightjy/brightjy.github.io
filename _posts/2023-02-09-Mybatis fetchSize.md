---
layout: post
title: "MyBatis 성능 향상 방법 - fetchSize"
date: '2023-02-09 10:00:00'
author: BBarkji
categories: java
tags: spring, mybatis, sql, query
cover:  "/assets/instacode.png"
---


# MyBatis 성능 향상 방법?

사실 마이바티스 쓰면서 '왜 JPA 아니고 아직도 마이바티스야?'했지 마이바티스도 성능 향상을 위해 뭔가 설정을 해줄 수 있는지 몰랐다. 역시 새로운 것도 좋지만 이미 쓰고 있는 것부터 잘 알아야해... 

그러다 fetchSize를 보았고, 잊지 않기위해 간단히 정리한다.
아 참고로 fetchSize는 오라클에서만 가능하다. 



### 대량데이터 조회 시 fetchSize


예) 

```
<select id="selectExample" parameterType="String" resultType="map" fetchSize="50000">
    SELECT  * 
    FROM    EXAMPLE_TABLE
</select>
```


* fetchSize는 한 번에 조회해오는 로우의 수인데, 기본적으로 아무 설정을 하지 않으면 10개 씩 가져온다. 한 번에 가져오는 양을 늘리면 WAS <-> DB 간 트래픽을 줄여 성능이 향상될 수 있다고 한다.


