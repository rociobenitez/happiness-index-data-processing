# Métodos

## Definición de métodos

```
public void checkBalance(){
    // Cuerpo del método
    System.out.println("Hola!");
    System.out.println("Tu balance es " + balance);
}
```

- `public void checkBalance()` es la declaración del método.
- `public` significa que otras clases pueden acceder a este método.
- `void` (palabra clave) significa que no hay un resultado específico del método.
- `checkBalance()` es el nombre del método.

Cada método tiene su propia *firma de método* única que se compone del nombre del método y su tipo de parámetro. En este ejemplo, la firma del método es `checkBalance()`.

`checkBalance()` se considera un método no estático porque su firma no incluye la palabra clave `static` como lo hace el método `main()`.

### Añadir método a una clase

```
public class Store {
    // instance fields
    String productType;

    // constructor method
    public Store(String product) {
        productType = product;
    }

    // advertise method
    public void advertise() {
        System.out.println("Come spend some money!");
        System.out.println("Selling " + productType + "!");
    }

    // main method
    public static void main(String[] args){

    }
}
```

## Llamando al método

```
class Car {

    String color;

    public Car(String carColor) {
        color = carColor;
    }

    public void startEngine() {
        System.out.println("Starting the car!");
    }

    public static void main(String[] args) {
        Car myFastCar = new Car("red")
        // Call a method on an object
        myFastCar.startEngine()
        System.out.println("That was one fast car!");
    }

}
```

## Scope

El **alcance** define dónde se puede acceder a una determinada variable o método en un programa. Todo lo que está dentro de las llaves es el alcance de un método. No podemos acceder a variables que están declaradas dentro de un método en código que está fuera del alcance de ese método.

Las variables pueden tener 3 tipos de scopes:

- **Alcance a nivel de clase (Class level scope)** *(variables de instancia)*: cualquier variable declarada dentro de una clase es accesible para todos los métodos de esa clase. Dependiendo de su *modificador de acceso (public o private)*, a veces se puede acceder a él fuera de la clase.

- **Alcance a nivel de método (method level scope)** *(variables locales)*: cualquier variable declarada dentro de una método, incluidos los argumentos, NO es accesible fuera de ese método.

- **Alcance de bloque (block scope)** *(loop variables - variables de buble)*: cualquier variable declarada en un bucle `for` NO es accesible después del bucle, a menos que se haya definido de antemano.

## Modificadores de acceso

En Java, existen cuatro **modificadores de acceso* que restringen la accesibilidad del método o variable al que se aplica el modificador. Sólo se utilizan dentro de clases, no dentro de métodos.

- `private`: El modificador **más restrictivo**. Limita el acceso a métodos y variables a la clase en la que están declarados. Se elige cuando no es necesario utilizar ciertos métodos o variables fuera de la clase.
- `default`: Permite el acceso solo desde el paquete actual. Si no hay ningún modificador de acceso especificado, el método o variable asumirá este.
- `protected`: Permite el acceso a un método o variable solo desde dentro del paquete actual, a menos que se acceda a través de una clase secundaria fuera del paquete.
- `public`: El modificador **menos restrictivo**. Permite el acceso a una clase, método o variable no solo desde dentro de la clase en la que se está declarado, sino también desde fuera. Este es el que se usa con mayor frecuencia.