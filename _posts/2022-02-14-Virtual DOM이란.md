---
layout: post
title: "Virtual DOM이란?"
date: '2022-02-14 23:30:00'
author: BBarkji
categories: React
tags: VirtualDOM
cover:  "/assets/instacode.png"
---



React를 배우자 - Virtual DOM이란?
==============


Virtual DOM(a.k.a. VDOM)은 UI의 이상적인 또는 "가상"적인 표현을 메모리에 저장하고, ReactDOM과 같은 라이브러리에 의해 "실제 "DOM과 동기화하는 프로그래밍 개념이다. 이걸 "재조정(Reconciliation)"이라고 한다. 



재조정(Reconciliation)

React는 선언적  API를 제공하기 때문에 갱신이 될 때마다 매번 무엇이 바뀌었는지를 걱정할 필요가 없다.



이런 접근 방식이 React의 선언적 API를 가능하게 한다. React에게 원하는 UI 상태를 알려주면, DOM이 그 상태와 일치하도록 한다. 

Virtual DOM은 특정 기술이라기보다는 패턴에 가깝기 때문에 사람마다 의미하는 바가 다르다. 보통은 사용자 인터페이스를 나타내는 객체이기 때문에 React elements(React 앱의 가장 작은 단위. React DOM은 React 엘리먼트와 일치하도록 DOM을 업데이트 한다.)와 연관된다. 


한 줄 요약:

"Virtaul DOM은 유저가 보고 있는 UI와 실제 UI와의 변경 사항을 체크하여, 변경된 부분만 '재조정'할 수 있도록 React.js 가 메모리에 보관하고 있는 UI 사본이다."



