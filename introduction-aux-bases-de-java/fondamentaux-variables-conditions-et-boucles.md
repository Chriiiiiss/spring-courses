---
description: >-
  Explorez les éléments clés de Java : Déclarer des variables, utiliser des
  boucles, appliquer des conditions et itérer sur des tableaux.
---

# Fondamentaux : Variables, Conditions et Boucles

### **Le Typage :**

Java utilise un typage statique[^1].&#x20;

On y retrouve donc des types primitifs `int` , `double`, `char` , `boolean` et des objets[^2] `String`, `Integer` etc.

<details>

<summary>Exemples de déclaration de variable : </summary>

```java
int maVariable = 5
double maSuperVariable = 8.3
String maVariableCool = "Hello"
```

</details>

***

### **Les conditions :**

Les conditions sont plutôt simples, on retrouve `if`, `else if`, `else`, switch qui utilise des booléens.  On peut y utiliser des opérateurs comparateurs comme  `<`,`>`,`=`,`!=` et des opérateurs logiques comme `&&` ou `||`.

<details>

<summary>Exemple de condition</summary>

```java
if ((condition && autre condition) != (troisième condition)){
   //Reste du code
} else {
   //Reste du code
}
```

</details>

***

### **Les boucles :**&#x20;

Comme les conditions on peut y retrouver les opérateurs cités précédemment. Java offre plusieurs types de boucles pour itérer à travers des données comme `for` , `while`,  `do...while` et `for each`

<details>

<summary>Exemple des différentes boucles</summary>

#### **For**

<pre class="language-java"><code class="lang-java"><strong>//FOR
</strong><strong>for (int i = 0; i &#x3C; 5; i++) {
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

[^1]: Le type de chaque variable doit être déclaré explicitement.

[^2]: Primitive Wrapper
