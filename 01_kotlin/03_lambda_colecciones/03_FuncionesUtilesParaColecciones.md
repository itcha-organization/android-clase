# Uso básico de funciones de orden superior con colecciones
En Kotlin, existen varias funciones de orden superior que permiten manipular colecciones como listas, conjuntos y mapas de manera eficiente. Estas funciones simplifican tareas como filtrar, transformar y agrupar elementos dentro de las colecciones.

A continuación, se explican algunas de las funciones de orden superior más utilizadas para operar con colecciones en Kotlin.

## 1. map: Transformar elementos

### **Descripción:**
La función `map` transforma cada elemento de una colección aplicando una función y devuelve una nueva colección con los resultados. La colección original no se modifica.
### **Sintaxis:**
```kotlin
val result = collection.map { it -> transform(it) }
```
- `collection`: La colección que se va a transformar.
- `transform`: La operación que se aplica a cada elemento.
### **Ejemplo:**
```kotlin
val numeros = listOf(1, 2, 3, 4, 5)
val cuadrados = numeros.map { it * it }
println(cuadrados)  // Salida: [1, 4, 9, 16, 25]
```
### Minicuestionario
1. **Pregunta**:  
   ¿Cuál es el propósito de la función `map` en Kotlin?
   - A) Reemplazar elementos de una lista
   - B) Transformar cada elemento de una lista según una función dada
   - C) Filtrar elementos de una lista
   - D) Ordenar una lista

<details>
  <summary>Respuesta</summary>
  
  B) Transformar los elementos de una lista según una función dada  
  **Explicación:**
  - La función `map` transforma los elementos de una lista o colección aplicando una función a cada uno de ellos, generando una nueva lista con los resultados.
</details>

2. **Pregunta**:  
   Dada la lista `val numeros = listOf(1, 2, 3, 4, 5)`, ¿qué devuelve el siguiente código?
   ```kotlin
   val resultado = numeros.map { it * 2 }
   ```
   - A) `[1, 2, 3, 4, 5]`
   - B) `[2, 4, 6, 8, 10]`
   - C) `[0, 1, 2, 3, 4]`
   - D) `[5, 4, 3, 2, 1]`

<details>
  <summary>Respuesta</summary>
  
  B) `[2, 4, 6, 8, 10]` 
  **Explicación:**
  - La función `map` multiplica cada elemento de la lista `numeros` por 2. Si `numeros` contiene `[1, 2, 3, 4, 5]`, el resultado será `[2, 4, 6, 8, 10]`.
</details>

3. **Pregunta**:  
   Si tienes una lista de cadenas `val nombres = listOf("Ana", "Luis", "Carlos")`, ¿qué hará la función `map` con el siguiente código?
   ```kotlin
   val resultado = nombres.map { it.length }
   ```
   - A) Convertirá todas las cadenas a mayúsculas
   - B) Devolverá una lista con las longitudes de las cadenas
   - C) Devolverá una lista con las primeras letras de cada nombre
   - D) Filtrará los nombres con más de 4 caracteres

<details>
  <summary>Respuesta</summary>
  
  B) Devolver una lista con la longitud de cada cadena  
  **Explicación:**
  - En este caso, `map` devuelve la longitud de cada cadena de la lista `nombres`, resultando en una lista con las longitudes de los nombres.
</details>

4. **Pregunta**:  
   ¿Es posible aplicar `map` sobre un conjunto (Set) en Kotlin?
   - A) Sí
   - B) No

<details>
  <summary>Respuesta</summary>
  
  A) Sí  
  **Explicación:**
  - La función `map` puede aplicarse no solo a listas, sino también a otros tipos de colecciones como Set, aunque los resultados duplicados no serán permitidos en un Set.
</details>

5. **Pregunta**:  
   ¿Qué se imprime con el siguiente código?
   ```kotlin
   val numeros = listOf(10, 20, 30)
   val resultado = numeros.map { it + 5 }
   println(resultado)
   ```
   - A) `[10, 20, 30]`
   - B) `[5, 15, 25]`
   - C) `[15, 25, 35]`
   - D) `[50, 60, 70]`

<details>
  <summary>Respuesta</summary>
  
  C) `[15, 25, 35]`  
  **Explicación:**
  - La función `map` suma 5 a cada elemento de la lista `numeros`, resultando en `[15, 25, 35]`.
</details>

6. **Pregunta**:  
   ¿Qué sucede si aplicas `map` a una lista vacía en Kotlin?
   - A) Genera un error
   - B) Devuelve `null`
   - C) Devuelve una lista vacía
   - D) Llena la lista con valores predeterminados

<details>
  <summary>Respuesta</summary>
  
  C) Devuelve una lista vacía  
  **Explicación:**
  - Cuando `map` se aplica a una lista vacía, no hay elementos para transformar, por lo tanto, el resultado es una lista vacía.
</details>

