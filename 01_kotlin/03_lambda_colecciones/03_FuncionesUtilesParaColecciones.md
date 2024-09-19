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

### Minicuestionario
1. **¿Cuál es la función principal de `reduce` en Kotlin?**  
   A) Convertir una lista en un conjunto  
   B) Acumular los elementos de una colección en un solo valor  
   C) Filtrar elementos de una colección  
   D) Dividir una colección en varias partes

<details>
  <summary>Respuesta</summary>
  
  B) Acumular los elementos de una colección en un solo valor 
  
  **Explicación:**
  - La función `reduce` se usa para combinar todos los elementos de una colección en un solo valor mediante una operación acumulativa.
</details>

2. **¿Qué imprime el siguiente código?**
   ```kotlin
   val numeros = listOf(1, 2, 3, 4, 5)
   val resultado = numeros.reduce { acumulador, valor -> acumulador + valor }
   println(resultado)
   ```  
   A) 15  
   B) 10  
   C) 5  
   D) 1

<details>
  <summary>Respuesta</summary>
  
  A) 15
  
  **Explicación:**
  - El código utiliza `reduce` para sumar todos los elementos de la lista. La suma acumulada es 1 + 2 + 3 + 4 + 5 = 15.
</details>

3. **¿Cómo funciona el siguiente código?**
   ```kotlin
   val numeros = listOf(2, 3, 4)
   val resultado = numeros.reduce { acumulador, valor -> acumulador * valor }
   println(resultado)
   ```  
   A) Suma cada elemento de la lista  
   B) Multiplica acumulativamente cada elemento  
   C) Devuelve siempre el primer valor  
   D) Filtra números mayores de 2

<details>
  <summary>Respuesta</summary>
  
  B) Multiplica acumulativamente cada elemento 
  
  **Explicación:**
  - La función `reduce` multiplica acumulativamente los elementos. El cálculo es 2 * 3 * 4 = 24.
</details>

4. **¿Qué condición necesita cumplir una colección para usar la función `reduce`?**  
   A) La colección debe tener al menos un elemento  
   B) La colección debe estar vacía  
   C) La colección solo debe tener números enteros  
   D) Los elementos deben estar ordenados

<details>
  <summary>Respuesta</summary>
  
  A) La colección debe tener al menos un elemento  
  
  **Explicación:**
  - `reduce` solo puede usarse en colecciones que tienen al menos un elemento. Si se usa en una colección vacía, se produce un error.
</details>

5. **¿Qué devuelve el siguiente código?**
   ```kotlin
   val numeros = listOf(5, 10, 15)
   val resultado = numeros.reduce { acumulador, valor -> acumulador - valor }
   println(resultado)
   ```  
   A) -20  
   B) 0  
   C) 30  
   D) 5

<details>
  <summary>Respuesta</summary>
  
  A) -20
  
  **Explicación:**
  - Aquí, la operación acumulativa es la resta: 5 - 10 = -5, y luego -5 - 15 = -20.
</details>

6. **¿Cuál es el resultado del siguiente código?**
   ```kotlin
   val lista = listOf("a", "b", "c", "d")
   val resultado = lista.reduce { acumulador, valor -> acumulador + valor }
   println(resultado)
   ```  
   A) "abcd"  
   B) "a b c d"  
   C) "a-b-c-d"  
   D) "a"

<details>
  <summary>Respuesta</summary>
  
  A) "abcd"
  
  **Explicación:**
  - La función `reduce` concatena las cadenas de forma acumulativa, resultando en "abcd".
</details>

7. **¿Qué ocurre si llamas a `reduce` en una lista vacía?**  
   A) Devuelve `null`  
   B) Se produce un error  
   C) Devuelve 0  
   D) Devuelve una lista vacía

<details>
  <summary>Respuesta</summary>
  
  B) Se produce un error
  
  **Explicación:**
  - `reduce` no puede utilizarse con listas vacías. Si la lista está vacía, se generará una excepción en tiempo de ejecución. Para manejar listas vacías, es mejor usar `fold`.
</details>

8. **¿Qué hace el siguiente código?**
   ```kotlin
   val palabras = listOf("Kotlin", "es", "genial")
   val resultado = palabras.reduce { acumulador, valor -> "$acumulador $valor" }
   println(resultado)
   ```  
   A) Reemplaza las palabras por comas  
   B) Combina las palabras con un espacio entre ellas  
   C) Elimina las palabras duplicadas  
   D) Ordena las palabras alfabéticamente

