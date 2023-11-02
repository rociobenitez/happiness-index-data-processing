# Ejemplo de uso de Colecciones (Listas) en Scala

```
object ColeccionesListasScala {
  def main(args: Array[String]): Unit = {
    // Declaración y creación de una lista de tareas
    val tareas = List("Estudiar Scala", "Practicar Big Data", "Hacer ejercicio")

    // Acceso a elementos de la lista por índice
    val primeraTarea = tareas(0)
    val segundaTarea = tareas(1)

    // Imprimir la lista completa
    println("Lista de tareas: " + tareas.mkString(", "))

    // Imprimir elementos individuales
    println(s"Primera tarea: $primeraTarea")
    println(s"Segunda tarea: $segundaTarea")

    // Agregar elementos a la lista (creando una nueva lista)
    val tareasActualizadas = tareas :+ "Leer un libro" :+ "Hacer la compra"
    println("Lista de tareas actualizada: " + tareasActualizadas.mkString(", "))

    // Filtrar elementos que contienen la palabra "Hacer"
    val tareasFiltradas = tareasActualizadas.filter(tarea => tarea.contains("Hacer"))
    println("Tareas que contienen 'Hacer': " + tareasFiltradas.mkString(", "))
  }
}
```

**Consola:**

```
Lista de tareas: Estudiar Scala, Practicar Big Data, Hacer ejercicio
Primera tarea: Estudiar Scala
Segunda tarea: Practicar Big Data
Lista de tareas actualizada: Estudiar Scala, Practicar Big Data, Hacer ejercicio, Leer un libro, Hacer la compra
Tareas que contienen 'Hacer': Hacer ejercicio, Hacer la compra
```

En este ejemplo, hemos creado un programa Scala que utiliza una lista (List) para gestionar tareas. Aquí se explican los conceptos clave:

- Se declara y crea una lista de tareas (`tareas`) que contiene tres elementos.

- Los elementos de la lista se pueden acceder por índice, y en este caso, hemos obtenido la primera y segunda tarea.

- Se imprime la lista completa utilizando `mkString` para convertirla en una cadena legible.

- Luego, se agrega elementos adicionales a la lista (`"Leer un libro"`` y `"Hacer la compra"`) creando una nueva lista (`tareasActualizadas`).

- Finalmente, se filtran las tareas que contienen la palabra "Hacer" para obtener una lista de tareas que cumplen con ese criterio.

Este ejemplo ilustra cómo declarar, crear, acceder, modificar y filtrar una lista en Scala para administrar tareas o elementos de una colección.