## Clases de Datos

1. ## Introducción a las Clases de Datos

Las **clases de datos** en Kotlin son clases que se utilizan principalmente para almacenar datos. Su propósito principal es contener **información** y no tener comportamientos complejos. Kotlin proporciona una forma concisa y eficiente de crear este tipo de clases con la palabra clave `data`.

Cuando defines una clase de datos, Kotlin genera automáticamente varios métodos útiles para ti, como:
- `equals()`: Para comparar objetos por sus valores.
- `hashCode()`: Para generar un código hash basado en los valores.
- `toString()`: Para proporcionar una representación en cadena del objeto.
- `copy()`: Para crear una copia del objeto con la opción de modificar algunas propiedades.

1. ## Sintaxis de una Clase de Datos

```kotlin
data class Persona(val nombre: String, val edad: Int)
```
- `data class Persona` define una clase de datos.
- `val nombre` y `val edad` son las **propiedades** de la clase `Persona`.

1. ## Ejemplos de Clases de Datos

**Ejemplo 1: Creación y uso básico**
```kotlin
data class Persona(val nombre: String, val edad: Int)

fun main() {
    val persona1 = Persona("Ana", 25)
    val persona2 = Persona("Ana", 25)

    println(persona1)  // Salida: Persona(nombre=Ana, edad=25)

    // Comparación basada en los valores
    println(persona1 == persona2)  // Salida: true
}
```
- Aquí hemos creado una clase de datos `Persona` con dos propiedades: `nombre` y `edad`.
- Cuando creamos dos instancias (`persona1` y `persona2`) con los mismos valores, la clase de datos genera automáticamente un método `equals()`, lo que permite que se comparen por **valores** y no por la referencia de los objetos. Por eso, `persona1 == persona2` es `true`.
- Además, gracias al método `toString()` generado automáticamente, cuando imprimimos `persona1`, obtenemos una representación clara de sus valores.

**Ejemplo 2: Uso del método `copy()`**
```kotlin
data class Persona(val nombre: String, val edad: Int)

fun main() {
    val persona1 = Persona("Ana", 25)
    
    // Crear una copia de persona1, pero con una edad diferente
    val persona2 = persona1.copy(edad = 30)

    println(persona2)  // Salida: Persona(nombre=Ana, edad=30)
}
```
- El método `copy()` permite hacer una **copia** exacta de un objeto, pero con la opción de modificar algunas propiedades.
- En este caso, se crea una copia de `persona1`, pero cambiamos la propiedad `edad` de `25` a `30`, manteniendo el mismo `nombre`.
- Este es un método útil cuando trabajas con objetos **inmutables** y necesitas crear variantes de un objeto sin modificar el original.

**Ejemplo 3: Descomposición de una Clase de Datos**
```kotlin
data class Persona(val nombre: String, val edad: Int)

fun main() {
    val persona = Persona("Carlos", 32)

    // Descomposición en sus propiedades
    val (nombre, edad) = persona

    println("Nombre: $nombre, Edad: $edad")  // Salida: Nombre: Carlos, Edad: 32
}
```
- En este ejemplo, estamos utilizando una característica de Kotlin conocida como **descomposición**.
- Con las clases de datos, puedes extraer las propiedades directamente en variables separadas. Aquí, las propiedades `nombre` y `edad` se extraen de la instancia `persona` y se asignan a dos variables (`nombre` y `edad`).
- Esto es muy útil para evitar escribir código redundante al acceder a las propiedades de un objeto y hace que el código sea más legible.

1. ## 演習
