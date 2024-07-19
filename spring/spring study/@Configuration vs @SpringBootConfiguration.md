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
