---
description: >-
  l'Inversion of Control (IoC) en Spring, un concept clé améliorant modularité
  et flexibilité.
---

# IoC: Concept et Impact

## Qu'est ce que l'IoC ?

L'Inversion of Control est souvent mal compris car son effet est principalement <mark style="color:blue;">**sous le capot**</mark>.

#### Sans IoC

Notre code contrôle directement le flux d'exécution, de la création à la gestion des objets.

#### Avec IoC

Spring va venir prendre en charge la création et la gestion des objets. Et notre code à nous va venir se concentrer sur la [**logique métier**](#user-content-fn-1)[^1], tandis que Spring s'occupe de l'assemblage des composants.



## Injection de Dépendance (DI)

L'injection de dépendance est une technique de programmation qui diminue le couplage entre les classes. Elle permet de fournir les dépendances d'un objet[^2] de l'extérieur plutôt que de les créer à l'intérieur de l'objet.

{% tabs %}
{% tab title="Sans la DI 😔" %}
{% code title="ReservationRoomDao.java" %}
```java
public class ReservationRoomDao {

    private String dbHost;
    private String dbUsername;
    private String dbPassword;

    public ReservationRoomDao() {
        this.dbHost = System.getenv("DB_HOST");
        this.dbUsername = System.getenv("DB_USERNAME");
        this.dbPassword = System.getenv("DB_PASSWORD");
    }

    public void save(ReservationRoom reservationRoom) {
        // Logique pour save la réservation dans la base de données
    }
}
```
{% endcode %}

{% code title="ReservationRoomService.java" fullWidth="true" %}
```java
public class ReservationRoomService {

    private ReservationRoomDao reservationRoomDao;

    public ReservationRoomService() {
        // Hop, on crée directement la dépendance.
        this.reservationRoomDao = new ReservationRoomDao();

    public void reserve(ReservationRoom reservationRoom) {
        // Logique supplémentaire avant de save la réservation
        reservationRoomDao.save(reservationRoom);
    }
}
```
{% endcode %}

{% code title="Main.java" %}
```java
public class Main {
    public static void main(String[] args) {
        ReservationRoomService service = new ReservationRoomService();

        service.reserve(new ReservationRoom());
    }
}

```
{% endcode %}

Ici nous rencontrons un problème majeur

Si j'ai un autre service qui doit faire appel à `ReservationRoomDao` qui va se charger de créer l'instance ?

Une problématique qu'on voudrait éviter. Un couplage fort.
{% endtab %}

{% tab title="Avec la DI 🙂" %}
{% code title="ReservationRoomDao.java" %}
```java
public class ReservationRoomDao {

    private String dbHost;
    private String dbUsername;
    private String dbPassword;

    public ReservationRoomDao() {
        this.dbHost = System.getenv("DB_HOST");
        this.dbUsername = System.getenv("DB_USERNAME");
        this.dbPassword = System.getenv("DB_PASSWORD");
    }

    public void save(ReservationRoom reservationRoom) {
        // Une petite logique pour save dans la db
    }
}

```
{% endcode %}

{% code title="ReservationRoomService" %}
```java
public class ReservationRoomService {
    private ReservationRoomDao ReservationRoomDao;

    // On définit ici un constructeur
    public ReservationRoomService(ReservationRoomDao ReservationRoomDao) {
        this.ReservationRoomDao = ReservationRoomDao; // Dépendance injectée
    }
    // Autres méthodes...
}

```
{% endcode %}

```java
public class Main {
    public static void main(String[] args) {
        ReservationRoomDao dao = new ReservationRoomDao();
        ReservationRoomService service = new ReservationRoomService(dao);

        // Using the service to make a reservation
        service.reserve(new ReservationRoom());
    }
}

```

Magie magie, c'est déjà un peu plus modulaire
{% endtab %}

{% tab title="La DI avec Spring 🤩" %}
{% code title="ReservationRoomDao.java" %}
```java
@Repository
public class ReservationRoomDao {

    private String databaseUrl;
    private String username;
    private String password;

    public ReservationRoomDao(@Value("${database.url}") String databaseUrl,
                               @Value("${database.username}") String username,
                               @Value("${database.password}") String password) {
        this.databaseUrl = databaseUrl;
        this.username = username;
        this.password = password;
    }

    // Des petites méthodes...
}

```
{% endcode %}

{% code title="ReservationRoomService.java" %}
```java
@Service
public class ReservationRoomService {
    @Autowired
    private ReservationRoomDao ReservationRoomDao;
    // Des petites méthodes..
}

```
{% endcode %}

Spring crée automatiquement des instances de `ReservationRoomDao` , `ReservationRoomService` et va injecter `ReservationRoomDao` dans `ReservationRoomService`.

Le couplage est faible, <mark style="color:green;">**on laisse toute les commandes**</mark> à Spring et bye bye le `Main.java`
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Un couplage faible est important car ça apporte une meilleurs fléxibilité, les modules peuvent êtres plus facilement testé et il est plus facile de réutiliser un module ou une classe.
{% endhint %}

## Configuration Externe

Spring offre son lot de configuration externe pour avoir un peu la main sur nos beans[^3]

On peut ainsi personnaliser complètement nos beans, spécifier quand [ils ont le droit de vivre et quand ils ont le droit de mourir](#user-content-fn-4)[^4].

### Avant Spring Boot

Avant Spring Boot, la configuration nécessitait un fichier XML bien fournit pour définir et décrire nos beans

<details>

<summary>Exemple d'injection de valeurs</summary>

{% code title="applicationContext.xml" %}
```xml
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="reservationRoomDao" class="com.example.ReservationRoomDao">
        <property name="databaseUrl" value="${db.url}"/>
        <!-- Autre configuration  -->
    </bean>

    <bean id="reservationRoomService" class="com.example.ReservationRoomService">
        <property name="reservationRoomDao" ref="reservationRoomDao"/>
    </bean>

</beans>

```
{% endcode %}



</details>

### Depuis Spring Boot

Avec l'évolution de Spring et l'introduction de Spring Boot, l'utilisation de fichiers de configuration XML tels que `applicationContext.xml` est devenue moins fréquente.&#x20;

Spring Boot favorise une approche de configuration basée sur les annotations et les fichiers de propriétés (comme `application.properties` ou `application.yml`), qui simplifie grandement le processus de configuration.

* Spring Boot  vient utiliser intensivement les annotations pour la configuration, réduisant/éliminant le besoin de fichiers XML.

{% hint style="info" %}
Des annotations comme `@SpringBootApplication`, `@Service`, `@Repository`, `@Autowired`,  `@Value, etc...`
{% endhint %}

<details>

<summary>Exemple d'injection de valeurs </summary>



<pre class="language-properties" data-title="application.properties"><code class="lang-properties"><strong>
</strong>spring.datasource.url=${DATABASE_URL}
spring.datasource.username=${DATABASE_USERNAME}
spring.datasource.password=${DATABASE_PASSWORD}

</code></pre>

</details>

### Comparatif des deux méthodes de configuration

{% tabs %}
{% tab title="Sans Spring Boot" %}
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

{% tab title="Avec Spring Boot" %}
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

[^1]: algorithmes et mécanismes de traitement des données qui sont essentiels pour accomplir des fonctions spécifiques

[^2]: &#x20;objet dont il a besoin pour fonctionner

[^3]: composants (On verra l'appélation beans plus tard)

[^4]: init-method="method" || destroy-method="method"
