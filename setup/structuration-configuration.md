# Structuration du projet et configuration de la Base de Données

## Structuration du projet

Avant de commencer à écrire du code, il faut structurer l'application en différents packages en suivant le modèle MVC [Broken link](broken-reference "mention") (Modèle-Vue-Contrôleur). Voici une structure de packages typique pour une application Spring Boot :

*   **Package `com.api.crud.model`**

    Ce package contiendra les entités JPA, qui représentent les tables de la base de données.
*   **Package `com.api.crud.repository`**

    Ce package comprendra les interfaces Spring Data JPA Repository pour l'accès aux données.
*   **Package `com.api.crud.service`**

    Placer la logique métier de l'application.
*   **Package `com.api.crud.controller`**

    Ce package contiendra les contrôleurs qui gèrent les requêtes et les réponses HTTP.

## Configuration de la Base de Données

Copier le fichier `data.sql` dans `src/main/resources` pour initialiser la base de données.

{% code title="src/main/resources/data.sql" %}
```sql
DROP TABLE IF EXISTS task;

CREATE TABLE task (
  id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(250) NOT NULL,
  completed BOOLEAN NOT NULL
);

INSERT INTO task (title, completed) VALUES
  ('Tâche 1', FALSE),
  ('Tâche 2', TRUE),
  ('Tâche 3', FALSE);
```
{% endcode %}

Dans `src/main/resources/application.properties`, pour les configurations de la base de données, ajoutez ces lignes :

{% code title="application.properties" %}
```java
#Global configuration
spring.application.name=api

#Tomcat configuration
server.port=8080

#Log level configuration
logging.level.root=ERROR
logging.level.org.springframework.boot.autoconfigure.h2=INFO
logging.level.org.springframework.boot.web.embedded.tomcat=INFO
spring.jpa.hibernate.ddl-auto=update

#H2 Configuration
spring.h2.console.enabled=true
spring.datasource.url=jdbc:h2:mem:api
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=mt5
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
```
{% endcode %}

Vous aurez accès à là database plus tard en allant sur le lien [suivant](http://localhost:8080/h2-console) !

Concernant la console H2, une fois l’application démarrée, vous pouvez aller sur l’URL `http://localhost:9000/h2-console`. Une fenêtre de login s’ouvre, et il est nécessaire d’indiquer l’URL Jdbc (qui change à chaque démarrage de l’application).

Récupérez l’URL JDBC (en l'occurrence jdbc:h2:mem:b59feadd-5612-45fe-bd1c-3b62db66ea8a'), saisissez dans le formulaire, puis `Connect`. Le username par défaut est bien “sa”, et le password par défaut est vide.
