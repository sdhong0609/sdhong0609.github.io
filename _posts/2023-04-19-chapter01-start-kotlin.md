---
layout: single
title:  "Chapter 01 코틀린 시작하기 배운 것 정리"
categories: [Kotlin Basic, ]
tag: [kotlin]
---

**코틀린의 탄생 배경**

코틀린은 다음과 같은 프로그래밍이 가능한 멀티플랫폼 언어
* Kotlin/JVM: 자바 가상 머신에서 동작하는 애플리케이션 제작 가능
* Kotlin/JS: 자바 스크립트로 웹 브라우저에서 동작하는 애플리케이션 제작 가능
* Kotlin/Native: LLVM 컴파일러를 이용하여 여러 플랫폼을 타깃으로 하는 애플리케이션 제작 가능
<br>
<br>

**코틀린의 장점**
1. 자료형 오류를 미리 잡을 수 있는 정적 언어 : 코틀린은 프로그램이 컴파일될 때 자료형을 검사하여 확정하는 정적 언어. 즉 자료형 오류를 초기에 발견할 수 있어 프로그램의 안전성이 좋아짐
2. 널 포인터 예외로 인한 프로그램 중단 예방 가능 : 널 포인터 예외(NullPointerException, NPE)는 프로그램이 실행되는 도중에 발생하기 때문에 쉽게 예상하지 못함. 하지만 코틀린은 NPE를 예방 가능. 코틀린처럼 NPE를 예방하는 특성을 'NPE에서 자유롭다'라고 말한다.
3. 아주 간결하고 효율적 : 코틀린은 여러 가지 생략된 표현이 가능하여 다른 언어보다 훨씬 간결하고 효율적으로 코딩할 수 있음.
4. 함수형 프로그래밍과 객체지향 프로그래밍 모두 가능: 함수를 변수에 저장하거나 함수를 다른 함수의 매개변수로 넘길 수 있는 함수형 프로그래밍과 클래스를 사용하는 객체 지향 프로그래밍 둘다 가능. (보통 이런 특징을 '다중 패러다임 언어'라고 부른다)
5. 세미콜론을 생략할 수 있음 : 코드를 작성할 때 세미콜론(;) 생략 가능
<br>
<br>

**안드로이드 공식 언어로 채택된 코틀린**

자바 언어로 프로그램을 작성하기 위해서 SDK인 자바 JDK가 필요하며, 자바 바이트코드를 실행하기 위해서는 JVM이 필요하다. 오라클이 이에 대한 라이선스 비용을 지불하는 정책을 시행하고 있기 때문에, 구글은 분쟁을 피하기 위해 자체적인 가상 머신(DalvikVM 및 ART)을 만들거나 새로운 SDK를 제작하는 등의 조치를 취해 왔다. 그리고 자바 언어를 대체하려고 코틀린을 안드로이드 공식 언어로 채택했다.
<br>
<br>
<br>

**코틀린의 main() 함수는 프로그램의 실행 진입점**
```kotlin
fun main() {
    println("Hello Kotlin!")
}
```
자바 같은 객체 지향 언어에서 프로그램을 실행하려면 최소 하나의 클래스와 그 안에 main() 함수가 있어야 한다. 하지만 코틀린은 선언한 클래스가 없는데도 불구하고 main() 함수와 println() 함수를 통해 콘솔에 문자열을 출력하고 있다. 어떻게 이런 일이 가능할까? <br>
작성한 코틀린 코드는 JVM(Java Virtual Machine)에서 실행되며, main() 함수가 있는 파일 이름을 기준으로 자바 클래스가 자동 생성된다.
```java
/* Decompile 코드 */

public final class HelloKotlinKt {
   public static final void main() {
      String var0 = "Hello Kotlin!";
      System.out.println(var0);
   }

   // $FF: synthetic method
   public static void main(String[] var0) {
      main();
   }
}
```
main() 메서드를 다시 한번 살펴보자. static은 이 메서드가 정적 메서드임을 나타내고 있다. static으로 선언하면 프로그램의 정적 메모리 영역에 객체가 만들어지기 때문에 객체의 생성 없이 호출해 사용할 수 있다. final은 최종 메서드임을 나타낸다.<br>
[프로그램의 메모리 영역 정리](https://sdhong0609.github.io/kotlin%20basic/program-memory-area/)
<br>
<br>
<br>
<br>
<br>
<br>
[출처 : Do it! 코틀린 프로그래밍](http://www.yes24.com/Product/Goods/74035266)