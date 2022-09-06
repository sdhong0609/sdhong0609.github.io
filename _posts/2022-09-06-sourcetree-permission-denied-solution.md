---
layout: single
title:  "소스트리 Permission denied 에러 해결방법"
categories: [How To Do, ]
tag: [git, sourcetree]
---

회사의 프로젝트를 소스트리에 연결하고 페치(fetch) 및 풀(pull)을 진행하던 중 
![permission_denied_error](/images/2022-09-06-sourcetree-permission-denied-solution/permission_denied_error.png)

이런 에러를 마주하게 되었다. 이 에러가 발생하면서 원격서버에서 최신프로젝트를 로컬로 가져오지 못하게 되었다. 이 방법을 해결하는 방법에 대해 작성한다. 터미널에서 해결하면 된다.
<br/><br/>

### **1. ssh 키 로컬에 있는지 확인**
![screenshot_terminal_01](/images/2022-09-06-sourcetree-permission-denied-solution/screenshot_terminal_01.jpg)

```java
ssh-add -l
```
`ssh-add -l`를 입력하고 'The agent has no identities.'가 뜨는 것을 확인한다.
<br/><br/>

### **2. ssh 키 로컬에 등록**
![screenshot_terminal_02](/images/2022-09-06-sourcetree-permission-denied-solution/screenshot_terminal_02.jpg)

```java
ssh-add --apple-use-keychain ~/.ssh/id_rsa
```
`ssh-add --apple-use-keychain ~/.ssh/id_rsa`를 입력한다.
<br/><br/>

### **3. ssh 키 제대로 등록되었는지 확인**
![screenshot_terminal_03](/images/2022-09-06-sourcetree-permission-denied-solution/screenshot_terminal_03.jpg)

```java
ssh-add -l
```
`ssh-add -l`를 다시 입력하면 ssh 키가 제대로 등록된 것을 확인할 수 있다.
<br/>
마지막으로 `exit`을 입력하여 터미널을 종료한다.

<br/><br/>
이렇게 ssh 키를 로컬에 등록하는 과정을 진행하면 된다. 그리고 소스트리에서 다시 페치(fetch) 혹은 풀(pull)을 진행하면 정상적으로 작동한다.
