---
description: >-
  Gérer les exceptions en Java, un élément clé pour créer des applications
  robustes et fiables, en comprenant leur capture, traitement, et prévention.
---

# Maîtrise de la Gestion des Exceptions

Dans le développement, les erreurs sont inévitables. Même avec l'utilisation de tests unitaires, tous les problèmes potentiels d'une application ne peuvent pas être résolus. Pour faire face à ces défis, Java a développé un système robuste de gestion **des exceptions**, visant à augmenter la sécurité du code.

Ce système utilise des objets pour représenter les erreurs, ainsi qu'une combinaison de trois mots-clés essentiels `- try,` `catch,` et `finally` - qui aident à détecter, gérer, et traiter ces erreurs. En plus, il fournit les mécanismes pour lever (`throw`) ou propager (`throws`) ces exceptions, permettant une gestion plus fine des erreurs rencontrées.

{% hint style="warning" %}
Il ne faut pas confondre `error` et `exception`&#x20;

* Ici on parle d'`Exception`. Cela désigne la classe que les applications doivent essayer de gérer, divisée en deux catégories principales : les exceptions vérifiées (`Exception`) et les exceptions non vérifiées (`RuntimeException`).
* `Error` indique des problèmes graves qui ne devraient normalement pas être traités par une application (comme `OutOfMemoryError`)
{% endhint %}

<details>

<summary>Exemple d'exceptions</summary>

Une **division par 0** ou l'ouverture d'un **fichier inexistant** renvoie forcement une erreur

**Erreur :**&#x20;

```java
  public static void main(String[] args) {
    int i = 3;
    int j = 0;
    System.out.println("résultat = " + (i / j));
  }
```

Ce que renvoie la console :

```
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at ToDos.main(ToDos.java:9)
```

</details>

Les erreurs les plus communes que l'on peut retrouver sont :&#x20;

* <mark style="color:blue;">ArithmeticException</mark> : Quelque chose s'est passé pendant une opération d'algorithmie par exemple une division par 0&#x20;
* <mark style="color:blue;">NullPointerException :</mark>&#x20;

***

## Comment traiter les exceptions ?

On identifie et traite les exceptions de la manière suivante :&#x20;

```java
try {
      operation_risquée1;
      opération_risquée2;
    } catch (ExceptionInteressante e) {
      traitements
    } catch (ExceptionParticuliere e) {
      traitements
    } catch (Exception e) {
      traitements
    } finally {
      traitement_pour_terminer_proprement;
    }
```

<details>

<summary>Exemple de traitement d'erreur</summary>

Si on reprend l'exemple d'au dessus, on va tester si notre erreur est arithmétique grâce à `catch (ArithmeticException e)`

```java
public static void main(String[] args) {
    int i = 3;
    int j = 0;
    try {
      System.out.println("résultat = " + (i / j));
    } catch (ArithmeticException e) {
      System.out.println("Erreur arithmétique");
    }
  }
```

La console nous renvoie alors :&#x20;

```
Erreur arithmétique
```

`catch (Exception e)` permet de récupérer toutes les autres erreurs. Dans notre cas, si notre erreur n'était pas une erreur d'arithmétique, `catch (Exception e)` exécuterait ses traitement en imprimant `Autre erreur`.&#x20;

</details>

Si plusieurs type d'exception peuvent être présente dans le code, il faut alors faire plusieurs blocs catch. Mais attention, l'ordre séquentiel des block catch est important. Il faut traiter en premier les exceptions les plus précises (sous-classes) avant les exceptions plus générales. Un message d'erreur s'affiche dans la console dans cas contraire.

<details>

<summary>Exemple de l'orde séquentiel</summary>

```java
public static void main(String[] args) {
    int i = 3;
    int j = 0;
    try {
      System.out.println("résultat = " + (i / j));
    } catch (Exception e) {
      System.out.println("Autre erreur");
    } catch (ArithmeticException e) {
      System.out.println("Erreur arithmétique");
    }
  }
```

`catch (Exception e)` permet de récupérer toutes les autres erreurs. Dans notre cas, la console ne va pas afficher `"Erreur arithmétique"` car `catch (Exception e)` est un selecteur plus global

On aura ça dans la console&#x20;

```
error: exception ArithmeticException has already been caught
    } catch (ArithmeticException e) {
```

</details>

La clause finally définit un bloc qui sera toujours exécuté, qu'une exception soit levée ou non. Ce bloc est facultatif.&#x20;

### Les méthodes importantes

* `getMessage()` : Retourne le message d'erreur détaillé de l'objet `Throwable`.
* `printStackTrace()` : Imprime la trace de la pile d'exécution au moment où l'objet `Throwable` a été créé, ce qui est très utile pour le débogage.
* `getCause()` : Retourne la cause de l'exception, ou `null` si la cause est inexistante ou inconnue.
* `fillInStackTrace()` : Remplit la trace de la pile pour cet objet `Throwable`.
* `getStackTrace()` : Fournit un tableau de stack trace elements représentant la trace de la pile au moment où l'objet `Throwable` a été créé.

<details>

<summary>Mise en pratique</summary>

```java
  public static void main(String[] args) {
    int i = 3;
    int j = 0;
    try {
      System.out.println("résultat = " + i/j);
    } catch (ArithmeticException e) {
      System.out.println(e.getMessage());
      System.out.println(" ");
      System.out.println(e.toString());
      System.out.println(" ");
      e.printStackTrace();
    }
  }
```

Résultat dans la console

```
/ by zero 
 
java.lang.ArithmeticException: / by zero
 
printStackTrace
java.lang.ArithmeticException: / by zero
	at ToDos.main(ToDos.java:10)
```

</details>

### Personnalisation des Exceptions

### Propagation des Exceptions



***
