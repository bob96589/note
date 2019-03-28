# Spring Boot

> `@SpringBootApplication` annotation can be used to enable those three features, that is:
>
> * `@EnableAutoConfiguration`: enable [Spring Boot’s auto-configuration mechanism](https://docs.spring.io/spring-boot/docs/current/reference/html/using-boot-auto-configuration.html)
> * `@ComponentScan`: enable `@Component` scan on the package where the application is located \(see [the best practices](https://docs.spring.io/spring-boot/docs/current/reference/html/using-boot-structuring-your-code.html)\)
> * `@Configuration`: allow to register extra beans in the context or import additional configuration classes

> auditing can be enabled by annotating a configuration class with the @EnableJpaAuditing annotation.



