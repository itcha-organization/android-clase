# Expresiones Lambda

基本
・ラムダ構文を使用して関数を定義する方法。
・関数を変数に格納する方法。
クイズ

関数を引数として他の関数に渡す方法。
他の関数から関数を返す方法。
ラムダ式をより簡潔にする方法。
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
ココマデ

1. ## Uso de Lambdas con Tipos de Función

Las lambdas pueden ser asignadas a variables con tipos de función. Esto es útil para hacer explícitos los tipos de entrada y salida.

#### **Ejemplo con un tipo de función:**

```kotlin
val multiplicar: (Int, Int) -> Int = { a, b -> a * b }
println(multiplicar(4, 3))  // Salida: 12
```

- Aquí, el tipo de la variable `multiplicar` está explícitamente definido como una función que recibe dos enteros y devuelve un entero.

### **Lambdas como Parámetros de Funciones**

Las lambdas son muy útiles cuando las pasamos como parámetros a otras funciones. Esto es lo que hace posible las **funciones de orden superior**.

#### **Ejemplo:**

```kotlin
fun operarNumeros(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}

fun main() {
    val resultado = operarNumeros(10, 5) { x, y -> x - y }
    println(resultado)  // Salida: 5
}
```

- Aquí, la función `operarNumeros` toma dos números y una función lambda como parámetros. En este caso, usamos una lambda para realizar la operación de resta.

### **Lambdas en Kotlin vs Funciones Anónimas**

Kotlin también permite definir **funciones anónimas**, que son similares a las lambdas pero con una sintaxis más tradicional. Las funciones anónimas pueden ser útiles cuando necesitas un mayor control sobre el retorno o el tipo de la función.

#### **Ejemplo de función anónima:**

```kotlin
val resta = fun(a: Int, b: Int): Int {
    return a - b
}

println(resta(10, 3))  // Salida: 7
```

- Aquí, hemos definido una función anónima que resta dos números y la asignamos a la variable `resta`.

### **Lambdas con Múltiples Líneas**

Aunque las lambdas generalmente se usan para funciones concisas, también pueden contener varias líneas de código. En estos casos, debes usar `{}` para definir el bloque de código.

#### **Ejemplo con varias líneas:**

```kotlin
val calcular: (Int, Int) -> Int = { a, b ->
    val suma = a + b
    val resta = a - b
    suma * resta
}

println(calcular(7, 3))  // Salida: 40
```

- Esta lambda realiza múltiples operaciones dentro de su cuerpo: suma los valores, los resta y luego multiplica los resultados.

### **Ejemplos de uso de Lambdas en Colecciones**

Una de las principales aplicaciones de las lambdas en Kotlin es el manejo de colecciones. Muchas funciones de la biblioteca estándar, como `map`, `filter`, `reduce`, y `forEach`, toman lambdas como argumentos.

#### **Ejemplo:**

```kotlin
val numeros = listOf(1, 2, 3, 4, 5)
val numerosPares = numeros.filter { it % 2 == 0 }
println(numerosPares)  // Salida: [2, 4]
```

- Aquí usamos una lambda para filtrar solo los números pares de la lista.

### **Conclusión**

Las **expresiones lambda** son una característica fundamental en Kotlin que permiten escribir código más expresivo y funcional. Al ser compactas y poderosas, permiten una mejor legibilidad y flexibilidad en el código. Las lambdas son particularmente útiles cuando se combinan con funciones de orden superior y manipulación de colecciones.

---

Este material ofrece una vista más detallada sobre las **lambdas** y cómo usarlas en diferentes contextos. Las lambdas son una herramienta poderosa en Kotlin, especialmente cuando trabajas con colecciones o necesitas escribir código funcional y conciso.



Una **expresión lambda** es una función anónima que puede ser tratada como un valor. Es compacta y muy útil cuando trabajamos con funciones de orden superior o manipulamos colecciones.

#### **Sintaxis básica de una lambda:**

