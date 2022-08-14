---
layout: single
title:  "안드로이드 액티비티 생명주기 (Android Activity Lifecycle)"
categories: [Android, ]
tag: [android, activity, lifecycle]
---

안드로이드의 가장 기본적인 개념 중에 생명주기라는 것이 있다. 생명주기 혹은 수명주기라고 하는데 이는 lifecycle이라는 단어를 우리말로 해석하다보니 단어가 혼용되는 것이다. 생명주기라는 말을 그대로 탄생하고 성장하여 죽음에 이르기까지의 과정을 말한다.
<br/><br/>
하지만 이를 안드로이드의 액티비티에 적용하면 액티비티가 생성되어 화면에 나타나고 실행되다가 화면이 가려지고 아예 없어져서 액티비티가 종료되는 일련의 과정을 액티비티 생명주기라고 말할 수 있다.
<br/><br/><br/>

![activity_lifecycle.png](/images/2022-08-14-android-activity-lifecycle/activity_lifecycle.png)
<br/>

이미지 출처 : [안드로이드 공식 가이드](https://developer.android.com/guide/components/activities/activity-lifecycle)
<br/><br/>

### <span style="color: skyblue">**1. onCreate()**</span>
Activity가 처음 만들어질 때 호출되는 함수이면서, 최초로 한번 실행되는 함수이다. 주로 View를 만들거나 화면 Layout 정의, Databinding 등을 이곳에서 한다. Activity 최초 실행 시, 한번만 해야할 작업을 이 함수 내에서 하면 된다.
<br/>

### <span style="color: skyblue">**2. onStart()**</span>
Activity가 사용자에게 보여지기 직전에 호출되는 함수이다. 화면에 진입할 때 실행되어야 하는 작업을 이곳에서 하면 된다.
<br/>

### <span style="color: skyblue">**3. onResume()**</span>
Activity가 비로소화면에 보여지는 단계이며 사용자에게 Focus를 잡은 상태이다. onResume()까지 호출되면 Activity는 Running 상태가 된다. onResume()은 굉장히 자주 호출되는 함수이기 때문에 내 경험상 이 함수에서 해야 할 것이 많다.
<br/><br/>
예를 들어 A화면에서 B화면으로 갔닥 back 버튼을 눌러서 A화면으로 돌아오면 A화면의 onResume() 함수가 호출된다. 그래서 A화면의 데이터를 업데이트를 하는 함수를 onResume() 내에서 호출하기도 한다.
<br/>

### <span style="color: skyblue">**4. onPause()**</span>
Activity 위에 다른 Activity가 올라와서 Focus를 잃었을 때 호출되는 함수이다. 다른 Activity가 호출되기 전에 잠깐 실행되는 함수이기 때문에 시간이 많이 소요되는 작업이나 다량의 작업을 처리하는 것은 권장되지 않는다.
<br/>

### <span style="color: skyblue">**5. onStop()**</span>
Activity 위에 다른 Activity가 완전히 올라와 화면에서 100% 가려질 때 기존 Activity는 Stopped 상태에 들어가고, onStop()을 호출한다. 홈버튼을 눌렀을 때도 onPause()와 같이 호출된다.
<br/>

### <span style="color: skyblue">**5-1. onRestart()**</span>
Activity가 Stopped 상태에서 Activity가 다시 불려지면 onRestart() 함수가 호출된다. onRestart()가 호출된 후에 onStart()가 호출된다.
<br/>

### <span style="color: skyblue">**6. onDestory()**</span>
Activity가 완전히 종료될 때, 즉 제거되는 경우 호출되는 함수이다. onStop(), onDestroy() 함수는 메모리 부족이 발생하면 스킵될 수 있다.
<br/><br/>

사실 Activity의 Lifecyle의 개념을 알고는 있지만, 막상 앱 개발을 하다보면 다양한 상황을 맞닥뜨리다 보니 헷갈리 때가 꽤 있다. 그럴 때는 항상 각각의 함수에 breakpoint를 찍어서 디버깅을 해보거나 로그를 찍어보면 확실히 알 수 있다. 확실하지 않은 상황일 때는 디버깅만큼 좋은 도구가 없다.
