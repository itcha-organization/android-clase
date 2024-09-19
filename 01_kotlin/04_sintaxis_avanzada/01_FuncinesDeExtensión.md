# Funciones de extensión

## **1. ¿Qué son las funciones de extensión?**
Una función de extensión es una función que se añade a una clase existente, como si fuera parte de ella, sin alterar su implementación original. Puedes agregar nuevas funcionalidades a clases ya definidas en bibliotecas o incluso en el lenguaje mismo.

### **Sintaxis básica:**
```kotlin
fun NombreDeClase.nombreDeLaFuncion(argumentos): TipoDeRetorno {
    // Cuerpo de la función
}
```
#### **Puntos clave:**
- **`NombreDeClase`**: La clase a la que se le agrega la función.
- **`nombreDeLaFuncion`**: El nombre de la nueva función.
- **`argumentos`**: Si la función necesita argumentos, estos se especifican aquí.
- **`TipoDeRetorno`**: El tipo de dato que devolverá la función.

## **2. Ejemplos de funciones de extensión**

### **Ejemplo: Agregar una función de extensión a la clase `String`**
```kotlin
fun String.saludar() {
    println("¡Hola, me llamo $this!")
}

fun main() {
    val nombre = "Kotlin"
    nombre.saludar()  // Salida: ¡Hola, me llamo Kotlin!
}
```
#### **Explicación:**
En este ejemplo, agregamos una función `saludar()` a la clase `String`. La palabra clave `this` se refiere al objeto sobre el cual se llama la función (en este caso, un `String`), lo que nos permite acceder a él dentro de la función de extensión.

## **3. Uso práctico de funciones de extensión**

Las funciones de extensión pueden hacer que el código sea más claro y reutilizable. Por ejemplo, al extender clases existentes o bibliotecas, puedes agregar nuevas funcionalidades sin modificar su implementación original.

### **Ejemplo: Función de extensión para capitalizar palabras en una lista de cadenas**
Imagina que tienes una lista de nombres y quieres capitalizar la primera letra de cada nombre. Podrías escribir una función de extensión que lo haga de forma sencilla:
```kotlin
fun List<String>.capitalizar(): List<String> {
    return this.map { it.capitalize() }
}

fun main() {
    val nombres = listOf("ana", "juan", "carlos")
    val nombresCapitalizados = nombres.capitalizar()
    
    println(nombresCapitalizados)  // Salida: [Ana, Juan, Carlos]
}
```
#### **Explicación:**
- En este caso, estamos extendiendo la clase `List<String>` para agregar la función `capitalizar()`. Esta función toma cada elemento de la lista (que es un `String`) y usa la función `capitalize()` para poner la primera letra de cada palabra en mayúsculas.
- Luego devolvemos una nueva lista con los nombres capitalizados.

## **4. Restricciones de las funciones de extensión**

Las funciones de extensión tienen algunas limitaciones.

1. **No pueden acceder a miembros privados o protegidos**:
   Como las funciones de extensión no son verdaderos métodos de la clase, no pueden acceder a propiedades o métodos privados o protegidos de la clase.

### **Ejemplo: No se puede acceder a propiedades privadas**
```kotlin
class Persona(val nombre: String, private val edad: Int)

fun Persona.mostrarEdad() {
    // println("Edad: $edad")  // Error: 'edad' es privado
}

fun main() {
    val persona = Persona("Kotlin", 7)
    persona.mostrarEdad()  // No se puede acceder a miembros privados
}
```

## **5. Ejercicios**

### Ejercicios1:
1. Define una función de extensión `cuadrado()` para el tipo `Int`, que devuelva el cuadrado del número.
2. Utilice el código inicial en la siguiente URL. También se proporciona el código de prueba para que lo pruebes.
   https://pl.kotl.in/E21nQHK-p

### Ejercicios2:
1. Define una función de extensión `mayusculas()` para el tipo `List<String>`, que cambia cada elemento a mayúsculas y devuelve una nueva lista que contiene el elemento que se ha cambiado a mayúsculas.
2. Utilice el código inicial en la siguiente URL. También se proporciona el código de prueba para que lo pruebes.
   https://pl.kotl.in/HH2xL58-i

Respuesta:
   https://pl.kotl.in/7gqUBhI0r
