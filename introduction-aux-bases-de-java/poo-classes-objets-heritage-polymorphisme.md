---
description: >-
  Découvrez la programmation orientée objet en Java : les bases des classes et
  objets, et les concepts avancés d'héritage et de polymorphisme.
---

# POO: Classes, Objets, Héritage, Encapsulation, Polymorphisme

En Java, la POO[^1] est centrale et comprend plusieurs éléments clés tels que **les classes**, **les objets**, **l'héritage, l'encapsulation** et le **polymorphisme**. La POO utilise des objets pour modéliser les données et les interactions entre ces données.&#x20;

***

### Les Classes et Objets

#### Un objet :&#x20;

C'est une idée, un concept, un objet qu'on va mettre en relation avec d'autre objets.

#### Une classe  :&#x20;

C'est un modèle ou un plan à partir duquel les objets sont créés. Une classe définit les états (attributs, champs) et les comportements (méthodes, fonctions) que ses objets auront.

> La class qui lancera l'application java doit forcément posséder une méthode `main()`

<details>

<summary>Exemple de classe et objet</summary>

{% code title="car.java" %}
```java
public class Car {
//Propriétés
    String brand;
    int maxSpeed;

//Méthode
    void vroom() {
        System.out.println("Car is going brrr");
    }
}

// Création d'un objet de la classe Voiture
Car myCar = new Car();
myCar.brand = "Peugeot";
myCar.maxSpeed = 180;
maVoiture.vroom();  // Affiche : "Car is going brrr"
```
{% endcode %}

</details>

***

### Héritage

L'héritage permet à une classe d'hériter des caractéristiques (propriétés et méthodes) d'une autre classe.&#x20;

La classe qui hérite est appelée sous-classe ou classe dérivée, et la classe dont les caractéristiques sont héritées est appelée superclasse ou classe de base.

<details>

<summary><strong>Exemple :</strong> Une superclasse <code>Animal</code> et sa sous-classe <code>Chat</code>.</summary>

```java
public class Animal {
    String nom;

    void manger() {
        System.out.println(nom + " mange.");
    }
}

public class Chat extends Animal {
    void miauler() {
        System.out.println("Miaou !");
    }
}

// Utilisation
Chat monChat = new Chat();
monChat.nom = "Moka";
monChat.manger();  // Moka mange.
monChat.miauler(); // Miaou !
```

</details>

***

### Encapsulation

L'encapsulation est une manière de définir une classe de telle sorte que ses attributs ne puissent pas être directement manipulés de l'exterieur de la classe mais seulement indirectement par l'intermédiaire des méthodes. Cela permet de contrôler la manière dont les données sont lues ou modifiées.

<details>

<summary>Exemple encapsulation</summary>

La variable `solde` ne peut pas être lu ou modifiée directement de l'extérieur de la classe `CompteBancaire`

```java
public class CompteBancaire {
    // Déclaraton d'une propriété privée
    private double solde;

    // Déclaraton d'une methode publique pour voir le solde
    public double getSolde() {
        return solde;
    }

    public void deposer(double montant) {
        solde += montant;
    }

    public void retirer(double montant) {
        solde -= montant;
    }
}
```

</details>

***

### Polymorphisme

Le terme vient du grec "poly" (plusieurs) et "morph" (forme). En POO, cela signifie qu'un objet peut prendre plusieurs formes.

<details>

<summary>Exemple de polymorphisme</summary>

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

[^1]: Programmation orientée objet
