# Expresiones Lambda

1. ## ¿Qué es una Expresión Lambda?
Una **expresión lambda** es una función anónima que puedes tratar como una **primera clase** en Kotlin. Esto significa que puedes asignarla a una variable, pasarla como parámetro o devolverla desde otras funciones. Las lambdas permiten escribir código más conciso y expresivo, especialmente al trabajar con funciones de orden superior.

### **Sintaxis de las Expresiones Lambda**
La sintaxis de una lambda en Kotlin es muy compacta. Aquí está su estructura básica:
```kotlin
{ parámetros -> cuerpo de la función }
```
- **Parámetros**: Son los valores de entrada de la lambda, que pueden ser uno o más.
- **Cuerpo de la función**: Es el bloque de código que se ejecuta cuando la lambda es llamada. Puede ser una sola expresión o un bloque de varias líneas.
  
#### **Ejemplo básico:**
```kotlin
val suma: (Int, Int) -> Int = { a, b ->
    a + b
}
```
- Aquí, `suma` es una variable que contiene una lambda que toma dos enteros (`a` y `b`) y devuelve su suma.
- `(Int, Int) -> Int` indica que el tipo de datos es un tipo de función que acepta dos parámetros `Int` y devuelve un valor de tipo `Int`.
- Puedes llamar a esta lambda como cualquier otra función:
```kotlin
println(suma(3, 4))  // Salida: 7
```

### **Sintaxis del tipo de dato de Lambda(las funciones)**
Los tipos de funciones consisten en un conjunto de paréntesis que contienen una lista de parámetros, el símbolo -> y un tipo de datos que se muestra.

