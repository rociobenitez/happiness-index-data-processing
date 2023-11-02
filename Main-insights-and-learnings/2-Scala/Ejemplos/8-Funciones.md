# Ejemplo de Funciones en Scala

En este ejemplo, hemos definido tres funciones:

1. `describirPersona`: Describe los datos personales, incluyendo el nombre, la edad, la ciudad y el nombre de la mascota.

2. `describirIntereses`: Describe las actividades e intereses, mostrando las actividades físicas y las áreas de aprendizaje.

3. `mensajePersonal`: Genera un mensaje personalizado basado en el nombre, la ciudad y la fecha actual.

Al llamar a estas funciones en la función `main`, obtendrás una descripción de tus datos personales, tus actividades e intereses, y un mensaje personalizado basado en los datos proporcionados.


```
object FuncionesScala {
  def main(args: Array[String]): Unit = {
    // Datos personales
    val nombre = "Rocío"
    val edad = 30
    val ciudad = "Madrid"
    val mascota = "Noa"

    // Actividades e intereses
    val actividades = List("Crossfit", "Atletismo")
    val aprendizaje = List("Big Data", "Análisis de Datos", "Inteligencia Artificial")

    // Llamar a la función para describir datos personales
    describirPersona(nombre, edad, ciudad, mascota)

    // Llamar a la función para describir actividades e intereses
    describirIntereses(actividades, aprendizaje)

    // Llamar a la función para obtener un mensaje personalizado
    val mensaje = mensajePersonal(nombre, ciudad, "noviembre de 2023")
    println(mensaje)
  }

  // Función para describir datos personales
  def describirPersona(nombre: String, edad: Int, ciudad: String, mascota: String): Unit = {
    println(s"Soy $nombre, tengo $edad años y vivo en $ciudad.")
    println(s"Tengo un perro que se llama $mascota.")
  }

  // Función para describir actividades e intereses
  def describirIntereses(actividades: List[String], aprendizaje: List[String]): Unit = {
    println(s"Practico las siguientes actividades: ${actividades.mkString(", ")}")
    println(s"Estoy aprendiendo: ${aprendizaje.mkString(", ")}")
  }

  // Función para obtener un mensaje personalizado
  def mensajePersonal(nombre: String, ciudad: String, fecha: String): String = {
    s"Estamos a $fecha y mi nombre es $nombre. Vivo en $ciudad y me encanta aprender nuevas cosas."
  }
}
```

**Consola:**

```
Soy Rocío, tengo 30 años y vivo en Madrid.
Tengo un perro que se llama Noa.
Practico las siguientes actividades: Crossfit, Atletismo
Estoy aprendiendo: Big Data, Análisis de Datos, Inteligencia Artificial
Estamos a noviembre de 2023 y mi nombre es Rocío. Vivo en Madrid y me encanta aprender nuevas cosas.
```