<details>
  <summary>Respuesta</summary>
  
  B) Combina las palabras con un espacio entre ellas  
  
  **Explicación:**
  - Este código utiliza `reduce` para concatenar las palabras con un espacio entre cada una, resultando en "Kotlin es genial".
</details>

9. **¿Qué imprime el siguiente código?**
    ```kotlin
    val numeros = listOf(1, 2, 3, 4, 5)
    val resultado = numeros.reduce { acumulador, valor -> acumulador + valor * 2 }
    println(resultado)
    ```  
    A) 30  
    B) 40  
    C) 50  
    D) 60

<details>
  <summary>Respuesta</summary>
  
  B) 40
  
  **Explicación:**
  - En este caso, cada número se multiplica por 2 antes de ser sumado acumulativamente. El cálculo es: 1 + (2 * 2) + (3 * 2) + (4 * 2) + (5 * 2) = 1 + 4 + 6 + 8 + 10 = 40.
</details>


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

### Miniquiz: Uso de `forEach` en Kotlin

1. **¿Qué hace la función `forEach` en Kotlin?**  
   A) Filtra elementos de una colección  
   B) Ejecuta una acción en cada elemento de una colección  
   C) Ordena los elementos de una colección  
   D) Devuelve el primer elemento de una colección

<details>
  <summary>Respuesta</summary>
  
  B) Ejecuta una acción en cada elemento de una colección 
  
  **Explicación:**
  - `forEach` es una función que ejecuta una acción (generalmente un bloque de código o una expresión lambda) para cada elemento en una colección.
</details>

2. **¿Qué imprime el siguiente código?**
   ```kotlin
   val numeros = listOf(1, 2, 3, 4)
   numeros.forEach { println(it) }
   ```  
   A) 1 2 3 4  
   B) 4 3 2 1  
   C) 1  
   D) No imprime nada

<details>
  <summary>Respuesta</summary>
  
  A) 1 2 3 4  
  
  **Explicación:**
  - El método `forEach` recorre cada número de la lista e imprime su valor. En este caso, se imprimen los números 1, 2, 3 y 4 en líneas separadas.
</details>

3. **¿Qué función realiza `forEach` en este código?**
   ```kotlin
   val frutas = listOf("Manzana", "Banana", "Cereza")
   frutas.forEach { fruta -> println("Fruta: $fruta") }
   ```  
   A) Imprime solo la primera fruta  
   B) Imprime la lista completa en una sola línea  
   C) Imprime cada fruta con un prefijo  
   D) Filtra las frutas que contienen la letra "a"
   
<details>
  <summary>Respuesta</summary>
  
  C) Imprime cada fruta con un prefijo  
  
  **Explicación:**
  - El código recorre la lista de frutas e imprime cada una con el prefijo "Fruta:". El resultado es "Fruta: Manzana", "Fruta: Banana" y "Fruta: Cereza" en líneas separadas.
</details>

4. **¿Es posible modificar los elementos de una lista dentro de `forEach`?**  
   A) Sí, siempre que la lista sea mutable  
   B) No, `forEach` no permite modificar los elementos  
   C) Solo si usamos una variable global  
   D) Depende del tamaño de la lista
   
<details>
  <summary>Respuesta</summary>
  
  A) Sí, siempre que la lista sea mutable  
  
  **Explicación:**
  - `forEach` se puede usar para modificar los elementos de una lista, pero solo si la lista es mutable (por ejemplo, `MutableList`). En una lista inmutable (`List`), los elementos no se pueden modificar.
</details>

5. **¿Cuál es la diferencia entre `forEach` y un bucle `for`?**  
   A) `forEach` no puede usarse con listas vacías  
   B) `forEach` es más rápido que `for`  
   C) `forEach` es una función de orden superior, mientras que `for` es una estructura de control  
   D) `forEach` no acepta expresiones lambda
   
<details>
  <summary>Respuesta</summary>
  
  C) `forEach` es una función de orden superior, mientras que `for` es una estructura de control  
  
  **Explicación:**
  - `forEach` es una función de orden superior que acepta una lambda, mientras que `for` es una estructura de control que se utiliza para iterar manualmente sobre una colección.
