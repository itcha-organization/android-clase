# Conceptos básicos de Kotlin

1. ## Introducción
   ¿Sabes qué es Kotlin? Descúbrelo y habla de Kotlin con los demás.
   1. ### Características y ventajas de Kotlin
      1. **Un lenguaje de programación moderno y fácil de usar:**
         <br>
         Kotlin es un lenguaje de programación moderno con una sintaxis concisa y fácil de entender. Esto te permite crear rápidamente programas que realmente funcionan sin tener que escribir código complejo. Puedes ver resultados inmediatos a medida que aprendes, haciendo que el aprendizaje sea divertido.
      1. **El lenguaje oficial de desarrollo de Android:**
         <br>
         Kotlin ha sido adoptado por Google como el lenguaje oficial para el desarrollo de aplicaciones Android, por lo que al aprender Kotlin, los estudiantes pueden adquirir habilidades directamente relacionadas con el desarrollo real de aplicaciones.
      1. **Un lenguaje popular y útil para tu carrera profesional:**
         <br>
         Kotlin crece en popularidad año tras año y está especialmente demandado en el sector del desarrollo de aplicaciones móviles. Las empresas también buscan ingenieros con conocimientos de Kotlin, lo que supone un gran activo en tu futura carrera profesional.
      1. **Buena comunidad y soporte:**
         <br>
         Kotlin tiene una comunidad activa y hay muchos recursos y soporte disponibles en caso de que tengas alguna pregunta o problema. Si tienes algún problema mientras aprendes, es fácil encontrar una solución y tu aprendizaje irá sobre ruedas, haciendo menos probable que te quedes atrás.

   1. ### Comparamos la sintaxis de Kotlin y C#
      La sintaxis de Kotlin y C# es más o menos similar.Aquí hay algunos ejemplos para algunas de las sintaxis.
      1. **Variables (Variables)**
         - **Kotlin** usa `val` para variables inmutables y `var` para variables mutables.
         - **C#** usa `var` para declarar variables con inferencia de tipos, pero las variables pueden ser reasignadas.
         #### Kotlin
         ```kotlin
         val nombre: String = "Juan"  // Inmutable
         var edad: Int = 25           // Mutable
         ```
         #### C#
         ```csharp
         var nombre = "Juan";  // Inferencia de tipos, pero puede cambiarse
         var edad = 25;        // Mutable
         ```
      
      1. **Funciones (Funciones)**
         - Ambas lenguas definen funciones de manera similar, pero la sintaxis varía.
         #### Kotlin
         ```kotlin
         fun saludar(nombre: String): String {
             return "Hola, $nombre"
         }
         ```
         #### C#
         ```csharp
         string Saludar(string nombre) {
             return $"Hola, {nombre}";
         }
         ```
      
      1. **Clases (Clases)**
         Ambos lenguajes usan una sintaxis similar para definir clases, aunque con ligeras diferencias.
         #### Kotlin
         ```kotlin
         class Persona(val nombre: String, var edad: Int)
         ```
         #### C#
         ```csharp
         class Persona {
             public string Nombre { get; }
             public int Edad { get; set; }
         
             public Persona(string nombre, int edad) {
                 Nombre = nombre;
                 Edad = edad;
             }
         }
         ```
      
      1. **Herencia de clases (Herencia)**
         Ambos lenguajes permiten herencia, pero Kotlin usa `open` para permitir que una clase sea heredada.
         #### Kotlin
         ```kotlin
         open class Animal
         class Perro: Animal()
         ```
         #### C#
         ```csharp
         class Animal {}
         class Perro : Animal {}
         ```
      
      1. **Null Safety (Seguridad ante null)**
         - **Kotlin** tiene un sistema de seguridad para `null` que obliga a manejar posibles valores `null` explícitamente.
         - **C#** también ofrece tipos anulables (`nullable`) usando `?` en los tipos.
         #### Kotlin
         ```kotlin
         val nombre: String? = null  // Tipo nullable
         ```
         #### C#
         ```csharp
         string? nombre = null;  // Tipo nullable
         ```
      
      1. **Bucles for (Bucles)**
         Los bucles `for` son muy parecidos en ambos lenguajes.
         #### Kotlin
         ```kotlin
         for (i in 1..10) {
             println(i)
         }
         ```
         #### C#
         ```csharp
         for (int i = 1; i <= 10; i++) {
             Console.WriteLine(i);
         }
         ```
   - Referencia
     - 初めての Kotlin プログラムhttps://developer.android.com/codelabs/basic-android-kotlin-compose-first-program?hl=ja&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-1%3Fhl%3Dja%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-first-program#0

