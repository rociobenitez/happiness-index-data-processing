# Ejemplo de Condicionales en Scala

En este ejemplo, hemos utilizado tus datos personales para crear un diagrama de flujo condicional que evalúa diferentes condiciones:

El primer diagrama de flujo verifica si eres mayor de edad o menor de edad según tu edad.

El segundo diagrama de flujo determina si eres desarrolladora web y estás aprendiendo Big Data, o si eres menor de edad, o si eres mayor de edad y no estás aprendiendo Big Data.

El tercer diagrama de flujo examina si vives en Madrid y, si es así, si eres desarrolladora web o no.

Al ejecutar el programa, obtendrás mensajes de salida personalizados que reflejan las condiciones basadas en tus datos personales.

```
object DiagramaDeFlujoPersonal {
  def main(args: Array[String]): Unit = {
    val nombre = "Rocío"
    val edad = 30
    val profesion = "desarrolladora web"
    val estaAprendiendoBigData = true
    val ciudad = "Madrid"

    // Diagrama de flujo con instrucción if-else
    if (edad < 18) {
      println(s"$nombre, eres menor de edad.")
    } else {
      println(s"$nombre, eres mayor de edad.")
    }

    // Diagrama de flujo con instrucción if-else-if-else
    if (estaAprendiendoBigData) {
      if (profesion == "desarrolladora web") {
        println(s"$nombre, eres desarrolladora web y estás aprendiendo Big Data.")
      } else {
        println(s"$nombre, no eres desarrolladora web, pero estás aprendiendo Big Data.")
      }
    } else if (edad < 18) {
      println(s"$nombre, eres menor de edad pero no estás aprendiendo Big Data.")
    } else {
      println(s"$nombre, eres mayor de edad y no estás aprendiendo Big Data.")
    }

    // Diagrama de flujo con instrucciones if-else anidadas
    if (ciudad == "Madrid") {
      if (profesion == "desarrolladora web") {
        println(s"$nombre, eres desarrolladora web que vive en Madrid.")
      } else {
        println(s"$nombre, no eres desarrolladora web, pero vives en Madrid.")
      }
    } else {
      println(s"$nombre, no vives en Madrid.")
    }
  }
}
```

**Consola:**

```
Rocío, eres mayor de edad.
Rocío, eres desarrolladora web y estás aprendiendo Big Data.
Rocío, eres desarrolladora web que vive en Madrid.
```