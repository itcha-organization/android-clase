# Uso básico de funciones de orden superior con colecciones
En Kotlin, existen varias funciones de orden superior que permiten manipular colecciones como listas, conjuntos y mapas de manera eficiente. Estas funciones simplifican tareas como filtrar, transformar y agrupar elementos dentro de las colecciones.

A continuación, se explican algunas de las funciones de orden superior más utilizadas para operar con colecciones en Kotlin.

1. ## map: Transformar elementos

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

1. ## filter: Filtrar elementos según una condición
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

1. ## reduce: Acumular los elementos en un solo valor
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

1. ## forEach: Ejecutar una acción en cada elemento
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

1. ## find: Encontrar el primer elemento que cumpla una condición
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

1. ## Ejercicios Prácticos

1. Usa la función `filter` para obtener una lista de números pares de una colección.
2. Aplica la función `map` para convertir una lista de cadenas en mayúsculas.
3. Utiliza la función `reduce` para calcular el producto de todos los números de una lista.