1. ## Variable
   1. ### Declaración de variable
      Para definir una nueva variable, comienza con la palabra clave `val` o `var` de Kotlin.
      - Palabra clave val: Úsala cuando esperes que el valor de la variable no cambie.
      - Palabra clave var: Úsala cuando esperes que el valor de la variable pueda cambiar.

      Código de ejemplo:
      ```kolin
      val nombre: String = "Juan"  // Inmutable
      var edad: Int = 25           // Mutable
      ```

      Sintaxis:

      ![image](https://github.com/user-attachments/assets/3287d540-ef9c-471a-92bf-835fcaad40e8)

   1. ### Los tipos de datos (`Int`, `String`, `Boolean`, etc.)
      Los tipos de datos básicos en Kotlin se muestran en la siguiente tabla.

      ![image](https://github.com/user-attachments/assets/2605e4c1-4a5a-40e4-b65f-34ea95a43647)

      - **Plantillas de strings:**
        <br>
        En Kotlin, las plantillas de strings permiten incrustar variables o expresiones directamente dentro de una cadena de texto utilizando el símbolo `$`. Si la expresión es más compleja, se encierra entre llaves `{}`.
        <br>
         ```kotlin
         val nombre: String = "Juan"  // Inmutable
         var edad: Int = 25           // Mutable
         
         // $nombre inserta el valor de la variable nombre en la cadena.
         // $edad inserta el valor de la variable edad en la cadena.
         println("$nombre tiene $edad años.")
         
         // ${edad + 1} evalúa la expresión antes de insertarla.
         println("El año que viene $nombre cumplirá ${edad + 1} años.")
         ```
      - **Inferencia de tipo:**
        <br>
        La inferencia de tipo es cuando el compilador de Kotlin puede inferir (o determinar) qué tipo de datos debe ser una variable, sin que el tipo se escriba de manera explícita en el código. Eso significa que puedes omitir el tipo de datos en una declaración de variable si proporcionas un valor inicial para ella.
     
        Pruebe a omitir el tipo de datos en el código de ejemplo para comprobar que no se produce ningún error.
        ```kotlin
         val nombre = "Juan"  // String
         var edad = 25           // Int
        ```
   1. ### Convención de codificación
      Algunas convenciones de codificación recomendadas por Google.

      - Los nombres de las variables deben seguir la convención de mayúsculas y minúsculas, y comenzar con una letra minúscula.
      - En una declaración de variable, debes especificar un espacio después de los dos puntos cuando se especifica el tipo de datos.
  
        ![image](https://github.com/user-attachments/assets/16f6db52-a936-4ee4-94fa-a615949d9ace)

      - Debe haber un espacio antes y después de un operador como la asignación (=), la suma (+), la resta (-), la multiplicación (*) la división (/) y muchos más.
     
        ![image](https://github.com/user-attachments/assets/c9a816c4-eb0a-4bf0-9fad-f0db4efd306b)
      
   1. ### Ejercicio: definir algunas variables y constantes y realizar operaciones

   - リファレンス：
     - Kotlin で変数を作成して使用するhttps://developer.android.com/codelabs/basic-android-kotlin-compose-variables?hl=ja&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-1%3Fhl%3Dja%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-variables#0

1. ## Funciones en Kotlin
   1. ### Cómo definir una función y cómo llamarla
      Para definir una función, comienza con la palabra clave `fun` en Kotlin.
      
      Sintaxis:

      ![image](https://github.com/user-attachments/assets/0b881cbe-3625-409e-872b-60f99a55f4b4)

      Ejecute el siguiente código de ejemplo para ver cómo se definen y llaman las funciones.

      ```kotlin
      fun main() {
          // Llamada a la funcion
          println(saludoCumpleaños("Juan", 25))
      }
      
      // Definición de la función
      fun saludoCumpleaños(nombre: String, edad: Int): String {
          val saludoNombre = "¡Feliz cumpleaños, $nombre!"
          val saludoEdad = "¡Ahora tienes $edad años!"
          return "$saludoNombre\n$saludoEdad"
      }
      ```

      - **El tipo Unit:**
        <br>
        De forma predeterminada, si no se especifica un tipo de datos que se muestra, el predeterminado es `Unit. `Unit` significa que la función no muestra ningún valor. `Unit` es equivalente a el tipo `void` en Java y C#.

        Ejemplo de código para funciones que no devuelven ningún valor:
         ```kotlin
         fun birthdayGreeting(): Unit { // El tipo de retorno es Unit
             println("Happy Birthday, Rover!")
             println("You are now 5 years old!")
         }
         ```

   1. ### Argumentos con nombre
      En Kotlin, puedes llamar a una función con muchos parámetros o pasar los argumentos en un orden diferente; por ejemplo, colocar el parámetro age antes del parámetro name. Cuando incluyes un nombre de parámetro si llamas a una función, esta se denomina argumento con nombre.

      ```kotlin
      fun main() {
          // El orden en que se pasan los parámetros es diferente,
          // pero el resultado es el mismo.
          println(saludoCumpleaños(nombre = "Juan", edad = 25))
          println(saludoCumpleaños(edad = 25, nombre = "Juan"))
      }
      
      fun saludoCumpleaños(nombre: String, edad: Int): String {
          val saludoNombre = "¡Feliz cumpleaños, $nombre!"
          val saludoEdad = "¡Ahora tienes $edad años!"
          return "$saludoNombre\n$saludoEdad"
      } 
      ```
   1. ### Argumentos predeterminados
      Los parámetros de la función también pueden especificar argumentos predeterminados.Cuando llamas a una función, puedes decidir omitir los argumentos para los que haya un valor predeterminado, en cuyo caso se usa el predeterminado.

      Para agregar un argumento predeterminado, agrega un operador de asignación (=) después del tipo de datos para el parámetro y configúralo del mismo modo que a un valor.
  
      ```kotlin
      fun main() {
          // Si se llama a la función sin argumentos, se aplican los valores por defecto
          println(saludoCumpleaños())
      }
      
      // Los valores por defecto se asignan en la definición del parámetro.
      fun saludoCumpleaños(nombre: String = "Juan", edad: Int = 25): String {
          val saludoNombre = "¡Feliz cumpleaños, $nombre!"
          val saludoEdad = "¡Ahora tienes $edad años!"
          return "$saludoNombre\n$saludoEdad"
      }
      ```
   1. ### Ejercicio: crear programas de cálculo básico utilizando funciones


   - リファレンス：
     - Kotlin で関数を作成して使用するhttps://developer.android.com/codelabs/basic-android-kotlin-compose-functions?hl=ja&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-1%3Fhl%3Dja%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-functions#0

1. ## Condiciones y bucles
   1. ### Cómo usar sentencias if/else para expresar condiciones
      En Kotlin, las sentencias `if/else` funcionan de manera similar a otros lenguajes. A continuación te muestro cómo se usan las sentencias `if/else` en diferentes contextos.
      1. **Uso básico de `if/else`**
         <br>
         Este es el uso más común para verificar una condición:
         ```kotlin
         val numero = 10
         
         if (numero > 5) {
             println("El número es mayor que 5")
         } else {
             println("El número es menor o igual a 5")
         }
         ```
      
      1. **Anidación de `if/else`**
         <br>
         Puedes anidar múltiples condiciones `if/else` para manejar más casos:
         ```kotlin
         val numero = 10
         
         val mensaje = if (numero > 10) {
             "El número es mayor que 10"
         } else if (numero == 10) {
             "El número es igual a 10"
         } else {
             "El número es menor que 10"
         }
         
         println(mensaje)  // Salida: El número es igual a 10
         ```
         
      1. **Condiciones más complejas**
         <br>
         Puedes combinar varias condiciones en un `if` utilizando operadores lógicos como `&&` (y) y `||` (o):
         ```kotlin
         val numero = 10
         
         if (numero > 5 && numero < 15) {
             println("El número está entre 5 y 15")
         }
         ```
         ```kotlin
         val edad = 20
         
         if (edad < 18 || edad > 65) {
             println("Eres menor de 18 o mayor de 65 años.")
         } else {
             println("Tienes entre 18 y 65 años.")
         }
         ```
   1. Cómo usar una sentencia when para varias ramas
   1. Cómo usar if/else y when como expresiones
   1. Cómo utilizar los bucles
      https://www.sejuku.net/blog/100855
   1. 演習

1. オプション（時間余ったら）
   - 【公式】練習問題https://developer.android.com/codelabs/basic-android-kotlin-compose-intro-kotlin-practice-problems?hl=ja&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-1%3Fhl%3Dja%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-intro-kotlin-practice-problems#0

#### 語彙
- エントリーポイント
- 
