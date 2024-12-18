---
author: 김규형
date: 2024-12-15 14:10:00 +0800
categories: [NHN Academy, CS]
tags: [CS, NHN Acedemy, Java]
render_with_liquid: true
---

# JAVA 개념 정리 (09.04 ~ 09.08)

## Java의 특징

### 객체 지향 언어 (OOP)

- 객체란 무엇인가
    1. 현실 세계의 Entity를 객체로 지정해 이 객체로 프로그래밍을 하는 기법
    2. 객체는 필드와 메소드를 통해 노출 됨 
    3. 이러한 방식을 통해 내부 상태는 숨기고 객체간의 상호작용 → 데이터 캡슐화
    4. 모듈성, 정보 은닉, 코드 재사용, 디버깅 용이성 등의 기능을 제공함 
- 클래스란?
    1. 객체를 생성하기 위한 Blueprint
    2. 클래스를 기반으로 얼마든지 객체를 찍어낼 수 있음 
- 상속이란?
    1. 자식 객체는 부모 객체의 함수를 사용가능하다
    2.  클래스는 하나의 슈퍼 클래스를 가지며 무한의 서브 클래스 생성 가능 

- 객체 지향의 설계 원칙
    1. 단일 책임 원칙 : 한 클래스는 하나의 책임
    2. 개방 폐쇄 원칙 : 확장에는 Open, 수정에는 Close
    3. 리스코프 치환 원칙 : 하위 타입은 항상 상위 타입을 대체 가능
    4. 인터페이스 분리 원칙 : 인터페이스의 메소드는 최소한일 수록 좋다.
    5. 의존관계 역전 원칙 : 변하치 않은 불변 클래스와 관계를 맺을것.
- 패키지 → 기능별로 클래스와 인터페이스를 구성하는 것들을 묶은것
- API → Application Programming Interface
- 자바는 완전한 객체 지향은 아니다… 대신에 아름다운 객체지향
- JDK → 자바 개발 도구 (컴파일 기능 있음)
- JRE → 자바 실행 머신 (컴파일 기능이 없음)

### JVM

- Java Byte Code를 OS에 맞게 변환 → OS에 독립적
- 컴파일 하면 바이트코드 생성
- 스택 기반 동작
- 가비지 컬렉션을 통한 메모리 관리
    1. 동적으로 할당됐던 메모리 영역 중 필요 없는 메모리 영역을 회수해서 관리

### 메모리 영역

- 메소드 영역 : 전역 변수와 Static을 저장
- 스택 영역 : 지역 변수와 매개변수를 저장, 메소드 호출시 할당 및 종료시 반환, LIFO의 구조를 가짐
- 힙 영역 : new 키워드로 관리 객체, 배열이 저장됨 가비지 컬렉션으로 관리

### Synchronized

- 여러개의 Thread가 한개의 자원을 이용할때 나타나는 교착 상태(Deadlock)을 방지
- 하나의 Thread가 접근지 다른 Thread의 접근을 막음
- 남발하면 성능 저하

### String

- java.lang.String
- String 생성시 new String()과 리터럴 방식으로 구분
- new String은 Heap 영역에 저장
- 리터럴 방식은 String Constatnt Pool 영역에 저장
- 리터럴은 객체를 생성하지 않고 그대로 저장하는 방법 → 가독성, 최적화 우수

### final

- 클래스, 메소드, 변수 등을 한 번만 할당
- 한번 초기화 되면 변경할수 없으며 오버라이딩과 상속을 금지함

## Java 자료형 / Collections

### 정수형

- byte - 1 , short -2 , int - 4, long - 8

### 실수형

- float - 4, double - 8

### 문자형

- char - 2

### 논리형

- boolean - 1

### 배열

- Scan에 빠름 바이트 수에 맞게 입력

### List

- ArrayList → 배열 형식으로 데이터를 저장 스캔에 유리
- LinkedList → 자료 삽입에 유리 순차 접근만 가능하기에 스캔에 불리

### TreeSet

- 검색에 메우 최적화
- 일반적인 트리 구조

### HashSet

- Tree 구조보다 검색에 빠름

## JAVA 개념

### 자바 접근 제어자

- Public, Protected, default, private
- 객체들간의 관계에 있어 권한을 부여 가능
- 데이터의 부적절한 사용으로부터 보호 가능

## 다형성

- 같은 자료형에 여러가지 타입의 데이터를 대입하여 다양한 결과를 얻어낼 수 있는 성질

### 업 캐스팅

- 자식 클래스가 부모 클래스 타입으로 캐스팅
- 해당 클래스는 부모 클래스의 멤버만 접근 가능
- 하나의 인스턴스로 묶어서 관리 가능 → 다운 캐스팅이 필수적

### 다운 캐스팅

- 부모 클래스가 자식 타입으로 캐스팅 되는것
- 주로 업케스팅한 객체를 되돌리는데 쓰임

### 추상 클래스

- 추상 메소드가 하나 이상 포함된 클래스
- abstract로 정의된 경우
- 하위 메소드의 기능 확장을 추구
- 다중상속이 불가능
- 하위 클래스에서 추상 메서드의 구현을 강제함
- Overrriding

### 인터페이스

- 모든 메소드가 추상 메소드로만 이루어져 있음
- 하위 메소드가 구현시 특정 메소드가 반드시 있어야함
- 다중 상속이 가능
- Overrriding
- 서브타이핑이라고도 불림
- 리스코프 치환 원칙(LSP)를 만족함 
→ 자식이 부모의 행동 호환성을 유지, 부모 클래스를 대체 가능함.
- 추상클래스와 차이 
→ 다중 상속이 가능하기에 기능에 따른 인터페이스를 상속해 기능 확장
→ 인터페이스 분리 원칙(ISP)라고 함

### 상속

- extends
    1. 부모의 변수, 메소드 사용가능
    2. 다중 상속 X
- implements
    1. 부모 메소드를 반드시 재정의 해야함 
    2. 다중 상속이 가능 

### Overrriding

- 하위 클래스에서 상위 클래스의 메소드를 재 정의해서 사용
- 코드 중복을 줄이고 기능 확장에 이점

### Overloading

- 같은 이름을 가지지만 매개변수가 다른 여러 개의 메소드를 선언
- 메소드 이름의 중복으로 가독성 증가

## 싱글톤 패턴, Static

### 싱글톤 패턴

- 인스턴스의 불필요한 생성을 방지하고 오직 한개만 생성
- 메모리 낭비 방지
- 데이터 공유의 용이

### Static

- 인스터스가 아닌 클래스에 고정
- 객체 인스턴스 생성하지 않고 사용 가능
- JVM에 Static 영역에 바로 배치
- Static 변수 선언시 클래스 변수라고도 함

### 차이

- Static은 다형성을 사용할수 없음
- Static은 프로그램 실행시 초기화, 싱글톤은 getInstance 호출 시에 생성
