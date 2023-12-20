---
description: >-
  Découvrir l'approches traditionnel utilisant du XML et voir la différence avec
  la configuration Java amené dans Spring 3.0.
---

# Configuration XML vs. Java

## XML

```xml
<beans>
    <bean id="monBean" class="com.exemple.MonBean">
        <!-- Configuration supplémentaire -->
    </bean>
</beans>
```

## Java

```java
@Configuration
public class AppConfig {
    @Bean
    public MonBean monBean() {
        return new MonBean();
    }
}
```
