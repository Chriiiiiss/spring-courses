# Repository

Dans le package `com.api.crud.repository`, créez une interface `TaskRepository`.

TaskRepository est une interface qui étend JpaRepository pour gérer automatiquement nos requêtes crud.

{% code title="repository/TaskRepository.java" %}
```java
package com.api.crud.repository;

import com.api.crud.model.Task;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface TaskRepository extends JpaRepository<Task, Long> {
	
}
```
{% endcode %}

* **@Repository** : Indique que cette interface est un repository Spring.
* **JpaRepository** : Fournit des méthodes CRUD prêtes à l'emploi et peut être étendue pour des requêtes personnalisées.
