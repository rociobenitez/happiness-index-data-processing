# Ejemplo de bucles en Scala

En este ejemplo personalizado, hemos utilizado bucles en Scala para ilustrar tres situaciones diferentes:

Un bucle for que saluda a la persona (en este caso, a ti) cinco veces, utilizando la variable i para numerar las iteraciones.

Un bucle while que cuenta desde 0 hasta tu edad, imprimiendo cada año.

Otro bucle for que verifica si los números del 1 al 10 son pares o impares y muestra un mensaje correspondiente.

Al ejecutar el programa, obtendrás mensajes de salida que reflejarán las iteraciones y el conteo personalizados según tu nombre y edad.

```
object BuclesScala {
  def main(args: Array[String]): Unit = {
    val nombre = "Rocío"
    val edad = 30

    // Bucle for para imprimir un mensaje varias veces
    for (i <- 1 to 5) {
      println(s"¡Hola, $nombre! (Iteración $i)")
    }

    // Bucle while para contar hasta la edad
    var contador = 0
    while (contador < (edad / 2)) {
      println(s"Tienes $contador años.")
      contador += 1
    }

    // Bucle for con condición personalizada
    for (i <- 1 to 10) {
      if (i % 2 == 0) {
        println(s"$i es un número par.")
      } else {
        println(s"$i es un número impar.")
      }
    }
  }
}

```

**Consola:**

```
¡Hola, Rocío! (Iteración 1)
¡Hola, Rocío! (Iteración 2)
¡Hola, Rocío! (Iteración 3)
¡Hola, Rocío! (Iteración 4)
¡Hola, Rocío! (Iteración 5)
Tienes 0 años.
Tienes 1 años.
Tienes 2 años.
Tienes 3 años.
Tienes 4 años.
Tienes 5 años.
Tienes 6 años.
Tienes 7 años.
Tienes 8 años.
Tienes 9 años.
Tienes 10 años.
Tienes 11 años.
Tienes 12 años.
Tienes 13 años.
Tienes 14 años.
1 es un número impar.
2 es un número par.
3 es un número impar.
4 es un número par.
5 es un número impar.
6 es un número par.
7 es un número impar.
8 es un número par.
9 es un número impar.
10 es un número par.
```