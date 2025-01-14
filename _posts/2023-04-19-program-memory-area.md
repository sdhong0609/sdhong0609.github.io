---
layout: single
title:  "프로그램의 메모리 영역"
categories: [CS, ]
tag: [cs]
---

***프로그램의 메모리 영역***
<br>
프로그램이 사용하는 메모리 영역에는 여러 가지가 있다.
<br>
<br>
<img src="/images/2023-04-19-program-memory/program-memory-area01.png" width="50%" height="50%"/>
<br>
* 코드 영역(Code): 코드(Code) 영역에는 명령어가 들어간다.
* 데이터 영역(Data): 프로그램이 컴파일되면 정적 변수나 문자열 등이 들어가는 정적 메모리 영역인 데이터(Data) 영역이 있다. JVM에서는 이 영역을 메서드 정적 영역(Method Static Area)이라고도 부른다.
* 힙(Heap): 실행 중 생성되는 객체는 동적 메모리 영역인 힙(Heap)이라는 곳에 만들어진다.
* 스택(Stack): 코드 블록인 중괄호 {} 안에서 사용한 변수나 함수 호출 블록은 임시로 쓰이는 메모리 영역인 스택(Stack)에 들어간다. 중괄호 블록이 끝나면 임시로 사용한 변수는 스택에서 제거된다.

1) 코드(code) 영역: 실행할 프로그램의 코드
2) 데이터(data) 영역: 전역 변수, 정적(static) 변수
3) 힙(heap) 영역: 런타임시 크기가 결정됨(동적할당)
4) 스택(stack) 영역: 컴파일 타임에 크기가 결정됨

JVM을 사용하는 프로그램에는 동적 메모리 영역의 객체가 사용된 뒤 아무 참조가 없으면 자동으로 삭제하는 GC(Garbage Collector)가 있다. 쓸모없는 객체를 치워 주는 일을 한다.
<br>
<br>

![program-memory-area02](/images/2023-04-19-program-memory/program-memory-area02.png)

<br>
<br>
<br>
<br>
<br>
<br>
[참고 : Do it! 코틀린 프로그래밍](http://www.yes24.com/Product/Goods/74035266)