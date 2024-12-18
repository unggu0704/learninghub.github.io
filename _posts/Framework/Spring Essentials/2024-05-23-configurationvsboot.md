---
title: "@Configuration와 @SpringBootConfiguration 차이"
author: 김규형
date: 2024-05-23 11:44:10 +0800
categories: [Framework, Spring Essentials]
tags: [BackEnd, SpringBoot, Spring]
render_with_liquid: true
comments: true
image: 
  path: https://velog.velcdn.com/images/zosungwoo/post/fee02cff-da23-4681-a387-8e810b67480c/image.jpg
---

# @Configuration vs @SpringBootConfiguration

> 싸피에서는 `@SpringBootConfiguration` 를 사용하지만 인프런 강의에서는 `@Configuration` 를 사용한다.
> 

### 계층 구조

```jsx
@SpringBootApplication
-------> @SpringBootConfiguration
       -------> @Configuration
```

### SpringBootApplication의 메타 어노테이션

```jsx
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan(excludeFilters = { @Filter(type = FilterType.CUSTOM, classes = TypeExcludeFilter.class),
        @Filter(type = FilterType.CUSTOM, classes = AutoConfigurationExcludeFilter.class) })
public @interface SpringBootApplication {
```

- 즉 **SpringBootApplication**를 사용한다면 여러 효과를 받을 수 있다.
