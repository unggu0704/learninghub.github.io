---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Data Base]
tags: [CS, DataBase]
render_with_liquid: true
comments: true
---
# DataBase keyword

## 데이터 베이스 관리 시스팀(DBMS)

- 데이터 정의 기능
- 데이터 조작 기능
- 데이터 제어 기능
- DBMS의 구조
    
    ![Untitled]({{ site.baseurl }}{{ page.url }}/DataBase%20keyword%206823c8faec17417f9615ffd3f0963fb6/Untitled.png)
    
    - 질의 처리기 / 저장 시스템으로 나뉨

### 데이터 모델

- 개념적 데이터 모델
    - 현실 세계를 추상화
- 논리적 데이터 모델
    - 실제 데이터가 어떻게 데이터베이스에 저장되는가?
- 물리적 데이터 모델

### 데이터 독립성

- 외부 스키마
    - 실세계의 존재를 어떻게 데이터 베이스로 옮길 것인가?
- 논리 스키마
    - 개념 스키마라고도 불린다
    - 조직 전체의 입장에서 DB 정의
    - 한개 밖에 없다.
- 물리 스키마
    - 내부 스키마라고도 불린다
    - 물리적으로 어떻게 DB에 저장되는지를 기술

## Key

### 후보키

- Tuple을 유일하게 식별하기 위해 사용되는 속성들의 부분 집합
- *유일성* 과 *최소성* 을 만족해야한다.

### 기본키

- 후보키 중에 선택한 Key
- Null 값을 가질 수 없음

### 대체키

- 후보 키중에 기본키를 제외한 나머지 키

### 슈퍼키

- 유일성은 만족하지만 최소성은 만족하지 못하는 키

### 외래키

- 다른 릴레이션의 기본 키를 참조

## 관계 구조

![Untitled]({{ site.baseurl }}{{ page.url }}/DataBase%20keyword%206823c8faec17417f9615ffd3f0963fb6/Untitled%201.png)

**속성** : 개체와 개체의 특성을 나타내는 것 (데이터베이스의 가장 작은 논리적 단위) = Column

**튜플** : 릴레이션을 구성하는 각가의 행 (속성의 모임), 파일 구조의 레코드와 비슷함

**도메인** : 속성이 취할 수 있는 원자 값들의 집합

속성의 수를 → **Degree**, **차수**

튜플의 수를 → **카디널리티**

## SQL

### 데이터 조작어(DML) - SIUD

- `SELECT`
- `INSERT`
- `UPDATE`
- `DELETE`

### 데이터 정의어(DDL) - CADRT

- `CREATE`
- `ALTER`
- `DROP`
- `RENAME`
- `TRUNCATE`

### 데이터 제어어(DCL) - GR

- `GRANT`
- `REVOKE`

### 트랜젝션 제어어(TCL) - CRS

- `COMMIT`
- `ROLLBACK`
- `SAVEPOINT`

## NoSQL

> 스키마도 없고 관계도 없다.
> 
- 일반적인 레코드를 문서라고 부른다.
- 이러한 문서를 JSON 형태처럼 보유 → JOIN 할 필요가 없이 이미 필요한 모든걸 보유
- JOIN 효율이 매우 떨어짐
    - 자주 변경되지 않음 + JOIN 할일이 별로 없을때  효과적인 NoSQL