---
layout: post
title: "Collection - List, Map, Set"
date: '2020-12-09 20:25:00'
author: BBarkji
categories: java
tags: collection
cover:  "/assets/instacode.png"
---


## Collection 이란?

>* 자료구조
>* 다수의 데이터를 쉽게 처리할 수 있는 method를 제공하는 API
>* Java Collection : List, Set, Map


## List

>* 순서가 있다. 
>* 중복을 허용한다. (순서로 구분)
>* ArrayList, Vector, LinkedList
> | 구분 | 특징|
> | --- | :---: | ---:|
> | `ArrayList` | 순차적으로 데이터를 추가/삭제하는 경우 효율적 |
> | `LinkedList` | 비 순차적으로 데이터를 추가/삭제하는 경우 효율적 |

```
/* 사용 예시 */

ArrayList<String> arrayList = new ArrayList<>();

/* 값 추가 */
arrayList.add("string0");	// 0번째 index
arrayList.add("string1");	// 1번째 index
arrayList.add("string2");	// 2번째 index

/* 값 꺼내기 */
String index3 = arrayList.get(3);	// 순서가 있으니 순서를 이용해 꺼낸다.

/* 순서 정해서 값 넣기 */
arrayList.set(2, "string222");		// 2번째 값 = string222

/* 리스트 길이 */
int size = arrayList.size();

/* 2번째 값 지우기 */
arrayList.remove(2);

/* 리스트 값 다 지우기 */
arrayList.clear();

```


## Set

>* 순서가 없다.
>* 중복을 허용하지 않는다. (순서가 없으니 구분X)
>* HashSet, TreeSet


## Map

>* (key, value) 로 값 구분
>* key는 중복이 안되고, value는 중복 가능하다. (key로 구분)
>* HashMap, HashTable, TreeMap, Properties

```

HashMap<Integer, String> hashMap = new HashMap<Integer, String>();

/* 값 넣기 */
hashMap.put(0, "str0");
hashMap.put(1, "str1");
hashMap.put(2, "str2");

/* 값 꺼내기 (/
String str = hashMap.get(2);		// "str2"

/* n 번째 값 지우기 */
hashMap.remove(2);

/* hashMpa 비우기 */
hashMap.clear();

/* hashMap 전부 가져오기 */
Iterator<Integer> iterator = hashMap.keySet().iteretor();	// 해시맵의 key값을 다 가져옴
while(iterator.hasNext()) {	// 다음 값이 있는 동안은 계속 해라
	Iterator key = iterator.next();
	String string = hashMap.get(key);
	System.out.pringln(key + "번" + string);
}

 
```