```kotlin
val suma = { a: Int, b: Int -> a + b }
```

#### **Ejemplo con Lambdas:**

```kotlin
val imprimirMensaje: () -> Unit = { println("Hola desde una lambda") }

fun main() {
    imprimirMensaje()  // Salida: Hola desde una lambda
}
```

**Explicación**:
- Definimos una variable `imprimirMensaje` que es una función lambda sin parámetros (`() -> Unit`) y simplemente imprime un mensaje.
- Luego, la llamamos como cualquier otra función.


### **1. Introducción a las Funciones de Orden Superior**

Las **funciones de orden superior** en Kotlin son funciones que pueden recibir otras funciones como parámetros, o bien, pueden devolver una función. Este es un concepto clave en la programación funcional, ya que permite un estilo más declarativo y flexible.

#### **Ejemplo básico:**

```kotlin
fun operar(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}

fun main() {
    // Suma usando una función lambda
    val resultado = operar(5, 3) { x, y -> x + y }
    println(resultado)  // Salida: 8
}
```

**Explicación**:
- La función `operar` acepta dos enteros (`a` y `b`) y una función `operacion` que toma dos enteros y devuelve un entero.
- Luego, llamamos a `operar` pasando una **expresión lambda** que realiza la suma (`x + y`).


### **3. Operaciones con Colecciones**

Kotlin ofrece una rica API para manipular colecciones como `List`, `Set`, y `Map`, utilizando funciones de orden superior y expresiones lambda. Estas funciones permiten realizar operaciones como filtrado, transformación, y reducción de colecciones de una manera concisa y legible.

#### **Operaciones comunes:**

1. **`map`:** Transforma cada elemento de la colección.
2. **`filter`:** Filtra los elementos según una condición.
3. **`forEach`:** Aplica una acción a cada elemento.

#### **Ejemplo: Uso de `map` y `filter`**

```kotlin
fun main() {
    val numeros = listOf(1, 2, 3, 4, 5, 6)
    
    // Map - multiplicar cada número por 2
    val numerosDoblados = numeros.map { it * 2 }
    println(numerosDoblados)  // Salida: [2, 4, 6, 8, 10, 12]

    // Filter - obtener solo los números pares
    val numerosPares = numeros.filter { it % 2 == 0 }
    println(numerosPares)  // Salida: [2, 4, 6]
}
```

**Explicación**:
- **`map`** toma cada elemento de la lista `numeros` y lo multiplica por 2, devolviendo una nueva lista `numerosDoblados`.
- **`filter`** selecciona solo los números que son pares, devolviendo una nueva lista `numerosPares`.

### **4. Ejercicios para Practicar**

#### **Ejercicio 1: Usar funciones de orden superior**
Define una función `aplicarOperacion` que tome dos números y una operación (suma, resta, multiplicación o división) como una función lambda, y devuelve el resultado.

#### **Ejercicio 2: Usar lambdas con `forEach`**
Crea una lista de nombres y utiliza `forEach` para imprimir cada nombre con un saludo personalizado, por ejemplo, "Hola, Juan".

#### **Ejercicio 3: Filtrar y transformar una lista de personas**
Crea una clase `Persona` con propiedades `nombre` y `edad`. Luego, crea una lista de personas y filtra aquellas que tienen más de 18 años. Después, usa `map` para crear una lista de nombres en mayúsculas.

---

### **Conclusión**

En esta clase hemos aprendido sobre **funciones de orden superior**, que nos permiten usar funciones como parámetros y resultados. También exploramos las **expresiones lambda**, una forma compacta de definir funciones, y cómo podemos usarlas para manipular **colecciones** en Kotlin de manera sencilla y eficiente. Las herramientas proporcionadas por Kotlin hacen que escribir código conciso, legible y poderoso sea más fácil.

---

Este material te proporciona una base sólida para enseñar sobre las funciones de orden superior, expresiones lambda, y las operaciones con colecciones en Kotlin. ¡Espero que sea útil para tu clase!
