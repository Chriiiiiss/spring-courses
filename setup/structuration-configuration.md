# Structuration du projet

Avant de commencer à écrire du code, il faut structurer l'application en différents packages. Voici une structure de packages typique pour une application Spring Boot :

*   #### Package `com.api.crud.model`

    Ce package contiendra les entités JPA, qui représentent les tables de la base de données.
*   #### Package `com.api.crud.repository`

    Ce package comprendra les interfaces Spring Data JPA Repository pour l'accès aux données.
*   #### Package `com.api.crud.service`

    Placer la logique métier de l'application.
*   #### Package `com.api.crud.controller`

    Ce package contiendra les contrôleurs qui gèrent les requêtes et les réponses HTTP.

# Configuration de la Base de Données

Copier le fichier `data.sql` dans `src/main/resources` pour initialiser la base de données.

Dans `src/main/resources/application.properties`, pour les configurations de la base de données, ajoutez :&#x20;

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
```