7. **Pregunta**:  
   ¿Cuál es el resultado de este código?
   ```kotlin
   val numeros = listOf(1, 2, 3)
   val resultado = numeros.map { if (it % 2 == 0) it * 2 else it }
   println(resultado)
   ```
   - A) `[2, 4, 6]`
   - B) `[1, 4, 3]`
   - C) `[1, 2, 3]`
   - D) `[2, 4, 5]`

<details>
  <summary>Respuesta</summary>
  
  B) `[1, 4, 3]` 
  **Explicación:**
  - En este caso, la función `map` multiplica por 2 solo los números pares. Así, `1` y `3` se quedan igual, mientras que `2` se convierte en `4`.
</details>

8. **Pregunta**:  
   ¿Cómo puedes usar `map` para convertir una lista de números enteros a una lista de cadenas con el texto "Número: X", donde X es el número?
   - A) `val resultado = lista.map { "Número: $it" }`
   - B) `val resultado = lista.map { it.toString() }`
   - C) `val resultado = lista.filter { it > 0 }`
   - D) `val resultado = lista.mapNotNull { "Número: $it" }`

<details>
  <summary>Respuesta</summary>
  
  A) `val resultado = lista.map { "Número: $it" }`
  **Explicación:**
  - La función `map` toma cada elemento de la lista y lo transforma en una cadena del formato `"Número: $it"`.
</details>

9. **Pregunta**:  
    ¿Qué hace el siguiente código?
    ```kotlin
    val palabras = listOf("uno", "dos", "tres")
    val resultado = palabras.map { it.toUpperCase() }
    println(resultado)
    ```
    - A) Convierte todas las palabras a minúsculas
    - B) Convierte todas las palabras a mayúsculas
    - C) Devuelve la longitud de las palabras
    - D) Filtra las palabras de más de 3 letras

<details>
  <summary>Respuesta</summary>
  
  B) Convertir todas las palabras en mayúsculas  
  **Explicación:**
  - La función `map` aplica `toUpperCase()` a cada elemento de la lista, convirtiendo las palabras en mayúsculas. El resultado será `["UNO", "DOS", "TRES"]`.
</details>

## 2. filter: Filtrar elementos según una condición
   
### **Descripción:**
La función `filter` devuelve una nueva colección que contiene solo los elementos que cumplen con una condición dada.

### **Sintaxis:**
```kotlin
val result = collection.filter { it -> condition(it) }
```
- `collection`: La colección original.
- `condition`: La condición que cada elemento debe cumplir para ser incluido en la nueva colección.
### **Ejemplo:**
```kotlin
val numeros = listOf(1, 2, 3, 4, 5)
val numerosPares = numeros.filter { it % 2 == 0 }
println(numerosPares)  // Salida: [2, 4]
```
### Miniejercicio
1. **¿Cuál es la función principal de `filter` en Kotlin?**
   A) Sumar todos los elementos de una lista  
   B) Filtrar los elementos de una lista según una condición  
   C) Transformar los elementos de una lista

<details>
  <summary>Respuesta</summary>
  
  B) Filtrar los elementos de una lista según una condición  
  **Explicación:**
  - La función `filter` selecciona los elementos de una colección que cumplen una condición especificada y devuelve una nueva colección con esos elementos.
</details>

2. **¿Qué devolverá el siguiente código?**
   ```kotlin
   val numeros = listOf(1, 2, 3, 4, 5)
   val resultado = numeros.filter { it % 2 == 0 }
   println(resultado)
   ```
   A) `[2, 4]`  
   B) `[1, 3, 5]`  
   C) `[1, 2, 3, 4, 5]`

<details>
  <summary>Respuesta</summary>
  
  A) `[2, 4]`  
  **Explicación:**
  - `filter` selecciona solo los números pares de la lista. El operador `%` (módulo) comprueba si el número es divisible por 2 sin dejar residuo, es decir, los pares.
</details>

3. **¿Cuál será el resultado del siguiente código?**
   ```kotlin
   val palabras = listOf("kotlin", "java", "javascript", "python")
   val resultado = palabras.filter { it.startsWith("j") }
   println(resultado)
   ```
   A) `["java", "javascript"]`  
   B) `["python"]`  
   C) `["kotlin", "python"]`

<details>
  <summary>Respuesta</summary>
  
  A) `["java", "javascript"]` 
  **Explicación:**
  - `filter` selecciona solo las palabras que empiezan con la letra "j" usando el método `startsWith`.
</details>

4. **¿Es posible usar `filter` en un Set en Kotlin?**
   A) Sí  
   B) No

<details>
  <summary>Respuesta</summary>
  
  A) Sí   
  **Explicación:**
  - `filter` se puede aplicar a cualquier colección en Kotlin, incluidas listas, conjuntos (Sets) y mapas (Maps).
</details>

5. **¿Qué hará el siguiente código?**
   ```kotlin
   val numeros = listOf(10, 20, 30, 40)
   val resultado = numeros.filter { it > 25 }
   println(resultado)
   ```
   A) `[10, 20]`  
   B) `[30, 40]`  
   C) `[10, 20, 30, 40]`

