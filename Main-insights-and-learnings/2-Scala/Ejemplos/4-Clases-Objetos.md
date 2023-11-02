# Ejemplo de clases y objetos en Scala

```
// Definición de una clase llamada "Persona"
class Persona(nombre: String, edad: Int) {
  // Propiedades de la clase
  val nombreCompleto: String = s"$nombre (Edad: $edad)"

  // Método de la clase para saludar
  def saludar(): Unit = {
    println(s"Hola, mi nombre es $nombre y tengo $edad años.")
  }
}

// Objeto compañero (companion object) de la clase Persona
object Persona {
  // Método estático para crear instancias de Persona
  def apply(nombre: String, edad: Int): Persona = new Persona(nombre, edad)
}

object ClasesObjetosScala {
  def main(args: Array[String]): Unit = {
    // Creación de instancias de la clase Persona
    val persona1 = new Persona("Noa", 25)
    val persona2 = Persona("Rocío", 30)  // Usando el método apply del objeto compañero

    // Acceso a propiedades y métodos de las instancias
    println(persona1.nombreCompleto)
    persona2.saludar()
  }
}
```

**Consola:**
```
Noa (Edad: 25)
Hola, mi nombre es Rocío y tengo 30 años.
```

En este ejemplo, hemos definido una clase llamada "Persona" que tiene propiedades como nombre y edad, así como un método saludar que imprime un mensaje de saludo. También hemos definido un objeto compañero llamado "Persona" que tiene un método estático apply que permite crear instancias de la clase de manera más concisa.

En la función main, creamos dos instancias de la clase Persona: persona1 y persona2, y accedemos a sus propiedades y métodos. La salida del programa mostrará los nombres completos y mensajes de saludo de las personas.

Este ejemplo ilustra la definición de clases, la creación de objetos, el acceso a propiedades y métodos, así como el uso del objeto compañero en Scala.