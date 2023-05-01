---
layout: single
title:  "공부 정리: Chapter02 변수와 자료형,연산자 - Section02 변수와 자료형"
categories: [Kotlin Basic, ]
tag: [kotlin]
---

프로그램이 실행될 때 변수, 함수, 객체 등은 모두 메모리에 올라간다. 하지만 메모리 공간은 제한적이다. 좋은 프로그래머는 제한된 메모리 공간을 효율적으로 사용하기 위해 다양한 형태의 변수를 골라 프로그램을 만든다. 이때 변수의 모양(또는 성질)을 자료형이라고 부른다.

![chapter02-section02-01](/images/2023-04-27-chapter02-section02/chapter02-section02-01.png)

변수란 값을 넣을 수 있는 상자 정도로 비유할 수 있다. 위의 그림은 변수와 변수에 담긴 값을 표현한 그림이다. 변수는 상자이고 상자에 적힌 Int, String, Float은 상자에 담긴 값의 성질인 자료형을 의미한다.

<br>
<br>

**변수를 선언하고 자료형 추론하기**

![chapter02-section02-02](/images/2023-04-27-chapter02-section02/chapter02-section02-02.png)

코틀린은 자료형을 지정하지 않고 변수를 선언하면 변수에 할당된 값을 알아보고 알아서 자료형을 지정할 수 있다. 이것을 "자료형을 추론한다"라고 한다. 하지만 값을 할당하지 않으면서 변수를 선언하려면 자료형을 반드시 지정해야 한다.

<br>
<br>

**코틀린의 자료형은 참조형 자료형을 사용한다**

기본형(Primitive Data Type): 가공되지 않은 순수한 자료형으로 프로그래밍 언어에 내장

참조형(Reference Type): 객체를 생성하고 동적 메모리 영역에 데이터를 둔 다음 이것을 참조하는 자료형

코틀린에서는 참조형만 사용함. 참조형으로 선언한 변수는 성능 최적화를 위해 코틀린 컴파일러에서 다시 기본형으로 대체된다.

<br>
<br>

**기본형과 참조형의 동작 원리**

[기본형 자료형과 참조형 자료형의 동작 원리](https://sdhong0609.github.io/cs/primitive-data-type-and-reference-type/)

<br>
<br>

**정수 자료형**

![chapter02-section02-03](/images/2023-04-27-chapter02-section02/chapter02-section02-03.png)

![chapter02-section02-04](/images/2023-04-27-chapter02-section02/chapter02-section02-04.png)

<br>
<br>

**실수 자료형**

![chapter02-section02-05](/images/2023-04-27-chapter02-section02/chapter02-section02-05.png)

실수의 개수는 무한하지만 메모리 공간은 유한하다. 그래서 메모리에 모든 실수를 표현하기는 어렵다. 이러한 메모리의 단점을 극복하기 위해 실수를 표현할 때 부동 소수점(Floating-point) 방식을 사용한다. 부동 소수점 방식은 실수를 가수와 지수로 나누어 표현하는 방식이다.

![chapter02-section02-06](/images/2023-04-27-chapter02-section02/chapter02-section02-06.png)
위의 그림은 수학과 컴퓨터에서 부동 소수점을 표현해는 방식을 나타낸 것.

<br>
<br>

**논리 자료형**

![chapter02-section02-07](/images/2023-04-27-chapter02-section02/chapter02-section02-07.png)

<br>
<br>

**문자 자료형**

![chapter02-section02-08](/images/2023-04-27-chapter02-section02/chapter02-section02-08.png)

컴퓨터가 문자 자료형 값을 저장할 때 문자 세트(아스키코드 표, 유니코드 표)를 참고하여 번호로 저장한다. 예를 들어 컴퓨터에서는 문자 A가 65로 저장된다. 쉽게 말해 컴퓨터는 문자 A를 65로 이해한다.

<br>

*아스키코드와 유니코드란?*

컴퓨터에서 보통 영문 위주의 문자를 표현할 떄는 아스키코드(ASCII Code)를 사용한다. 아스키코드는 1바이트로 문자를 표현. 1바이트는 2의 8제곱 (256)이므로 아스키코드로는 256개의 문자 표현.
하지만 자바나 코틀린에서는 다양한 언어를 표현하기 위해 2바이트로 문자를 표현하는 유니코들르 사용한다. 2바이트는 2의 16제곱(65536)이므로 65536개의 문자를 표현 가능.

<br>
<br>

**문자열 자료형**

문자열 자료형은 기본형에 속하지 않는 배열 형태로 되어 있는 특수한 자료형.

![chapter02-section02-09](/images/2023-04-27-chapter02-section02/chapter02-section02-09.png)

위의 그림을 봄변 str1, str3에는 같은 문자열이 저장되어 있는데 이런 경우에는 "Hello"를 스택에 2번 저장하는 것보다 이미 저장된 값을 활용하는 것이 효율적. 그래서 코틀린은 힙 영역의 String Pool이라는 공간에 문자열인 "Hello"를 저장해 두고 이 값을 str1, str3이 참조하도록 만든다. 결과적으로 str3의 참조 주소는 str1과 동일하다. 이렇게 문자열 자료형은 String Pool을 이용해 필요한 경우 메모리 공간을 재활용한다.

<br>
<br>

**자료형에 별명 붙이기**

변수의 자료형이 복잡한 구조를 가지면 자료형에 별명을 붙일 수 있다. typealias라는 키워드 사용. 다음은 String에 Username이라고 별명을 붙인 것이다.

![chapter02-section02-10](/images/2023-04-27-chapter02-section02/chapter02-section02-10.png)

<br>
<br>
<br>
<br>
<br>
<br>
[참고 : Do it! 코틀린 프로그래밍](http://www.yes24.com/Product/Goods/74035266)