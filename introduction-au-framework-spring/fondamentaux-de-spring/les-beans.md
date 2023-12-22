---
description: >-
  Explorez la gestion des beans dans Spring, en comprenant leur création, leur
  configuration et leur utilisation pour favoriser l'inversion de contrôle (IoC)
  et la modularité dans les applications Java.
---

# Les Beans

Les beans sont des composants fondamentaux dans le framework Spring. Un Bean est un objet qui est instancié, assemblé et géré par Spring IoC[^1] Container.

***

### Definition des beans :&#x20;

Un Bean est un wrapper Java qui encapsule (regroupe) plusieurs objets en un seul. Ces objets (les Beans) sont gérés par un conteneur de Bean, comme celui fourni par le framework Spring. Un Bean est simplement une instance d'une classe.

Les beans peuvent être defini soit dans un fichier de configuration XML, soit par des annotations dans le code (c'est la manière la plus utilisée).&#x20;

Les annotations telles que `@Component`, `@Service`, `@Repository`, et `@Controller` sont utilisées pour déclarer automatiquement des beans. Spring scanne ces annotations pour enregistrer des beans.

<details>

<summary>Exemple de bean</summary>

Component

```java
@Component
public class MaClasseService {
    // Définition de la classe
}

// @Component indique au conteneur Spring de créer un Bean pour cette classe.
```

Override

```java
class Animal {
    void faireBruit() {
        System.out.println("Certains bruits");
    }
}

class Chien extends Animal {
    @Override
    void faireBruit() {
        System.out.println("Aboie");
    }
}

class Chat extends Animal {
    @Override
    void faireBruit() {
        System.out.println("Miaule");
    }
}

public class TestPolymorphisme {
    public static void main(String[] args) {
        Animal a;
        a = new Chien();
        a.faireBruit();  // Affiche "Aboie"

        a = new Chat();
        a.faireBruit();  // Affiche "Miaule"
    }
}
```

</details>

***

### Cycle de vie des beans :

Un bean est créé, soit par une déclaration dans un fichier de configuration, soit par une annotation. Spring injecte des objets dans le bean si nécessaire (par exemple, via `@Autowired`). Lorsque le conteneur Spring est fermé, les beans sont détruits.

***

### Injection de dépendances&#x20;



[^1]: Inversion of control
