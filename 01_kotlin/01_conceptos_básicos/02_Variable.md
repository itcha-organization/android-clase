## Variable
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
