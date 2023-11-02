# Ejemplos de uso de Arrays en Scala

```
object ArraysScala {
  def main(args: Array[String]): Unit = {
    // Declaración y creación de un array de números enteros
    val numeros = Array(1, 2, 3, 4, 5)

    // Acceso a elementos del array por índice
    val primerNumero = numeros(0)
    val segundoNumero = numeros(1)

    // Imprimir el array completo
    println("Array de números: " + numeros.mkString(", "))

    // Imprimir elementos individuales
    println(s"Primer número: $primerNumero")
    println(s"Segundo número: $segundoNumero")

    // Modificar un elemento del array
    numeros(2) = 10

    // Imprimir el array actualizado
    println("Array de números actualizado: " + numeros.mkString(", "))

    // Declaración y creación de un array de cadenas
    val colores = Array("Rojo", "Verde", "Azul")

    // Imprimir el array de cadenas
    println("Array de colores: " + colores.mkString(", "))
  }
}
```

**Consola:**

```
Array de números: 1, 2, 3, 4, 5
Primer número: 1
Segundo número: 2
Array de números actualizado: 1, 2, 10, 4, 5
Array de colores: Rojo, Verde, Azul
```

En este ejemplo, hemos creado un programa Scala que utiliza arrays para almacenar números enteros y cadenas de texto. Aquí se explican los conceptos clave:

Se declara y crea un array de números enteros llamado numeros con valores del 1 al 5.

Los elementos del array se pueden acceder por índice, y en este caso, hemos obtenido el primer y segundo números.

Se imprime el array completo utilizando mkString para convertirlo en una cadena legible.

Luego, se modifica un elemento del array al cambiar el valor en la tercera posición (índice 2) a 10.

Se declara y crea un array de cadenas llamado colores con valores "Rojo", "Verde" y "Azul".

Finalmente, se imprime el array de colores.

Este ejemplo ilustra cómo declarar, crear, acceder y modificar arrays en Scala, tanto para números enteros como para cadenas de texto.


## Métodos de Arrays

```
object ArraysMetodosScala {
  def main(args: Array[String]): Unit = {
    // Datos personales
    val nombre = "Rocío"
    val edad = 30
    val actividades = Array("Crossfit", "Atletismo")
    val actividades2 = Array("Natación", "Yoga")

    // Método: length (tamaño del array)
    val numActividades = actividades.length
    println(s"$nombre tiene $numActividades actividades.")

    // Método: contains (verificar si un elemento está en el array)
    val practicaCrossfit = actividades.contains("Crossfit")
    val practicaNatacion = actividades.contains("Natación")
    println(s"$nombre practica Crossfit: $practicaCrossfit")
    println(s"$nombre practica Natación: $practicaNatacion")

    // Método: indexOf (obtener el índice de un elemento)
    val indiceAtletismo = actividades.indexOf("Atletismo")
    println(s"$nombre practica Atletismo en la posición $indiceAtletismo del array.")

    // Método: mkString (convertir array en una cadena)
    val actividadesStr = actividades.mkString(", ")
    println(s"$nombre realiza las siguientes actividades: $actividadesStr")

    // Método: concat (concatenar dos arrays)
    val todasLasActividades = actividades.concat(actividades2)
    println(s"Todas las actividades: ${todasLasActividades.mkString(", ")}")

    // Método: distinct (eliminar elementos duplicados)
    val actividadesUnicas = todasLasActividades.distinct
    println(s"Actividades únicas: ${actividadesUnicas.mkString(", ")}")

    // Método: sorted (ordenar el array)
    val actividadesOrdenadas = actividadesUnicas.sorted
    println(s"Actividades ordenadas de $nombre: ${actividadesOrdenadas.mkString(", ")}")

    // Método: slice (obtener una porción del array)
    val actividadesDosYTres = todasLasActividades.slice(1, 3)
    println(s"Actividades en la posición 2 y 3: ${actividadesDosYTres.mkString(", ")}")
  }
}
```

**Consola:**

```
Rocío tiene 2 actividades.
Rocío practica Crossfit: true
Rocío practica Natación: false
Rocío practica Atletismo en la posición 1 del array.
Rocío realiza las siguientes actividades: Crossfit, Atletismo
Todas las actividades: Crossfit, Atletismo, Natación, Yoga
Actividades únicas: Crossfit, Atletismo, Natación, Yoga
Actividades ordenadas de Rocío: Atletismo, Crossfit, Natación, Yoga
Actividades en la posición 2 y 3: Atletismo, Natación
```

En este ejemplo, hemos utilizado tus datos personales y un array de actividades para demostrar algunos métodos comunes de arrays:

1. `length`: Obtenemos el tamaño del array para saber cuántas actividades realizas.

2. `contains`: Verificamos si ciertas actividades (por ejemplo, "Crossfit" y "Natación") están presentes en el array.

3. `indexOf`: Encontramos el índice de un elemento específico en el array ("Atletismo" en este caso).

4. `mkString`: Convertimos el array de actividades en una cadena legible, separando los elementos por comas.

5. `concat`: Concatenamos dos arrays de actividades (actividades1 y actividades2) para obtener una lista completa de todas las actividades que realizas.

6. `distinct`: Eliminamos elementos duplicados del array para obtener una lista de actividades únicas.

7. `sorted`: Ordenamos las actividades únicas alfabéticamente.

8. `slice`: Obtenemos una porción del array, en este caso, las primeras dos actividades.

Al ejecutar el programa, obtendrás mensajes de salida que muestran cómo se utilizan estos métodos con tus datos personales y tu array de actividades.