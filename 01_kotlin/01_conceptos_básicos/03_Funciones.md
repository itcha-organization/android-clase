## Funciones en Kotlin
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
