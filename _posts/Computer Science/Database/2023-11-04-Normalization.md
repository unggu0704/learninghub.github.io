---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Data Base]
tags: [CS, DataBase]
render_with_liquid: true
comments: true
---
# Normalization

> 데이터의 중복을 줄이고 무결성을 향상, 데이터의 유연성을 확보하는 과정
> 

### Normalization의 목표

- 중복된 데이터를 허용하지 않은 것
- 무결성 유지 및 저장 용량 효율적 관리
- 이상현상 방지
- DB 구조의 확장에 용이

## 1NF

- 테이블 컬럼은 원자 값을 갖도록 테이블을 분리 시킨다.
- 기본키만을 가지고 식별 할수 있어야한다.

![Untitled]({{ site.baseurl }}{{ page.url }}/Normalization%20cf5b4057525047a489e89550e67e5a0f/Untitled.png)

*제 1 정규화 처리*

![Untitled]({{ site.baseurl }}{{ page.url }}/Normalization%20cf5b4057525047a489e89550e67e5a0f/Untitled%201.png)

- Telephone Number의 atomic을 보장

## 2NF

- 테이블의 모든 컬럼은 FD를 만족해야한다.
- 기본키의 부분집합 키가 요소를 결정해서는 안된다.

![Untitled]({{ site.baseurl }}{{ page.url }}/Normalization%20cf5b4057525047a489e89550e67e5a0f/Untitled%202.png)

`Manufacturer` + `Mode` → `Model Full Name`

`Manufacturer` → `Manufacturer Country` 

따라서, `Model`과 `Manufacturer Country`는 아무런 연관관계가 없는 상황이다.

*제 2정규화 처리*

![Untitled]({{ site.baseurl }}{{ page.url }}/Normalization%20cf5b4057525047a489e89550e67e5a0f/Untitled%203.png)

## 3NF

- 이행적 종속을 제거하자

![Untitled]({{ site.baseurl }}{{ page.url }}/Normalization%20cf5b4057525047a489e89550e67e5a0f/Untitled%204.png)

- `Tournament`와 `Year`이 기본키
- `Winner Date of Birth`는 기본키가 아닌 `Winner`에 의해 결정

*제 3 정규형을 적용…*

![Untitled]({{ site.baseurl }}{{ page.url }}/Normalization%20cf5b4057525047a489e89550e67e5a0f/Untitled%205.png)

## BCNF

- 모든 결정자가 후보키여야 한다.

## 이상

- 정규화를 해야하는 이유 이상현상을 피하기 위해

### 삽입 이상

- 불필요한 데이터를 추가해야지 삽입할수 있는 현상
- null 값을 넣을순 없기에, 불필요한 course ID를 또 추가해야함

### 갱신 이상

- 어떤 데이터의 갱신이 필요해질 때 일부를 바꾸지 못한 경우
- 데이터의 일관성 문제

### 삭제 이상

- 하나의 튜플을 지우는데 다른 필요한 데이터까지 삭제되는 문제