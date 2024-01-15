# Avantages de Spring contre le Java Traditionnel

## Intro

Spring est un framework open source pour le développement d'applications en Java. Il est conçu pour simplifier le développement Java en offrant un modèle de programmation complet et une configuration extensible. Comparé au Java traditionnel, Spring apporte plusieurs avantages significatifs.

## **Facilité de Développement**

* **Inversion de Contrôle (IoC)** : Spring utilise l'IoC pour gérer les dépendances. Cela réduit le couplage entre les composants et facilite la gestion des dépendances, rendant le code plus scalable et facile à tester.
* **AOP (Aspect-Oriented Programming)** : [Spring supporte l'AOP qui permet de séparer les préoccupations transversales](#user-content-fn-1)[^1] (comme un Logger, [de la sécurité](#user-content-fn-2)[^2]) du code principal, améliorant ainsi la modularité.
  * Spring fournit une gestion déclarative des transactions lié aux opérations pour la base de données
  * Plutôt que d'ajouter manuellement des instructions de log dans chaque méthode, un aspect de Logger peut être créé pour s'appliquer automatiquement à plusieurs méthodes.
  * etc..

#### Simplification de la communication avec les bases de données

Spring offre une couche d'abstraction pour l'accès aux données, simplifiant l'interaction avec différentes sources de données telles que JDBC, Hibernate, Spring Data JPA, ou JDO.



[^1]: cross-cutting concerns

[^2]: Vérifier si un utilisateur à le droit de faire ce qu'il fait
