# Spring MVC : Développement d’applications Web

Spring MVC est aussi un sous-module du framework Spring qui fournit une architecture modèle-vue-contrôleur ([mvc.md](../../appendicium/mvc.md "mention")) pour le développement d'applications Web. Il est conçu pour offrir une approche flexible, bien structurée et facilement testable pour construire des applications Web.

#### Architecture MVC de Spring

* **Modèle** : Le modèle représente les données et la logique métier de l'application. Dans Spring MVC, les modèles sont souvent des objets Java qui contiennent ces données.
* **Vue** : La vue est responsable de l'affichage des données, généralement sous forme de pages HTML. Spring MVC peut intégrer divers moteurs de templating comme JSP, Thymeleaf ou FreeMarker.
* **Contrôleur** : Les contrôleurs gèrent les interactions utilisateurs, travaillent avec le modèle et sélectionnent une vue pour la présentation des données.

#### Configurer Spring MVC

Pour démarrer avec Spring MVC, vous devez configurer le DispatcherServlet dans le fichier `web.xml` ou équivalent si vous utilisez une configuration basée sur Java. Ce servlet agit comme un contrôleur frontal, gérant toutes les requêtes entrantes et les dispatchant vers les contrôleurs appropriés.

#### Définir des Contrôleurs

Les contrôleurs sont au cœur de l'application Spring MVC. Ils reçoivent les requêtes des utilisateurs et y répondent. Un contrôleur est typiquement une classe Java annotée avec `@Controller`. Il contient des méthodes de traitement des requêtes, annotées avec `@RequestMapping`, qui définissent comment les différentes requêtes HTTP sont gérées.

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class MyController {

    @GetMapping("/hello")
    public String sayHello() {
        return "hello";
    }
}
```

Dans cet exemple, `MyController` gère les requêtes GET vers `/hello`.

#### Créer des Vues

Les vues dans Spring MVC sont responsables de la présentation des données au client. Spring MVC peut être intégré avec divers moteurs de templates comme JSP, Thymeleaf, ou Freemarker. Par exemple, une vue simple en Thymeleaf pourrait ressembler à ceci :

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Hello Page</title>
</head>
<body>
    <h1 th:text="${message}"></h1>
</body>
</html>
```

Cette vue affiche le message fourni par le contrôleur.Avantages de Spring MVC.

#### Avantages du Spring MVC

* **Flexibilité** : Spring MVC est hautement configurable et s'adapte à divers besoins de développement Web.
* **Intégration** : Il s'intègre facilement avec d'autres technologies Spring, telles que Spring Security et Spring Data.
* **Testabilité** : La séparation claire des responsabilités rend les composants de l'application facilement testables.
