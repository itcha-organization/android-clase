# Uso básico de las clases

## 1. ¿Qué son las clases y los objetos?
En Kotlin, una clase es una plantilla para definir objetos, y un objeto es una instancia creada a partir de una clase. Las clases pueden tener propiedades (variables) y métodos (funciones), mientras que los objetos utilizan estas propiedades y métodos.

**Sintaxis: Definición básica de una clase e instanciación**
```kotlin
fun main() {
    // Instanciación de la clase. No se utiliza la palabra clave new.
    val persona1 = Persona("Juan", 30)
    // Llamada de método
    persona1.presentarse()  // Salida: Hola, me llamo Juan y tengo 30 años.
}

// Definición de una clase
class Persona(val nombre: String, var edad: Int) {
    
    // Método (función)
    fun presentarse() {
        println("Hola, me llamo $nombre y tengo $edad años.")
    }
}
```
- Defínala escribiendo la palabra clave `class` seguida del nombre de la clase y de llaves.
- No se utiliza la palabra clave `new` en instanciación.
- Como en otros lenguajes, las clases pueden definir funciones. Las funciones pueden invocarse utilizando instancias de clases.

La clase `Persona` se puede escribir en C# de la siguiente manera.Puedes ver que el caso de Kotlin es significativamente más corto.
```csharp
class Persona
{
    public string Nombre { get; }
    public int Edad { get; set; }

    // Constructor
    public Persona(string nombre, int edad)
    {
        Nombre = nombre;
        Edad = edad;
    }

    // Método (función)
    public void Presentarse()
    {
        Console.WriteLine($"Hola, me llamo {Nombre} y tengo {Edad} años.");
    }
}
```

## 2. Propiedades
Como en otros lenguajes, las clases pueden tener tanto propiedades como métodos. Las propiedades almacenan datos, mientras que los métodos realizan operaciones sobre esos datos.

**Sintaxis: Getter y Setter de una propiedad**
```kotlin
fun main() {
    // Instanciación de la clase
    val persona = Persona("Juan", 20)

    // Llamando a Getters
    println(persona.nombre)  // "Juan"
    println(persona.esAdulto)  // true

    // Llamando a Setters
    persona.apellido = "garcia"
    println(persona.apellido)  // "GARCIA"
}

// Definición de una clase
class Persona(val nombre: String, var edad: Int) {
    
    // Getter personalizado
    val esAdulto: Boolean
        get() = edad >= 18

    // Setter personalizado
    var apellido: String = ""
        set(value) {
            field = value.uppercase()  // Convertir a mayúsculas y poner
        }
}
```
- Las propiedades pueden definirse en dos lugares.
  - **Entre paréntesis después del nombre de la clase:** Aquí se definen las propiedades que son argumentos para el constructor primario.
  - **Entre llaves:** Aquí se definen las propiedades que no son argumentos del constructor primario.
- Las propiedades pueden definirse utilizando la misma sintaxis que las variables con `var` y `val`.`nombre` es de sólo lectura, `edad` es modificable.
- Getter y Setter se definen implícitamente sin código.Por ejemplo, un Getter y Setter para `nombre` no está definido, pero puede acceder a los valores de `nombre`.
- Si desea añadir procesamiento a Getter y Setter, también puede definirlo explícitamente.
  - La propiedad **`esAdulto`** define un getter personalizado, que devuelve `true` si `edad` es 18 o mayor.
  - La propiedad **`apellido`** define un setter personalizado, que convierte el valor a mayúsculas y lo asigna a `field`.
- `field` es una palabra clave especial utilizada en setters en propiedades Kotlin.`field` se utiliza para establecer valores para propiedades en setters personalizados.

## 3. Constructores
En Kotlin, las clases pueden tener un constructor primario y constructores secundarios. El constructor primario se define inmediatamente después de la declaración de la clase, mientras que los constructores secundarios se definen dentro del cuerpo de la clase.

**Sintaxis:**
![image](https://github.com/user-attachments/assets/fed18b1b-9d64-446f-90fb-9b9a9a334d66)

### **Ejemplo: Constructor primario y constructor secundario**
```kotlin
fun main() {
    // Uso
    val persona1 = Persona("Juan", 30)
    val persona2 = Persona("Ana")
    persona1.presentarse()  // Salida: Hola, me llamo Juan y tengo 30 años.
    persona2.presentarse()  // Salida: Hola, me llamo Ana y tengo 0 años.

}

class Persona(val nombre: String, var edad: Int) {
    // Constructor secundario
    constructor(nombre: String) : this(nombre, 0) {
        println("El nombre es $nombre, pero la edad no ha sido proporcionada.")
    }
    // Método (función)
    fun presentarse() {
        println("Hola, me llamo $nombre y tengo $edad años.")
    }
}
```
- El constructor primario inicializa las propiedades de la clase.
- El constructor secundario realiza una inicialización adicional. Su sintaxis incluye tres partes:
  - Declaración del constructor secundario. La definición del constructor secundario comienza con la palabra clave constructor, seguida de paréntesis. Si corresponde, los paréntesis contienen los parámetros que requiere el constructor secundario.
  - Inicialización del constructor principal. La inicialización comienza con dos puntos, seguidos de la palabra clave this y un conjunto de paréntesis. Si corresponde, los paréntesis contienen los parámetros que requiere el constructor principal.
  - Cuerpo del constructor secundario. A la inicialización del constructor principal le sigue un conjunto de llaves, que contienen el cuerpo del constructor secundario.

## 4. Minicuestionario

```kotlin
class Rectangulo(var ancho: Int, var alto: Int) {
    
    // Propiedad que calcula el área
    val area: Int
        get() = ancho * alto
    
    // Setter personalizado para la altura
    var altura: Int = alto
        set(value) {
            if (value > 0) {
                field = value
            } else {
                println("La altura debe ser positiva.")
            }
        }
}
```
  1. ¿Cuántas propiedades hay?
  1. ¿Qué propiedades son de sólo lectura?
  1. ¿Cuál es el resultado de ejecutar el siguiente código?
      ```kotlin
      fun main() {
          // Crear una instancia
          val rectangulo = Rectangulo(5, 10)
          // Usar el getter de la propiedad
          println("Área: ${rectangulo.area}")
      }
      ```
  1. ¿Cuál es el resultado de ejecutar el siguiente código?
      ```kotlin
      fun main() {
          // Crear una instancia
          val rectangulo = Rectangulo(5, 10)
          // Usar el setter de la propiedad
          rectangulo.altura = 15
          println("Nueva altura: ${rectangulo.altura}")
      }
      ```
  1. ¿Cuál es el resultado de ejecutar el siguiente código?
      ```kotlin
      fun main() {
          // Crear una instancia
          val rectangulo = Rectangulo(5, 10)
          // Usar el setter de la propiedad
          rectangulo.altura = -5
          println("Nueva altura: ${rectangulo.altura}")
      }
      ```

```kotlin
class Coche(val marca: String, var modelo: String) {

    constructor(marca: String, modelo: String, año: Int) : this(marca, modelo) {
        println("El coche es un $marca $modelo del año $año.")
    }

    fun moverse() {
        println("El vehículo se está moviendo.")
    }
}
```
  1. ¿Cuántas propiedades hay?
  1. ¿Cuáles son los argumentos del constructor principal?
  1. ¿Cuáles son los constructores secundarios?
  1. ¿Cuáles son los argumentos del constructor secundario?
  1. Consideremos un ejemplo de código que llama a un constructor secundario.

## 5. Ejercicios
