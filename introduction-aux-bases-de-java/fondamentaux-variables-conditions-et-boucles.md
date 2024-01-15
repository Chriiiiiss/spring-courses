---
description: >-
  Explorez les éléments clés de Java : Déclarer des variables, utiliser des
  boucles, appliquer des conditions et itérer sur des tableaux.
---

# Fondamentaux : Bases, Variables, Conditions et Boucles

## Comment je code ?

### **Qu'est-ce que le JDK ?**

Le <mark style="color:green;">**J**</mark>ava <mark style="color:green;">**D**</mark>evelopment <mark style="color:green;">**K**</mark>it, est l'ensemble des outils nécessaires pour développer des applications en Java. Il inclut le JRE[^1], qui est nécessaire pour exécuter des applications Java, ainsi que des outils comme le compilateur `javac` et d'autres utilitaires essentiels au développement.

{% hint style="info" %}
Pour installer le JDK rendez-vous sur le [site d'Oracle ](https://www.oracle.com/java/technologies/downloads/)
{% endhint %}

### Quel IDE ?

Aujourd'hui Il y a 2 gros **IDE** qui sortent du lot pour faire du java:

<details>

<summary><a data-footnote-ref href="#user-content-fn-2"><strong>Intellij IDEA</strong></a></summary>

Un IDE assez gourmand et lourd, mais qui possède un excellent ecosystem, beaucoup de plugin, [demande beaucoup de configuration](#user-content-fn-3)[^3] mais une fois pris en mains, c'est excellent et très pratique !

Il faudra télécharger la [<mark style="color:purple;">**\[Suite Jetbrain**</mark>](https://www.jetbrains.com/fr-fr/idea/download/?section=mac)<mark style="color:purple;">**]**</mark> puis configurer le JDK une fois dans l'application

</details>

<details>

<summary><a data-footnote-ref href="#user-content-fn-4">Eclipse</a></summary>

Eclipse offre un grand choix de personnalisation, est gratuit et comparé à Intellij IDEA il est bien moins gourmand

Il faudra télécharger <mark style="color:orange;">**\[**</mark>[<mark style="color:orange;">**Eclipse**</mark>](https://www.eclipse.org/downloads/)<mark style="color:orange;">**]**</mark> puis configuré le JDK

</details>

{% hint style="warning" %}
<mark style="color:yellow;">**Attention:**</mark> La configuration du JDK peut nécessiter de définir la variable d'environnement JAVA\_HOME et de configurer le chemin du JDK dans les paramètres de votre IDE.
{% endhint %}

## **La Structure de Base d'un Fichier Java**

En Java, chaque fichier source (`.java`) contient au moins une classe. Chaque classe est définie par le mot-clé `class`, suivi du nom de la classe. La convention veut que les noms de classe sois en PascalCase.

<details>

<summary>Exemple d'un fichier Java</summary>

{% code title="LittleClass.java" %}
```java
public class LittleClass {
    // Entrez le reste de votre code ici
}
```
{% endcode %}

</details>

#### Méthode main

La méthode main est le point d'entrée de tout programme en Java. C'est par cette méthode que l'exécution du programme commence.&#x20;

* <mark style="color:yellow;">**public**</mark> <mark style="color:yellow;">**:**</mark> Cela signifie que la méthode est accessible de partout. Dans le cas de la méthode `main` Java nécessite que la méthode soit `public` pour qu'elle puisse être appelée par le moteur d'exécution Java qui se trouve en dehors de la classe.
* <mark style="color:yellow;">**static**</mark> <mark style="color:yellow;">**:**</mark> Une méthode statique appartient à la classe plutôt qu'à un objet spécifique de la classe. Cela veut dire qu'il n'y aura pas de [**dynamic binding**](../appendicium/dynamic-binding.md) et qu'elle ne pourra avoir accès qu'aux variables situées à l'intérieur de la classe.
* <mark style="color:yellow;">**void :**</mark> Cela veut signifier que la fonction ne retourne rien.
* <mark style="color:yellow;">**String\[] args :**</mark> C'est le premier paramètre de la méthode main, il permet de récupérer ce qui a été donnée en argument lors de l'appel de la fonction sur le terminal sous la forme d'un tableau de String.&#x20;

<details>

<summary>Exemple</summary>

{% code title="LittleClass.java" %}
```java
public class LittleClass {
    public static void main(String[] args) {
        // Le code exécuté au démarrage du programme
        System.out.println("Hello World");
    }
}
```
{% endcode %}

</details>

#### Mais alors, comment je fais pour lancer ma classe maintenant ?

Une fois ma classe définit et ma super méthode `main` présente, je fais quoi ?

Avant de pouvoir le lancer il faut lancer le compilateur `javac` sur notre fichier.

Le compilateur va checker qu'il n'y a aucune erreur qui risquerait de faire planter instantanément le programme, et va par la suite générer un exécutable en .class.

**La marche à suivre est donc la suivante :**&#x20;

{% code title="bash" %}
```bash
javac LittleClass.java
java LittleClass
```
{% endcode %}

À noter qu'on a pas besoin de rajouter le `.class` lorsque nous souhaitons lancer l'executable.

***

## **Le Typage :**

Java utilise un typage statique[^5].&#x20;

On y retrouve donc des types primitifs `int` , `double`, `char` , `boolean` et des objets[^6] `String`, `Integer` etc.

<details>

<summary>Exemples de déclaration de variable : </summary>

{% code title="LittleClass.java" %}
```java
int maVariable = 5
double maSuperVariable = 8.3
String maVariableCool = "Hello"
```
{% endcode %}

</details>

***

## **Les conditions :**

Les conditions sont plutôt simples, on retrouve `if`, `else if`, `else`, switch qui utilise des booléens.  On peut y utiliser des opérateurs comparateurs comme  `<`,`>`,`=`,`!=` et des opérateurs logiques comme `&&` ou `||`.

<details>

<summary>Exemple de condition</summary>

{% code title="LittleClass.java" %}
```java
if ((condition && autre condition) !== (troisième condition)){
   //Reste du code
} else {
   //Reste du code
}
```
{% endcode %}

</details>

***

## **Les boucles :**&#x20;

Comme les conditions on peut y retrouver les opérateurs cités précédemment. Java offre plusieurs types de boucles pour itérer à travers des données comme `for` , `while`,  `do...while` et `for each`

<details>

<summary>Exemple des différentes boucles</summary>

#### **For**

<pre class="language-java"><code class="lang-java"><strong>for (int i = 0; i &#x3C; 5; i++) {
</strong>    // Reste du code
}
</code></pre>

***

#### **While :**

```java
int i = 0;
while (i < 5) {
    // Reste du code
    i++;
}
```

***

#### **Do While :**

```java
int i = 0;
do {
    // Reste du code
    i++;
} while (i < 5);
```

***

#### **For Each :**

```java
String[] fruits = {"pomme", "banane", "mangue"};
for (String fruit : fruits) {
    // Reste du code
}
```

</details>

[^1]: Java Runtime Environment

[^2]: Pour les riches ou les étudiants. (ce qui est assez paradoxal)

[^3]: Les VIM users vont adorés !

[^4]: Pour ceux qui n'aime pas Jetbrains

[^5]: Le type de chaque variable doit être déclaré explicitement. (merci)

[^6]: Primitive Wrapper
