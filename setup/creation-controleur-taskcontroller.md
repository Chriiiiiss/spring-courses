# Contrôleur

Dans le package `com.api.crud.controller`, créez une classe `TaskController`.

Utilisez les annotations `@RestController` et `@RequestMapping`.

Injectez (`@Autowired`) `TaskService`.

{% code title="controller/TaskController.java" %}
```java
@RestController
@RequestMapping("/tasks")
public class TaskController {
    private final TaskService taskService;

    @Autowired
    public TaskController(TaskService taskService) {
        this.taskService = taskService;
    }

    @GetMapping
    public List<Task> getTasks() {
        return taskService.getTasks();
    }

    // Autres endpoints...
}
```
{% endcode %}

* **@RestController** : Indique que cette classe est un contrôleur Spring Boot qui gère les requêtes HTTP.
* **@RequestMapping** : Définit l'URL de base pour toutes les requêtes traitées par ce contrôleur.
* **Méthodes** : Chaque méthode correspond à un endpoint HTTP pour effectuer des opérations CRUD.