</details>

6. **¿Qué imprime el siguiente código?**
   ```kotlin
   val numeros = listOf(5, 10, 15)
   numeros.forEach { println(it * 2) }
   ```  
   A) 10 20 30  
   B) 5 10 15  
   C) 2 4 6  
   D) 1 2 3
   
<details>
  <summary>Respuesta</summary>
  
  A) 10 20 30  
  
  **Explicación:**
  - El código multiplica cada número de la lista por 2 antes de imprimirlo. El resultado es 10, 20 y 30 en líneas separadas.
</details>

7. **¿Qué ocurre si usas `forEach` en una lista vacía?**  
   A) Devuelve una lista vacía  
   B) Se produce un error  
   C) No hace nada, ya que no hay elementos  
   D) Siempre devuelve un valor por defecto
   
<details>
  <summary>Respuesta</summary>
  
  C) No hace nada, ya que no hay elementos
  
  **Explicación:**
  - Si la lista está vacía, `forEach` no ejecuta ninguna acción, ya que no hay elementos sobre los cuales iterar.
</details>

8. **¿Qué tipo de función es `forEach` en Kotlin?**  
   A) Función de orden superior  
   B) Función recursiva  
   C) Función lambda  
   D) Función predeterminada
   
<details>
  <summary>Respuesta</summary>
  
  A) Función de orden superior  
  
  **Explicación:**
  - `forEach` es una función de orden superior porque toma una función (en forma de lambda) como argumento y la aplica a cada elemento de la colección.
</details>

9. **¿Qué ocurre si colocas un `return` dentro de un bloque `forEach`?**  
   A) Sale del bucle `forEach` inmediatamente  
   B) Detiene toda la ejecución del programa  
   C) Continúa con el siguiente elemento  
   D) No está permitido usar `return` en `forEach`
   
<details>
  <summary>Respuesta</summary>
  
  A) Sale del bucle `forEach` inmediatamente
  
  **Explicación:**
  - Usar `return` dentro de un bloque `forEach` detendrá la iteración actual y saldrá del bucle inmediatamente.
</details>

10. **¿Qué imprimirá el siguiente código?**
    ```kotlin
    val nombres = listOf("Juan", "Ana", "Pedro")
    nombres.forEach { nombre -> 
        if (nombre.startsWith("A")) println("Nombre que empieza con A: $nombre")
    }
    ```  
    A) "Nombre que empieza con A: Juan"  
    B) "Nombre que empieza con A: Ana"  
    C) "Nombre que empieza con A: Pedro"  
    D) No imprime nada
   
<details>
  <summary>Respuesta</summary>
  
  B) "Nombre que empieza con A: Ana"  
  
  **Explicación:**
  - El código verifica si el nombre comienza con la letra "A". Como "Ana" es el único nombre que cumple esta condición, solo se imprime "Nombre que empieza con A: Ana".
</details>

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

### Miniquiz: Uso de `find` en Kotlin

1. **¿Qué hace la función `find`?**  
   A) Muestra todos los elementos de la lista  
   B) Elimina un elemento de la lista  
   C) Devuelve el primer elemento que cumple una condición  
   D) Ordena la lista  
   
<details>
  <summary>Respuesta</summary>
  
  C) Devuelve el primer elemento que cumple con la condició
  
  **Explicación:**
  - La función `find` busca el primer elemento en la lista que cumpla con la condición proporcionada y lo devuelve. Si no encuentra ningún elemento que cumpla con la condición, devuelve `null`.
</details>

2. **¿Qué imprime el siguiente código?**
   ```kotlin
   val numeros = listOf(2, 4, 6, 8, 10)
   val resultado = numeros.find { it > 5 }
   println(resultado)
   ```  
   A) 2  
   B) 6  
   C) 10  
   D) null  
   
<details>
  <summary>Respuesta</summary>
  
  B) 6
  
  **Explicación:**
  - `find` busca el primer elemento mayor que 5. En este caso, el primer número que cumple con esta condición es `6`, por lo que se imprime ese valor.
</details>

3. **En el siguiente código, ¿cuál es el resultado de `find`?**
   ```kotlin
   val frutas = listOf("Mango", "Manzana", "Banana")
   val resultado = frutas.find { it.startsWith("B") }
   ```  
   A) "Manzana"  
   B) null  
   C) "Banana"  
   D) "Mango"  
   
