## Introducción a las clases

### Clases: Parámetros del constructor

Para **crear objetos con estados individuales dinámicos**, usaremos una combinación del ***método constructor y campos de instancia***.

Para asignar un valor a una variable de instancia, necesitamos modificar nuestro método constructor para incluir parámetros para que pueda acceder a los datos que queremos asignar a una instancia.

Ya hemos visto un parámetro en el método `main()`: `String[] args`, pero esta es la primera vez que usamos el valor del parámetro dentro del cuerpo de un método.

El `Carconstructor` ahora tiene un parámetro: `String carColor`:

```
public class Car {
  String color;
  // constructor method with a parameter
  public Car(String carColor) {
    // parameter value assigned to the field
    color = carColor;
  }
  public static void main(String[] args) {
    // program tasks
  }
}
```

Cuando se pasa un valor de cadena `Car()`, se asigna al parámetro `carColor`. Luego, dentro del constructor, `carColorse` asignará como valor a la variable de instancia color.

Nuestro método también tiene una firma que define el nombre y los parámetros del método. En el ejemplo anterior, la firma es Car(String carColor).

#### Cómo pasar valores a un método: Estudiantes de Ciencias de la Computación A AP

Hay dos tipos de parámetros: ***formales y reales***. Un parámetro formal especifica el tipo y nombre de los datos que se pueden pasar a un método. En nuestro ejemplo anterior, `String carColores` un parámetro formal; `carColor` representará cualquier String valor que se pase al constructor.

En Java, debido a la sobrecarga de [constructores](https://dev.java/learn/classes-objects/defining-constructors/), **una clase puede tener varios constructores siempre que tengan diferentes valores de parámetros**. La firma es útil porque ayuda al compilador a diferenciar entre los diferentes [métodos](https://dev.java/learn/classes-objects/defining-methods/) . Por ejemplo:

```
public class Car {
  String color;
  int mpg;
  boolean isElectric;

  // constructor 1
  public Car(String carColor, int milesPerGallon) {
    color = carColor;
    mpg = milesPerGallon;
  }
  // constructor 2
  public Car(boolean electricCar, int milesPerGallon) {
    isElectric = electricCar;
    mpg = milesPerGallon;
  }
}
```

En el ejemplo anterior, hay dos constructores. Cuando inicializamos un objeto, el compilador sabrá qué constructor usar debido a los valores que le pasamos. Por ejemplo, `Car myCar = new Car(true, 40)`` será creado por el segundo constructor porque los argumentos coinciden con el tipo y orden de la firma del segundo constructor.

Si no definimos un constructor, el compilador de Java generará un *constructor predeterminado* que no contiene argumentos y asigna los valores predeterminados del objeto. Los valores predeterminados se pueden crear asignando valores a los campos de instancia durante su declaración:

```
public class Car {
  String color = "red";
  boolean isElectric = false;
  int cupHolders = 4;

  public static main(String[] args) {
    Car myCar = new Car();
    System.println(myCar.color); // Prints: red
  }
}
```

### Clases: Asignación de valores a campos de instancia

Ahora que nuestro constructor tiene un parámetro, debemos pasar valores en la llamada al método. Estos valores se denominan ***argumentos***; una vez que se pasan, se utilizarán para dar el valor inicial a los campos de instancia.

Aquí creamos una instancia, `ferrari` en el `main()` con `"red"` como su campo `color`.

```
public class Car {
  String color;

  public Car(String carColor) {
    // assign parameter value to instance field
    color = carColor;
  }

  public static void main(String[] args) {
    // parameter value supplied when calling constructor
    Car ferrari = new Car("red");
  }
}
```

Pasamos el valor de cadena "rojo" a nuestra llamada al método constructor: new Car("rojo");.

El tipo del valor dado a la invocación debe coincidir con el tipo declarado por el parámetro.

Dentro del constructor, el parámetro `carColor` se refiere al valor pasado durante la invocación: "rojo". Este valor se asigna al campo de instancia color.

color ya ha sido declarado, por lo que no especificamos el tipo durante la asignación.

El objeto, ferrari, mantiene el estado de color como un campo de instancia que hace referencia al valor "rojo".

**Accedemos al valor de este campo con el operador punto (.):**

```
/*
accessing a field:
objectName.fieldName
*/

ferrari.color;
// "red"
```

Ejemplo:

```
public class Store {
  // instance fields
  String productType;
  
  // constructor method
  public Store(String product) {
    productType = product;
  }
  
  // main method
  public static void main(String[] args) {
    Store lemonadeStand = new Store("lemonade");
    System.out.println(lemonadeStand.productType);  
  }
}
```

### Clases: Múltiples Campos 

Los objetos no se limitan a un solo campo de instancia. Podemos declarar tantos campos como sean necesarios para los requisitos de nuestro programa.

Vamos a cambiar las instancias de Car para que tengan múltiples campos.

Añadiremos un booleano llamado isRunning, que indica si el motor del carro está encendido, y un entero llamado velocidad, que indica la velocidad a la que el carro está viajando.

```
public class Car {
  String color;
  // new fields!
  boolean isRunning;
  int velocity;
  
  // new parameters that correspond to the new fields
  public Car(String carColor, boolean carRunning, int milesPerHour) {
    color = carColor;
    // assign new parameters to the new fields
    isRunning = carRunning;
    velocity = milesPerHour;
  }

  public static void main(String[] args) {
    // new values passed into the method call
    Car ferrari = new Car("red", true, 27);
    Car renault = new Car("blue", false, 70);
    
    System.out.println(renault.isRunning);
    // false
    System.out.println(ferrari.velocity);
    // 27
  }
}
```

Debemos pasar valores a la invocación del constructor en el mismo orden en que aparecen en los parámetros.

```
// values match types, no error
Car honda = new Car("green", false, 0);

// values do not match types, error!
Car junker = new Car(true, 42, "brown");
```

Ejemplo práctico:

```
public class Store {
  // instance fields
  String productType;
  int inventoryCount;
  double inventoryPrice;
  
  // constructor method
  public Store(String product, int count, double price) {
    productType = product;
    inventoryCount = count;
    inventoryPrice = price;
  }
  
  // main method
  public static void main(String[] args) {
    Store cookieShop = new Store("cookies", 12, 3.75);
  }
}
```

Java es un lenguaje de programación orientado a objetos donde cada programa tiene al menos una clase. Los programas suelen construirse a partir de muchas clases y objetos, que son las instancias de una clase.

Las clases definen el estado y el comportamiento de sus instancias. El comportamiento proviene de métodos definidos en la clase. El estado proviene de campos de instancia declarados dentro de la clase.

Las clases se basan en las cosas del mundo real que queremos representar en nuestro programa. Más adelante exploraremos cómo se puede crear un programa a partir de varias clases. Por ahora, nuestros programas son de una sola clase.

```
public class Dog {
  // instance field
  String breed;
  // constructor method
  public Dog(String dogBreed) {
    /* 
    value of parameter dogBreed 
    assigned to instance field breed
    */
    breed = dogBreed;
  }
  public static void main(String[] args) {
    /* 
    create instance: 
    use 'new' operator and invoke constructor
    */
    Dog fido = new Dog("poodle");
    /* 
    fields are accessed using: 
    the instance name, `.` operator, and the field name.
    */
    fido.breed;
    // "poodle"
  }
}
```