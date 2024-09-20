# Funciones de Alcance

Como ya viste, Kotlin incluye muchas funciones que hacen que tu código resulte más conciso.
Una de esas funciones que encontrarás a medida que continúes aprendiendo sobre el desarrollo de Android son las funciones de alcance. Las funciones de alcance te permiten acceder de forma concisa a propiedades y métodos de una clase sin tener que acceder varias veces al nombre de la variable.
En esta clase, nos centraremos en dos tipos, `let()` y `apply()`.

## **1. Función `let`**

### **Concepto básico**

`let` es una función de alcance que pasa un objeto como argumento y permite realizar operaciones sobre él. Se utiliza principalmente para:
- **Verificación de no nulidad (`null`)**
- **Eliminar las referencias de objetos repetitivos**

### **Sintaxis:**
```kotlin
objeto.let { it -> 
    // operaciones
}
```
- **`it`**: Se refiere al objeto en sí y se puede acceder a él dentro del bloque `let`.
- **Valor de retorno**: Retorna el resultado de la última expresión dentro del bloque `let`.

### **Ejemplo 1: Uso de `let` para verificar no nulidad**
`let` es muy útil cuando necesitas realizar varias operaciones sobre un objeto solo si este no es nulo.
```kotlin
val email: String? = "usuario@ejemplo.com"

email?.let {
    println("Correo en minúsculas: ${it.lowercase()}")
    println("Dominio: ${it.substringAfter("@")}")
}
```
#### **Explicación:**
- El bloque `let` solo se ejecuta si `email` no es nulo.
- Dentro del bloque, `it` se refiere al valor de `email`.

### **Ejemplo 2: Eliminar las referencias de objetos repetitivos con `let`**
`let` también se usa para eliminar las referencias de objetos repetitivos.
```kotlin
class Persona(val nombre: String, val apellido: String, var edad: Int)

fun main() {
    val persona = Persona("Kyo", "Onuma", 27)
    
    // Refiriéndose a la instancia `persona` tres veces.
    println("Soy ${persona.nombre}")
    println("Me apellido ${persona.apellido}")
    println("Tengo ${persona.edad}")
    
    // Usando la función de alcance "let"
    persona.let {
        println("Soy ${it.nombre}")
        println("Me apellido ${it.apellido}")
        println("Tengo ${it.edad}")        
    }
}
```
#### **Explicación:**
- Aquí, instancia la clase `Persona` y mostra los valores cada propiedad.
- Utilizamos `let` para acceder a la cadena de forma temporal usando `it`.

## **2. Función `apply`**
### **Concepto básico**
`apply` se utiliza principalmente para la **inicialización o configuración de objetos**. Retorna el objeto sobre el que se aplica, por lo que es ideal para inicializaciones en cadena o patrones de tipo builder.

### **Sintaxis:**
```kotlin
objeto.apply {
    // configurar propiedades u operaciones
}
```
- **`this`**: Se refiere al objeto sobre el que se está aplicando `apply` y puede referirse implícitamente dentro del bloque.
- **Valor de retorno**: Devuelve el objeto sobre el cual se llama.

### **Ejemplo 1: Inicialización de objetos**
`apply` es excelente para configurar las propiedades de un objeto.

**Inicialización sin `apply`:**
```kotlin
val persona = Persona()
persona.nombre = "Juan"
persona.edad = 30

println("Nombre: ${persona.nombre}, Edad: ${persona.edad}")  // Salida: Nombre: Juan, Edad: 30
```
**Usando `apply`:**
```kotlin
val persona = Persona().apply {
    nombre = "Juan"
    edad = 30
}
println("Nombre: ${persona.nombre}, Edad: ${persona.edad}")  // Salida: Nombre: Juan, Edad: 30
```
#### **Explicación:**
- Dentro del bloque `apply`, se configuran las propiedades `nombre` y `edad` del objeto `persona`.
- `apply` devuelve el mismo objeto `persona` después de configurarlo.

---

### **Ejemplo 2: Inicialización de objetos anidados**
`apply` también es útil para inicializar objetos que contienen otros objetos.

**Inicialización sin `apply`:**
```kotlin
// Crear una instancia de Motor
val motor = Motor()
motor.tipo = "Híbrido"
motor.potencia = 120

// Asigna la instancia de Motor que acaba de crear a la propiedad Coche
val coche = Coche()
coche.marca = "Toyota"
coche.modelo = "Corolla"
coche.motor = motor

println("Marca: ${coche.marca}, Modelo: ${coche.modelo}, Motor Tipo: ${coche.motor.tipo}, Motor Potencia: ${coche.motor.potencia}")
```
**Usando `apply`:**
```kotlin
val coche = Coche().apply {
    marca = "Toyota"
    modelo = "Corolla"
    motor = Motor().apply {
        tipo = "Híbrido"
        potencia = 120
    }
}
```
#### **Explicación:**
- Aquí, inicializamos el objeto `Coche` y luego usamos `apply` nuevamente para inicializar su propiedad `Motor`.

## 3. Ejercicios
### Ejercicios1:
1. Reescríbe la referencia del objeto `libro` usando la función `let`.
2. Utilice el código inicial en la siguiente URL.
   https://pl.kotl.in/B5o1P5f98

### Ejercicios2:
1. Reescríbe asignación de valores a las propiedades del objeto `persona` usando la función `apply`.
2. Utilice el código inicial en la siguiente URL.
   https://pl.kotl.in/SrXNKSFfW

## **4. Estudiar más.**
Para obtener más conocimiento, pruebe la siguiente documentación oficial y los tutoriales oficiales.

- [Práctica:Clases y colecciones](https://developer.android.com/codelabs/basic-android-kotlin-compose-practice-classes-and-collections?hl=es-419#0)
- [Scope functions](https://kotlinlang.org/docs/scope-functions.html)
