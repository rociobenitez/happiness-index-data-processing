# Tipos de datos en Scala

En este ejemplo, se declaran variables de diferentes tipos de datos, como Int, Double, Char, Boolean y String. Luego, se realizan operaciones con estos tipos de datos, incluyendo aritmética y concatenación. También se muestran ejemplos de arreglos y listas en Scala.

Al ejecutar este programa, obtendrás una salida que muestra el valor de las variables y los resultados de las operaciones con diferentes tipos de datos. Esto ilustra la diversidad de tipos de datos disponibles en Scala y cómo se pueden utilizar en programas.

```
object TiposDeDatosScala {
  def main(args: Array[String]): Unit = {
    // Declaración de variables con asignación de valores
    val entero: Int = 42
    val decimal: Double = 3.14159265359
    val caracter: Char = 'A'
    val booleano: Boolean = true
    val cadena: String = "Hola, Rocío!"

    // Imprimir variables
    println(s"Entero: $entero")
    println(s"Decimal: $decimal")
    println(s"Caracter: $caracter")
    println(s"Booleano: $booleano")
    println(s"Cadena: $cadena")

    // Operaciones con tipos de datos
    val sumaEnteros = entero + 10
    val multiplicacionDecimales = decimal * 2.0
    val concatenacionCadenas = cadena + " Vamos a aprender Scala!"

    println(s"Suma de enteros: $sumaEnteros")
    println(s"Multiplicación de decimales: $multiplicacionDecimales")
    println(s"Concatenación de cadenas: $concatenacionCadenas")

    // Arreglos
    val arregloEnteros: Array[Int] = Array(1, 2, 3, 4, 5)
    val arregloCadenas: Array[String] = Array("Windows", "macOS", "Linux")

    println(s"Arreglo de enteros: ${arregloEnteros.mkString(", ")}")
    println(s"Arreglo de cadenas: ${arregloCadenas.mkString(", ")}")

    // Listas
    val listaEnteros: List[Int] = List(1, 2, 3, 4, 5)
    val listaCadenas: List[String] = List("Java", "Scala", "Spark")

    println(s"Lista de enteros: ${listaEnteros.mkString(", ")}")
    println(s"Lista de cadenas: ${listaCadenas.mkString(", ")}")
  }
}
```

**Consola:**

```
Entero: 42
Decimal: 3.14159265359
Caracter: A
Booleano: true
Cadena: Hola, Rocío!
Suma de enteros: 52
Multiplicación de decimales: 6.28318530718
Concatenación de cadenas: Hola, Rocío! Vamos a aprender Scala!
Arreglo de enteros: 1, 2, 3, 4, 5
Arreglo de cadenas: Windows, macOS, Linux
Lista de enteros: 1, 2, 3, 4, 5
Lista de cadenas: Java, Scala, Spark
```