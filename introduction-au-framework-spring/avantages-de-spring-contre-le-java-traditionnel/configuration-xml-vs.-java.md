---
description: >-
  Découvrir l'approches traditionnel utilisant du XML et voir la différence avec
  la configuration Java amené dans Spring 3.0.
---

# Configuration XML vs. Java

## Comparatif des deux méthodes de configuration

{% tabs %}
{% tab title="Sans Spring Boot (XML)" %}
{% code title="applicationContext.xml" %}
```xml
<!-- Configuration de la source de données (MySQL) -->
<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
    <property name="driverClassName" value="com.mysql.cj.jdbc.Driver" />
    <property name="url" value="jdbc:mysql://localhost:3306/mydb" />
    <property name="username" value="myuser" />
    <property name="password" value="mypassword" />
</bean>

<!-- Configuration du gestionnaire de transactions -->
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
    <property name="dataSource" ref="dataSource" />
</bean>

<!-- Configuration du gestionnaire de vues (JSP) -->
<bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
    <property name="prefix" value="/WEB-INF/views/" />
    <property name="suffix" value=".jsp" />
</bean>

```
{% endcode %}
{% endtab %}

{% tab title="Avec Spring Boot (Java)" %}
```java
@Configuration
public class AppConfig {
    @Bean
    public MonBean monBean() {
        return new MonBean();
    }
}
```

{% code title="application.properties" %}
```properties
# Configuration de la source de données
jdbc.url=jdbc:mysql://localhost:3306/mydb
jdbc.username=myuser
jdbc.password=mypassword
jdbc.driverClassName=com.mysql.cj.jdbc.Driver

# Configuration du serveur Web (Tomcat, par exemple)
server.port=8080

# Configuration de la vue (si vous utilisez JSP, par exemple)
view.prefix=/WEB-INF/views/
view.suffix=.jsp

```
{% endcode %}
{% endtab %}
{% endtabs %}