![image](https://github.com/user-attachments/assets/f6b9c0c5-33da-4f7a-a3c1-72b610049140)
#### **Ejemplos**
```kotlin
// Parámetros: Sin parámetros
// Tipo de retorno: Unit - No devuelve nada
val saludo: () -> Unit = {
    println("Hola mundo!")
}

// Parámetros: 3 valores de Int
// Tipo de retorno: Int
val sumaTres: (Int, Int, Int) -> Int = { a, b, c ->
    a + b + c
}

// Parámetros: 1 valor de Int
// Tipo de retorno: String
val decierEdad: (Int) -> String = { edad ->
    "Tengo $edad años."
}
```

### **Minicuestionario**
- ¿Cuáles son los parámetros y tipo de retorno de los siguientes tipos de datos de función?
  ```kotlin
  () -> Boolean
  ```
  ```kotlin
  (Boolean, String, Int) -> Unit
  ```
- Responda al siguiente código de ejemplo para el tipo de datos de cada expresión lambda.
  ```kotlin
  // #1
  val imprimirMensaje = { mensaje: String ->
      println(mensaje)
  }
  
  // #2
  val procesarTexto = { texto: String ->
      val textoEnMayusculas = texto.toUpperCase()
      val longitud = textoEnMayusculas.length
      println("Texto en mayúsculas: $textoEnMayusculas")
      println("Longitud del texto: $longitud")
      longitud
  }

  // #3
  val compararNumeros = { a: Int, b: Int ->
        val resultado = if (a > b) {
            "El primer número es mayor"
        } else if (a < b) {
            "El segundo número es mayor"
        } else {
            "Los números son iguales"
        }
        println("Comparación: $resultado")
        resultado
  }
  ```
1. ## Funciones que aceptan lambdas como argumentos

Es posible pasar lambdas como argumentos a funciones, lo que permite definir el comportamiento dinámicamente. En otras palabras, puedes pasar una función como parámetro para ser ejecutada dentro de otra función.

### Ejemplos

La siguiente función `ejecutarOperacion` toma dos enteros y una función lambda que acepta dos enteros como parámetros y devuelve un entero.
Esta función ejecuta la operación proporcionada sobre los valores `a` y `b`, y devuelve el resultado.
```kotlin
fun ejecutarOperacion(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}
```
**Ejemplo 1: Usando una lambda para realizar una suma**
```kotlin
fun main() {
    // Lambda para sumar dos números
    val sumar = { x: Int, y: Int -> x + y }

    // Pasar la lambda a la función
    val resultado = ejecutarOperacion(5, 10, sumar)

    println("El resultado de la suma es: $resultado")  // Salida: El resultado de la suma es: 15
}

fun ejecutarOperacion(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}
```
En este ejemplo, se pasa la lambda `sumar` a la función `ejecutarOperacion` para calcular la suma de `5 + 10`.

**Ejemplo 2: Usando una lambda para realizar una multiplicación**
```kotlin
fun main() {
    // Lambda para multiplicar dos números
    val multiplicar = { x: Int, y: Int -> x * y }

    // Pasar la lambda a la función
    val resultado = ejecutarOperacion(5, 10, multiplicar)

    println("El resultado de la multiplicación es: $resultado")  // Salida: El resultado de la multiplicación es: 50
}

fun ejecutarOperacion(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}
```
Aquí, utilizamos una lambda `multiplicar` para realizar una multiplicación con la misma función `ejecutarOperacion`.

**Ejemplo 3: Pasar lambda directamente como argumentos**

En los ejemplos anteriores, la lambda se asignaba a una variable y luego la variable se pasaba a la función como argumento.En este ejemplo, la lambda encerrada en llaves se pasa directamente a la función como argumento.

Usando lambdas, podemos pasar diferentes tipos de operaciones a la misma función, permitiendo ejecutar diferentes lógicas sin duplicar código.
Aquí, usamos la misma función `ejecutarOperacion` para sumar o restar números según la lambda que se pase.
```kotlin
fun main() {
    val a = 8
    val b = 4

    // Sumar
    val resultadoSuma = ejecutarOperacion(a, b, { x, y -> x + y })
    println("Suma: $resultadoSuma")  // Salida: Suma: 12

    // Restar
    val resultadoResta = ejecutarOperacion(a, b, { x, y -> x - y })
    println("Resta: $resultadoResta")  // Salida: Resta: 4
}

fun ejecutarOperacion(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}
```

1. ## Sintaxis simplificada en lambdas (uso de `it`)

Cuando una expresión lambda tiene un solo parámetro, es posible omitir la declaración del parámetro y usar la palabra clave **`it`** en Kotlin. Este `it` se utiliza automáticamente como el único parámetro de la lambda.

### Forma habitual: Con el parámetro explícito
```kotlin
val duplicar = { numero: Int ->
    numero * 2
}
val resultado = duplicar(5)
println(resultado)  // Salida: 10
```
### Sintaxis simplificada usando `it`
```kotlin
val duplicar = {
    it * 2
}
val resultado = duplicar(5)
println(resultado)  // Salida: 10
```
Ambos ejemplos realizan la misma operación, pero el segundo ejemplo utiliza `it` para simplificar la sintaxis.

### Cuándo usar `it`:
El uso de `it` es útil cuando queremos escribir funciones de una manera concisa. Sin embargo, si la operación es compleja o se requiere más de un parámetro, es recomendable declarar explícitamente los nombres de los parámetros para mejorar la legibilidad.

### **Minicuestionario**
- Reescribe las siguientes lambdas con la sintaxis simplificada usando `it`.
  ```kotlin
  # 1
  val imprimirMensaje = { mensaje: String ->
      println(mensaje)
  }  
  
  # 2
  val decierEdad: (Int) -> String = { edad ->
    "Tengo $edad años."
  }
  
  # 3
    val procesarTexto = { texto: String ->
      val textoEnMayusculas = texto.toUpperCase()
      val longitud = textoEnMayusculas.length
      println("Texto en mayúsculas: $textoEnMayusculas")
      println("Longitud del texto: $longitud")
      longitud
  }
  ```

1. ## Lambda de última posición
En Kotlin, si el último argumento de una función es una lambda, puedes colocar esa lambda **fuera de los paréntesis** de la llamada a la función. Esto se conoce como **trailing lambda** o **lambda de última posición**.

### Forma habitual
```kotlin
fun procesarNumeros(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}

val resultado = procesarNumeros(5, 10, { x, y -> x + y })
println(resultado)  // Salida: 15
```
### Usando lambda de última posición
```kotlin
val resultado = procesarNumeros(5, 10) { x, y -> x + y }
println(resultado)  // Salida: 15
```
Como la lambda es el último argumento de la función, podemos sacarla fuera de los paréntesis, lo que hace que el código sea más fácil de leer.
Esto se debe a que las funciones con una lambda como último argumento aparecen con frecuencia en el framework JetpackCompose que conocerás en el futuro. Por lo tanto, esta sintaxis es muy importante.

### **Minicuestionario**
- Reescribe las siguientes llamadas de funciones usando lambda de última posición.
  ```kotin
  # 1
  // Reescribe la siguiente llamada usando lambda de última posición
  val resultado = operar(5, 3, { x, y -> x + y })
  
  fun operar(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
  }
  ```
  ```kotin
  # 2
  // Reescribe la siguiente llamada usando lambda de última posición
  ejecutarSiCondicionEsVerdadera(true, {
      println("¡Es de día!")
  })

  fun ejecutarSiCondicionEsVerdadera(esDia: Boolean, accion: () -> Unit) {
      if (condicion()) {
          accion()
      }
  }
  ```
  ```kotin
  # 3
  // Reescribe la siguiente llamada usando lambda de última posición
  ejecutarAccion ({ println("He ejectado algo") })
  
  fun ejecutarAccion(accion: () -> Unit) {
      accion()
  }
  ```

1. ## 演習
