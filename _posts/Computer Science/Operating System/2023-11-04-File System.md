---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Operating System]
tags: [CS, OS]
render_with_liquid: true
comments: true
---
# File System

> 파일이나 자료를 유지 및 관리하는 방법
> 

**특징**

- 커널 영역에서 동작한다.
- 파일의 CRUD를 원활하게 하는 것이 목적
- 계층적 디렉터리를 가진다.

**역할**

- 파일 관리
- 보조 저장소 관리
- 파일 무결성 메커니즘
- 접근 방법의 제공
- 하드디스크의 효율적 사용

**구조**

- 메타 영역
    - 파일의 이름, 위치, 크기 등 파일 정보
- 데이터 영역
    - 파일의 데이터

## 파일 접근 방법

### 순차 접근

- 현재 찾는 파일의 위치가 앞으로 보내면서 탐색 없으면 뒤로 탐색 시작

![Untitled]({{ site.baseurl }}{{ page.url }}File%20System%20691ba8c64a7f41a598da40dfb47b38c0/Untitled.png)

- 테이프와 유사한 방법으로 동작한다. (포인터)

### 직접 접근

![Untitled]({{ site.baseurl }}{{ page.url }}File%20System%20691ba8c64a7f41a598da40dfb47b38c0/Untitled%201.png)

- 현재 위치를 가르키는 cp변수를 활용해 움직인다

### 색인 접근

![Untitled]({{ site.baseurl }}{{ page.url }}File%20System%20691ba8c64a7f41a598da40dfb47b38c0/Untitled%202.png)

- 레코드를 찾기 전 그에 대응되는 색인을 먼저 찾아 포인터를 얻는다.
- 크기가 큰 파일에 유리
- 하지만 색인 파일도 메모리이다.

## 디스크 구조

### 1단계 디렉터리

![Untitled]({{ site.baseurl }}{{ page.url }}File%20System%20691ba8c64a7f41a598da40dfb47b38c0/Untitled%203.png)

- 파일들은 서로 유일한 이름을 가진다.
- 서로 같은 이름 어디서든지 사용 불가

### 2단계 디렉터리

![Untitled]({{ site.baseurl }}{{ page.url }}File%20System%20691ba8c64a7f41a598da40dfb47b38c0/Untitled%204.png)

- 사용자에게 개별적인 디렉터리 만들어줌
    - UFD : 자신만의 사용자 파일 디렉터리
    - MFD : 사용자의 이름과 계정번호로 색인되어 있는 디렉터리

### 트리 구조 디렉터리

![Untitled]({{ site.baseurl }}{{ page.url }}File%20System%20691ba8c64a7f41a598da40dfb47b38c0/Untitled%205.png)

- 위의 트리 구조 디렉터리 에서 한 비트를 활용해서 추가 트리를 사용한다.
    - 0 이면 일반 파일
    - 1 이면 디렉터리 파일
- 절대 경로명과 상대 경로명이 존재한다.

### 그래프 구조 디렉터리 (비순환)

![Untitled]({{ site.baseurl }}{{ page.url }}File%20System%20691ba8c64a7f41a598da40dfb47b38c0/Untitled%206.png)

- 순환은 피해야한다. → 하위 디렉토리가 아닌 파일에만 링크를 허용
- 두가지 문제에 주의
    - **가명 문제** : 파일이  여러개의 경로명을 가질 수 있기에 중복 검색 위험
    - **할당 해제 문제** : 포인터를 해제 할 때 한번에 잘 해제 해야한다. 추후 삭제되지 않고 엉뚱한 디렉토리가 가르킬 수도..