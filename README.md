# Lista de Tareas App

Esta es una aplicación de Lista de Tareas desarrollada en Flutter con el uso del patrón Provider para gestionar el estado de las tareas.

## Levantar el Proyecto

1. **Requisitos Previos:**
   - Asegúrate de tener Flutter y Dart instalados en tu máquina. Puedes seguir las [instrucciones de instalación](https://flutter.dev/docs/get-started/install).

2. **Clonar el Repositorio:**
   ```bash
   git clone https://github.com/tu-usuario/tu-repositorio.git
   cd tu-repositorio
   ```

3. **Instalar Dependencias:**
   ```bash
   flutter pub get
   ```

4. **Ejecutar la Aplicación:**
   ```bash
   flutter run
   ```

## Estructura de Archivos

- **lib/modelo/task.dart:** Define la clase `Task` que representa el modelo de una tarea.

  ```dart
  class Task {
    String title;
    String description;
    bool isCompleted;

    Task({required this.title, required this.description, this.isCompleted = false});
  }
  ```

- **lib/providers/taskProvider.dart:** Implementa el patrón Provider y maneja el estado de las tareas en la aplicación.

  ```dart
    import 'package:flutter/material.dart';
    import 'package:examenformativo/modelo/task.dart';

    class TaskProvider extends ChangeNotifier {
    List<Task> _tasks = [];

    List<Task> get tasks => _tasks;

    void addTask(Task task) {
        _tasks.add(task);
        notifyListeners();
    }

    void updateTask(int index, Task task) {
        _tasks[index] = task;
        notifyListeners();
    }

    void removeTask(int index) {
        _tasks.removeAt(index);
        notifyListeners();
    }
    }

  ```

- **lib/vista/taskListScreen.dart:** La pantalla principal de la aplicación que muestra la lista de tareas. Permite marcar tareas como completadas, eliminar tareas y navegar a la pantalla de agregar/editar tareas.

  ```dart
  class TaskListScreen extends StatelessWidget {
    
  }
  ```

- **lib/vista/testCreateScreen.dart:** La pantalla para agregar o editar tareas. Utiliza un formulario para ingresar detalles de la tarea. También muestra el estado de completado y permite cambiarlo.

    ```dart
    class AddEditTaskScreen extends StatelessWidget {
    
    }

    ```

- **lib/main.dart:** Configura la aplicación Flutter, estableciendo `TaskProvider` como proveedor principal y definiendo `TaskListScreen` como la pantalla de inicio.

  ```dart
    class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return ChangeNotifierProvider(
        create: (context) => TaskProvider(),
        child: MaterialApp(
            title: 'Lista de Tareas',
            theme: ThemeData(
            primarySwatch: Colors.blue,
            ),
            home: TaskListScreen(),
        ),
        );
    }
    }
  ```

## Funcionalidades Clave

- **Vista de Lista de Tareas:**
  - Muestra una lista de tareas con título, descripción y estado de completado.
  - Permite marcar tareas como completadas.
  - Permite eliminar tareas de la lista.

- **Agregar/Editar Tareas:**
  - Proporciona un formulario para ingresar nuevos detalles de tarea (título, descripción).
  - Permite a los usuarios editar tareas existentes.

- **Patrón Provider:**
  - Utiliza el patrón Provider para gestionar el estado de las tareas en la aplicación.

- **Arquitectura y Código:**
  - Sigue una arquitectura limpia y modular.
  - El código está bien estructurado y documentado.



