---
layout: post
title: "Java UUID api"
date: '2021-01-15 15:00:00'
author: BBarkji
categories: java
tags: java
cover:  "/assets/instacode.png"
---



# Java UUID api (Java 8기준)
<br/>
<br/>
<br/>
* class UUID는 java.util.UUID 패키지에 속한다.
* Serializable, Comparable<UUID> 인터페이스를 상속한다.
<br/>
<br/>
<br/>
### Serializable      
serialized or deserialized 하기 위해서는 꼭 상속해야 하는 인터페이스다. 데이터 구조나 오브젝트 상태를 다른 저장 환경에서도 사용할 수 있는 상태로 바꾸어주거나(serialized;직렬화;) 또는 다시 원상 복귀해야 할 때 상속해야 하는 인터페이스.
<br/>
<br/>
<br/>
### Comparable<UUID>   
Comparable<T> 인터페이스를 상속하는 리스트 객체는 Collections.sort (and Arrays.sort)에 의해 자동으로 오름차순 정렬 된다.    
<br/>
<br/>
<br/>
class UUID가 이 둘을 상속하므로, UUID api를 활용하면,
데이터 구조나 오브젝트 상태를 직렬화 할 수 있으며, 결과 값은 오름차순으로 자동정렬 된다.
<br/>
<br/>
<br/>
한편,
<br/>
<br/>
<br/>
* uuid class는 변경 불가능한(immutable) 128bit의 고유 식별자(uique identifier)를 만든다. (=128비트 암호화)
* 형태는 아래와 같다.                 
0xFFFFFFFF00000000 time_low<br/>
0x00000000FFFF0000 time_mid<br/>
0x000000000000F000 version<br/>
0x0000000000000FFF time_hi<br/>
0xC000000000000000 variant<br/>
0x3FFF000000000000 clock_seq<br/>
0x0000FFFFFFFFFFFF node<br/>
<br/>
<br/>
<br/>
* class UUID의 메소드      
| Modifier and Type | Method | Description |
| --- | ---- | ----- |
| int | clockSequence() | The clock sequence value associated with this UUID. |
| int | compareTo(UUID val)| Compares this UUID with the specified UUID. |
| boolean | equals(Object obj) | Compares this object to the specified object. |
| static UUID | fromString(String name) | Creates a UUID from the string standard representation as described in the toString() method. |
|long|getLeastSignificantBits()|Returns the least significant 64 bits of this UUID's 128 bit value.|
|long|getMostSignificantBits()|Returns the most significant 64 bits of this UUID's 128 bit value.|
|int|hashCode()|Returns a hash code for this UUID.|
|static UUID|nameUUIDFromBytes(byte[] name)|Static factory to retrieve a type 3 (name based) UUID based on the specified byte array.|
|long|node()|The node value associated with this UUID.|
|static UUID|randomUUID()|Static factory to retrieve a type 4 (pseudo randomly generated) UUID|
|long|timestamp()|The timestamp value associated with this UUID.|
|String|toString()|Returns a String object representing this UUID.|
|int|variant()|The variant number associated with this UUID.|
|int|version()|The version number associated with this UUID.|      
<br/>
<br/>
<br/>
* 또한 java.lang.Object 를 상속받아 아래 메소드도 쓸 수 있다.
clone, finalize, getClass, notify, notifyAll, wait 