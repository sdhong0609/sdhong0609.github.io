---
layout: single
title:  "repository마다 다른 Git 계정 사용하기"
categories: [How To Do, ]
tag: [git, github]
---

내 github pages의 첫 글을 이 글로 시작한다.

회사에 입사할 때 안타깝게도 나는 내 개인 맥북으로 회사 일을 하기를 원했다. 회사에서 노트북을 제공했지만 오래된 노트북이었기에 차라리 내 개인노트북으로 하는 것이 낫다고 여겼기 때문이다.
<br/><br/>
하지만 이렇게 하면서 문제가 발생했는데 그것은 바로 내 개인 Git 계정과 회사 이메일로 만든 Git 계정이 다르다보니 커밋할 때 혼선이 생긴다는 것이다. 회사 프로젝트에 내 개인 Git 계정으로 커밋하고 내 프로젝트에 회사 Git 계정으로 커밋하는 상황이 발생해버렸다. 그 과정에서 해결법을 찾았다.
<br/><br/>
그래서 오늘은 그 해결법을 작성하고자 한다. 모든 명령어는 맥북 기준으로 작성되었으며 그래서 터미널을 사용하였다.
<br/><br/><br/>

### **전역으로 git 계정 설정**
```java
git config --global user.name "이름"
git config --global user.email "이메일"
```
"이름"과 "이메일"에 자신의 계정정보를 넣어주면 된다. 예를 들면
```java
git config --global user.name "hong"
git config --global user.email "sdhong0609@gmail.com"
```
이런 식으로 사용하면 된다.
<br/><br/>
이렇게 하면 전역으로 git 계정이 설정되며 자신의 모든 프로젝트에서 이 git 게정으로 커밋을 진행한다.
<br/><br/><br/>

### **개별로 git 계정 설정**
```java
git config --local user.name "이름"
git config --local user.email "이메일"
```
사실 다른 점은 `--global`을 사용했느냐 `--local`을 사용했느냐 이 차이일 뿐이다. 하지만 특정 프로젝트에 설정해주는 것이기 때문에 <span style="color: red">**터미널에서 해당 repository로 이동하여 커맨드를 입력해주어야 한다.**</span>
<br/><br/><br/>

### **git 계정 확인**
```java
git config --list
```
설정한 git 계정을 확인하려면 이 커맨드를 입력하면 된다. 그러면 목록이 쭉 뜨는데 `user.name`, `user.email` 항목이 안 보이면 Enter버튼(맥의 Return 버튼)을 꾹 눌러주면 된다. 그러면 항목들이 계속 아래로 스크롤되면서 나타날 것이다.
<br/><br/>

![screenshot_terminal](/images/2022-08-03-git-account/screenshot_terminal.png)

캡쳐한 스크린샷은 특정 repository에서 `git config --list` 커맨드를 입력한 결과이다. 중간 부분의 `user.name`과 `user.email`은 회사용 계정이고, 맨 마지막의 `user.name`과 `user.email`은 개인 계정이다. <span style="color: red"><br/>
가장 아래쪽의 계정으로 적용되는 것이므로</span> 해당 프로젝트는 내 개인 계정으로 커밋을 진행하는 것을 확인할 수 있다.<br/><br/>
마지막으로 이전의 터미널 상태로 돌아가려면 (END)표시가 떴을 떄 wq를 눌러주면 되돌아갈 수 있다.
