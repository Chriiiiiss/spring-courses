# Service

Dans le package `com.api.crud.service`, créez une classe `TaskService`. Injectez (`@Autowired`) `TaskRepository` et ajoutez des méthodes pour gérer les tâches.

{% code title="service/TaskService.java" %}
```java
@Service
public class TaskService {
    private final TaskRepository taskRepository;

    @Autowired
    public TaskService(TaskRepository taskRepository) {
        this.taskRepository = taskRepository;
    }

    public List<Task> getTasks() {
        return taskRepository.findAll();
    }
    // Autres méthodes...
}


```
{% endcode %}

* **@Service** : Marque la classe comme un service Spring, une couche pour la logique métier.
* **@Autowired** : Injecte automatiquement l'instance de `TaskRepository`.
* **Méthodes** : Implémente la logique métier, comme sauvegarder une tâche.
