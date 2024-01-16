---
description: >-
  Gradle et Maven, deux outils essentiels pour la construction et la gestion de
  projets Java
---

# Gradle vs Maven : Outils de Build Java

### **Qu'est-ce que Gradle ?**

Gradle est un système de build automatisé open source qui se distingue par sa flexibilité et sa capacité à gérer les dépendances et la configuration d'une manière très efficace. Il est souvent utilisé pour les projets Java, mais il peut supporter aussi [d'autres langages](#user-content-fn-1)[^1].

On retrouvera donc un fichier `build.gradle` à la racine du projet

#### **Caractéristiques clés**

* Utilise un langage basé sur **Groovy** ou [**Kotlin**](#user-content-fn-2)[^2] pour la définition de scripts de build.
* Performance optimisée grâce à l'utilisation d'un [**cache intelligent**](#user-content-fn-3)[^3].

{% code title="build.gradle" %}
```gradle
plugins {
    id 'java'
}

group 'com.myproject'
version '1.0-0'

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    testImplementation 'junit:junit:4.12'
}

```
{% endcode %}



### **Qu'est-ce que Maven ?**

Maven fais presque la même chose en un peu plus lent. Il utilise des fichiers XML ([**POM**](#user-content-fn-4)[^4]) pour décrire le projet, ses dépendances, l'ordre de build, et les plugins nécessaires.



Nous retrouverons ici un fichier `POM.xml` à la racine

**Caractéristiques clés :**

* Structure et format de projet standardisé.
* Possède un large [écosystème de plugins](https://maven.apache.org/plugins/).

{% code title="pom.xml" %}
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.myproject</groupId>
    <artifactId>my-project</artifactId>
    <version>1.0-0</version>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <version>2.3.0.1</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>

```
{% endcode %}



## Et maintenant ?

Après avoir fait le choix entre Maven et Gradle, il ne vous reste plus qu'a explorer l'écosystème Java pour ajouter des dépendances comme Junit[^5] ou le fameux framework <mark style="color:green;">**Spring**</mark>.

[^1]: Scala, C/C++, Android, Swift

[^2]: Language principalement utiliser pour faire du dev <mark style="color:green;">Android</mark>

[^3]: il est aussi possible de se donner le cache entre machine :exploding\_head:

[^4]: Project Object Model

[^5]: Framework pour effectuer des tests unitaires
