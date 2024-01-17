# Entité

L'entité `Task` représentera les tâches à gérer. Elle aura les attributs suivants :

* `id` (Long) : Identifiant unique de la tâche.
* `title` (String) : Titre de la tâche.
* `completed`(String) : Statut de la tâche.

Dans le package `com.api.crud.model`, créez une classe `Task`.

Ajoutez les attributs mentionnés avec les annotations appropriées (`@Entity`, `@Id`, `@GeneratedValue`).

{% code title="model/Task.java" %}
```java

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;

@Entity
public class Task {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
	
    private String title;
	
    private boolean completed;

    // Getters et setters
}
```
{% endcode %}

* **@Entity** : Indique que cette classe est une entité JPA.
* **@Id** et **@GeneratedValue** : Identifient le champ `id` comme clé primaire et configurent la stratégie de génération de l'identifiant.
* **Champs** : `title` et `completed` représentent les données de la tâche
