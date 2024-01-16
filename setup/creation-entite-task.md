# Création de l'entité

L'entité `Task` représentera les tâches à gérer. Elle aura les attributs suivants :

* `id` (Long) : Identifiant unique de la tâche.
* `title` (String) : Titre de la tâche.
* `completed`(String) : Statut de la tâche ("oui" : 1, "non":0).

Dans le package `com.api.crud.model`, créez une classe `Task`.

Ajoutez les attributs mentionnés avec les annotations appropriées (`@Entity`, `@Id`, `@GeneratedValue`).

```java
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

* **@Entity** : Indique que cette classe est une entité JPA.
* **@Id** et **@GeneratedValue** : Identifient le champ `id` comme clé primaire et configurent la stratégie de génération de l'identifiant.
* **Champs** : `title` et `completed` représentent les données de la tâche