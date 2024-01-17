# La Quête du Café Perdu

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Java Joe le barista</p></figcaption></figure>

Il va falloir aider un barista nommé Java Joe dans sa quête pour trouver la recette parfaite de café. Java Joe a plusieurs recettes, mais il a besoin d'un système pour les gérer efficacement.

{% code title="Requête à exécuter dans la console h2" %}
```sql
CREATE TABLE recette (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    nom VARCHAR(255),
    description TEXT,
    ingredients TEXT,
    instructions TEXT
);
```
{% endcode %}

<details>

<summary>Exemple d'une Interface de projection</summary>

{% code title="interface/TaskProjection.java" %}
```java
public interface TaskProjection {
    Long getId();
    String getTitle();
}
```
{% endcode %}

La méthode dans le repository ressemblera donc à ça

{% code title="repository/TaskRepository.java" %}
```java
List<TaskProjection> findAllProjectedBy();
```
{% endcode %}

</details>

### Voici la marche à suivre

* Créer un model `Recette` avec des attributs : `nom`, `description`, `ingredients`, et `instructions`.
* Exécuter la requête sql via la h2-console pour créer la table en base de donnée
* Définir une interface de projection pour les données à récupérer. Cela va permettre de spécifier exactement quelles propriétés de l'entité `Recette` on veux extraire.
* Créer une classe `RecetteRepository` qui va hériter de `JpaRepository<Recette, Long>`
* Créer le service
* Créer une classe `RecetteController`
  * Il faudra au moins faire la méthode `GET` pour valider
  * Mais les autres c'est que du bonus :smile:
