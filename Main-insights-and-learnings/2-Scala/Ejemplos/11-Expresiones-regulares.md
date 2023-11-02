# Ejemplo de uso de Expresiones Regulares en Scala

```
import scala.util.matching.Regex

object ExpresionesRegularesScala {
  def main(args: Array[String]): Unit = {
    // Texto de ejemplo que contiene información sobre números de teléfono
    val texto = "Mi número de teléfono es 123-456-7890 y otro número es 555-123-4567."

    // Definir una expresión regular para buscar números de teléfono en formato xxx-xxx-xxxx
    val patronTelefono = """\d{3}-\d{3}-\d{4}""".r

    // Encontrar todos los números de teléfono en el texto
    val numerosTelefono = patronTelefono.findAllIn(texto)

    // Imprimir los números de teléfono encontrados
    println("Números de teléfono encontrados:")
    numerosTelefono.foreach(println)

    // Extraer los números de teléfono y almacenarlos en una lista
    val listaNumeros = patronTelefono.findAllIn(texto).toList
    println("Lista de números de teléfono:")
    println(listaNumeros)
  }
}
```

**Consola:**

```
Números de teléfono encontrados:
123-456-7890
555-123-4567
Lista de números de teléfono:
List(123-456-7890, 555-123-4567)
```

En este ejemplo, hemos utilizado expresiones regulares en Scala para buscar y extraer números de teléfono en un texto de ejemplo. Aquí se explican los conceptos clave:

- Hemos definido una expresión regular (`patronTelefono`) que busca números de teléfono en el formato `xxx-xxx-xxxx`, donde "x" representa dígitos.

- Utilizamos `findallIn` para encontrar todos los números de teléfono en el texto y almacenarlos en un iterador `numerosTelefono`.

- Imprimimos los números de teléfono encontrados uno por uno.

- Extraemos los números de teléfono y los almacenamos en una lista llamada `listaNumeros`.

Al ejecutar el programa, obtendrás mensajes de salida que mostrarán los números de teléfono encontrados en el texto. Este ejemplo ilustra cómo usar expresiones regulares para buscar y extraer información específica de una cadena de texto en Scala.