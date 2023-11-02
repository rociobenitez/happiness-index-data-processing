# Ejemplo del uso de operadores en Scala

En este ejemplo, se demuestran varios tipos de operadores en Scala:

- *Operadores aritméticos* (suma, resta, multiplicación, división, módulo).
- *Operadores relacionales / de comparación* (igual, no igual, mayor que, menor que).
- *Operadores lógicos* (AND lógico, OR lógico, NOT lógico).
- *Operadores de asignación* (+=, -=, *=, /=).

El programa imprime los resultados de aplicar estos operadores a diferentes valores. Esto te dará una comprensión completa de cómo funcionan los operadores en Scala.

```
object OperadoresScala {
  def main(args: Array[String]): Unit = {
    // Operadores aritméticos
    val a = 10
    val b = 5
    val suma = a + b
    val resta = a - b
    val multiplicacion = a * b
    val division = a / b
    val modulo = a % b
    
    println(s"Suma: $suma")
    println(s"Resta: $resta")
    println(s"Multiplicación: $multiplicacion")
    println(s"División: $division")
    println(s"Módulo: $modulo")
    
    // Operadores de comparación
    val x = 10
    val y = 20
    val igual = x == y
    val noIgual = x != y
    val mayorQue = x > y
    val menorQue = x < y
    
    println(s"Igual: $igual")
    println(s"No Igual: $noIgual")
    println(s"Mayor Que: $mayorQue")
    println(s"Menor Que: $menorQue")
    
    // Operadores lógicos
    val condicion1 = true
    val condicion2 = false
    val andLogico = condicion1 && condicion2
    val orLogico = condicion1 || condicion2
    val notLogico = !condicion1
    
    println(s"AND Lógico: $andLogico")
    println(s"OR Lógico: $orLogico")
    println(s"NOT Lógico: $notLogico")
    
    // Operadores de asignación
    var variable = 5
    variable += 2 // Equivalente a variable = variable + 2
    variable -= 1 // Equivalente a variable = variable - 1
    variable *= 3 // Equivalente a variable = variable * 3
    variable /= 2 // Equivalente a variable = variable / 2
    
    println(s"Operadores de Asignación: $variable")
  }
}
```

**Consola:**

```
Suma: 15
Resta: 5
Multiplicación: 50
División: 2
Módulo: 0
Igual: false
No Igual: true
Mayor Que: false
Menor Que: true
AND Lógico: false
OR Lógico: true
NOT Lógico: false
Operadores de Asignación: 9
```