<details>
  <summary>Respuesta</summary>
  
  C) "Banana"
  
  **Explicación:**
  - La función `find` busca el primer elemento que empiece con "B". En este caso, el primer elemento que cumple con la condición es `"Banana"`.
</details>

4. **Si la lista está vacía, ¿qué devuelve `find`?**  
   A) Lanza un error  
   B) Devuelve `null`  
   C) Devuelve el último elemento  
   D) Devuelve una lista vacía  
   
<details>
  <summary>Respuesta</summary>
  
  B) Devuelve `null`
  
  **Explicación:**
  - Si la lista está vacía, `find` no puede encontrar ningún elemento que cumpla con la condición, por lo que devuelve `null`.
</details>

5. **¿Qué imprime el siguiente código?**
   ```kotlin
   val nombres = listOf("Ana", "Pedro", "Carla")
   val resultado = nombres.find { it.contains("ed") }
   println(resultado)
   ```  
   A) "Pedro"  
   B) null  
   C) "Ana"  
   D) "Carla"  
   
<details>
  <summary>Respuesta</summary>
  
  A) "Pedro"
  
  **Explicación:**
  - `find` busca el primer elemento que contenga "ed". El primer elemento que cumple con esta condición es `"Pedro"`.
</details>

6. **¿Cuál es la diferencia entre `find` y `filter`?**  
   A) `find` devuelve varios resultados y `filter` solo uno  
   B) `find` ordena la lista y `filter` la transforma  
   C) `find` devuelve el primer elemento que coincide con la condición, mientras que `filter` devuelve todos los elementos que cumplen la condición  
   D) `find` solo se aplica a listas de números  
   
<details>
  <summary>Respuesta</summary>
  
  C) `find` devuelve solo el primer elemento que cumple con la condición, mientras que `filter` devuelve todos los elementos que cumplen con la condición
  
  **Explicación:**
  - La diferencia principal es que `find` devuelve un solo elemento (el primero que cumple la condición), mientras que `filter` devuelve una lista con todos los elementos que cumplen la condición.
</details>

7. **¿Qué imprime el siguiente código?**
   ```kotlin
   val edades = listOf(18, 22, 25, 30)
   val resultado = edades.find { it < 20 }
   println(resultado)
   ```  
   A) 18  
   B) 22  
   C) 30  
   D) null  
   
<details>
  <summary>Respuesta</summary>
  
  A) 18
  
  **Explicación:**
  - `find` busca el primer número menor que 20, que en este caso es `18`.
</details>

8. **¿En qué tipo de colección se puede usar la función `find`?**  
   A) Solo en listas  
   B) Solo en conjuntos (sets)  
   C) Tanto en listas como en conjuntos  
   D) Solo en arreglos (arrays)  
   
<details>
  <summary>Respuesta</summary>
  
  C) Se puede usar en listas y conjuntos
  
  **Explicación:**
  - La función `find` se puede utilizar en colecciones como listas y conjuntos en Kotlin.
</details>

9. **¿Qué imprime el siguiente código?**
   ```kotlin
   val numeros = listOf(3, 5, 7, 9)
   val resultado = numeros.find { it % 2 == 0 }
   println(resultado)
   ```  
   A) 3  
   B) 9  
   C) null  
   D) 5  
   
<details>
  <summary>Respuesta</summary>
  
  C) `null`
  
  **Explicación:**
  - `find` busca el primer número par en la lista. Como no hay números pares en esta lista, el resultado es `null`.
</details>

10. **¿Cuál será el resultado de la función `find` en el siguiente código?**
    ```kotlin
    val letras = listOf("A", "B", "C", "D")
    val resultado = letras.find { it == "C" }
    println(resultado)
    ```  
    A) "A"  
    B) "B"  
    C) "C"  
    D) null  
   
<details>
  <summary>Respuesta</summary>
  
  C) "C"
  
  **Explicación:**
  - `find` busca la letra "C" en la lista y, como está presente, la devuelve como resultado.
</details>

## 6. Ejercicios Prácticos

1. Usa la función `filter` para obtener una lista de números pares de una colección.
2. Aplica la función `map` para convertir una lista de cadenas en mayúsculas.
3. Utiliza la función `reduce` para calcular el producto de todos los números de una lista.