<details>
  <summary>Respuesta</summary>
  
  B) `[30, 40]` 
  **Explicación:**
  - La condición `it > 25` filtra solo los números mayores que 25, resultando en `[30, 40]`.
</details>

6. **¿Qué devolverá `filter` cuando se aplique a una lista vacía?**
   A) Una excepción  
   B) Una lista vacía  
   C) `null`

<details>
  <summary>Respuesta</summary>
  
  B) Una lista vacía
  **Explicación:**
  - Si se aplica `filter` a una lista vacía, no hay elementos para evaluar, por lo que devuelve una nueva lista vacía.
</details>

7. **¿Qué sucederá si aplicas `filter` con una condición que no se cumple para ningún elemento?**
   ```kotlin
   val numeros = listOf(1, 2, 3)
   val resultado = numeros.filter { it > 5 }
   println(resultado)
   ```
   A) Imprimirá `[1, 2, 3]`  
   B) Imprimirá una lista vacía  
   C) Generará un error

<details>
  <summary>Respuesta</summary>
  
  B) Imprimirá una lista vacía 
  **Explicación:**
  - Ningún número en la lista original es mayor que 5, por lo que `filter` devuelve una lista vacía.
</details>

8. **¿Cómo filtrarías una lista de números para quedarte solo con los números negativos?**
   A) `val resultado = numeros.filter { it > 0 }`  
   B) `val resultado = numeros.filter { it < 0 }`  
   C) `val resultado = numeros.filter { it == 0 }`

<details>
  <summary>Respuesta</summary>
  
  B) `val resultado = numeros.filter { it < 0 }`
  **Explicación:**
  - La condición `it < 0` selecciona solo los números negativos.
</details>

9. **¿Qué imprimirá el siguiente código?**
   ```kotlin
   val lista = listOf(100, 200, 300, 400)
   val resultado = lista.filter { it >= 300 }
   println(resultado)
   ```
   A) `[300, 400]`  
   B) `[100, 200, 300, 400]`  
   C) `[100, 200]`

<details>
  <summary>Respuesta</summary>
  
  A) `[300, 400]`  
  **Explicación:**
  - La condición `it >= 300` selecciona los números que son mayores o iguales a 300.
</details>

10. **¿Es correcto el siguiente uso de `filter`?**
    ```kotlin
    val numeros = listOf(1, 2, 3, 4, 5)
    val resultado = numeros.filter { it -> it % 2 == 1 }
    println(resultado)
    ```
    A) Sí  
    B) No

<details>
  <summary>Respuesta</summary>
  
  A) Sí
  **Explicación:**
  - Esta es una forma correcta de usar `filter`. Aunque `it` ya está disponible como el valor actual, es válido usar `it ->` en la sintaxis lambda para mayor claridad, aunque normalmente se omite por conveniencia.
</details>

## 3. reduce: Acumular los elementos en un solo valor
### **Descripción:**
La función `reduce` permite combinar los elementos de una colección en un solo valor, aplicando una operación de acumulación secuencial.
### **Sintaxis:**
```kotlin
val result = collection.reduce { acc, element -> operation(acc, element) }
```
- `acc`: El valor acumulado hasta el momento.
- `element`: El elemento actual que se está procesando.
- `operation`: La operación que se aplica a `acc` y `element`.
### **Ejemplo:**
```kotlin
val numeros = listOf(1, 2, 3, 4, 5)
val suma = numeros.reduce { acc, numero -> acc + numero }
println(suma)  // Salida: 15
```

## 4. forEach: Ejecutar una acción en cada elemento
### **Descripción:**
La función `forEach` aplica una operación a cada elemento de la colección. No devuelve ningún valor, simplemente realiza la acción.
### **Sintaxis:**
```kotlin
collection.forEach { it -> action(it) }
```
- `collection`: La colección sobre la que se ejecuta la acción.
- `action`: La operación que se aplica a cada elemento.
### **Ejemplo:**
```kotlin
val numeros = listOf(1, 2, 3, 4, 5)
numeros.forEach { println(it) }
// Salida: 
// 1
// 2
// 3
// 4
// 5
```

## 5. find: Encontrar el primer elemento que cumpla una condición
### **Descripción:**
La función `find` devuelve el primer elemento que cumpla con la condición especificada. Si ningún elemento cumple la condición, devuelve `null`.
### **Sintaxis:**
```kotlin
val result = collection.find { it -> condition(it) }
```
- `condition`: La condición que se debe cumplir.
### **Ejemplo:**
```kotlin
val numeros = listOf(1, 2, 3, 4, 5)
val primerPar = numeros.find { it % 2 == 0 }
println(primerPar)  // Salida: 2
```

## 6. Ejercicios Prácticos

1. Usa la función `filter` para obtener una lista de números pares de una colección.
2. Aplica la función `map` para convertir una lista de cadenas en mayúsculas.
3. Utiliza la función `reduce` para calcular el producto de todos los números de una lista.
