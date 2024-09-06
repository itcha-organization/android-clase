# Cómo agregar imágenes a tu app para Android

1. ## Cómo agregar una imagen a tu proyecto
   Siga las instrucciones de la siguiente URL para añadir imágenes.

   https://developer.android.com/codelabs/basic-android-kotlin-compose-add-images?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-3%3Fhl%3Dja&hl=es-419#1

1. ## Recursos en Jetpack Compose
   Los recursos son los archivos adicionales y el contenido estático que usa tu código, como mapas de bits, strings de interfaz de usuario, instrucciones de animación, etc.
   
   Siempre debes separar los recursos para apps, como imágenes y strings, de tu código para que puedas mantenerlos de forma independiente. En tiempo de ejecución, Android utiliza el recurso adecuado según la configuración actual. Por ejemplo, puedes proporcionar un diseño de interfaz de la IU diferente según el tamaño de la pantalla o strings diferentes según la configuración de idioma.
   
   Siempre debes colocar cada tipo de recurso en un subdirectorio específico del directorio res/ de tu proyecto.
   
   Normalmente el directorio res/ contiene todos los recursos de los subdirectorios, que incluyen un directorio drawable/ para un recurso de imagen, un directorio mipmap/ para los íconos de selector y un directorio values/ para recursos de strings.
   ```
   MyProject/
       src/
           MyActivity.kt
       res/
           drawable/
               graphic.png
           mipmap/
               icon.png
           values/
               strings.xml
   ```
   
   Jetpack Compose puede acceder a los recursos definidos en tu proyecto de Android. Se puede acceder a los recursos con los ID de recursos que se generan en la clase R de tu proyecto.
   
   Una clase R es una clase que Android genera automáticamente y que contiene los ID de todos los recursos en el proyecto. En la mayoría de los casos, el ID del recurso es el mismo que el nombre del archivo.
   
1. ## Visualice imágenes utilizando el componente Image.
     Añade la función `ImagePreview` como el siguiente código para previsualizar y probar el componente `Image`.
     ```kotlin
     @Preview(showBackground = true)
     @Composable
     fun ImagePreview() {
         Image(
             painter = painterResource(id = R.drawable.androidparty),
             contentDescription = null
         )
     }
     ```

     El primer parámetro de `Image` es un objeto imagen.
     La función `painterResource` recupera el objeto imagen correspondiente al ID de recurso del parámetro.
     El segundo argumento de `Image` es una cadena para la guía de voz. La guía de audio está fuera del alcance de la clase, así que pasa `null`.
     

1. ## Utilice Box para mostrar elementos unos encima de otros.
   El diseño Box es uno de los elementos de diseño estándar en Compose. Usa el diseño Box para apilar elementos uno sobre el otro. El diseño Box también te permite configurar la alineación específica de los elementos que contiene.
  
  ![image](https://github.com/user-attachments/assets/ff07a5a7-6fe1-4992-860a-7018a0c61486)

  Añade una función `GreetingImage` bajo la función `GreetingText`.
  Dentro de un bloque de `Box`, se definen una `Image` y un `GreetingText` para superponer la imagen y el texto.
  El código es el siguiente. También debe corregirse la llamada a la función `GreetingImage`.
   ```kotlin
   @Composable
   fun GreetingImage(message: String, from: String, modifier: Modifier = Modifier) {
       val image = painterResource(R.drawable.androidparty)
       Box(modifier) {
           Image(
               painter = image,
               contentDescription = null
           )
           GreetingText(
               message = message,
               from = from,
               modifier = Modifier
                   .fillMaxSize()
                   .padding(8.dp)
           )
       }
   }
   ```
   ```kotlin
   @Preview(showBackground = true)
   @Composable
   fun BirthdayCardPreview() {
       HappyBirthdayTheme {
           GreetingImage(
               message = "Happy Birthday Sam!",
               from = "From Emma"
           )
       }
   }
   ```
   ```kotlin
   setContent {
       HappyBirthdayTheme {
           // A surface container using the 'background' color from the theme
           Surface(
               modifier = Modifier.fillMaxSize(),
               color = MaterialTheme.colorScheme.background
           ) {
               GreetingImage(
                   message = "Happy Birthday Sam!",
                   from = "From Emma"
               )
           }
       }
   }
   ```

1. ## Añade parámetros a Image para mejorar su aspecto.
   * Ajuste el tamaño del contenido usando el parametro `contentScale`.
     ```diff
     Image(
         painter = image,
         contentDescription = null,
     +    contentScale = ContentScale.Crop
     )
     ```
   * Cambie la opacidad  usando el parametro `alpha`.
     ```diff
     Image(
         painter = image,
         contentDescription = null,
         contentScale = ContentScale.Crop,
     +    alpha = 0.5F
     )
     ```
1. ## Ajuste de la alineación de elementos en Column y Row
   puedes agregar modificadores a los diseños para posicionar los elementos secundarios mediante propiedades de disposición y alineación.

   Para establecer la posición de los elementos secundarios dentro de un Row, configura los argumentos horizontalArrangement y verticalAlignment. Para una Column, configura los argumentos verticalArrangement y horizontalAlignment.

   La propiedad de las disposiciones se usa para organizar los elementos secundarios cuando el tamaño del diseño es mayor que la suma de sus elementos secundarios.

   Por ejemplo: cuando el tamaño de Column es mayor que la suma de sus tamaños secundarios, se puede especificar un verticalArrangement para definir el posicionamiento de la elementos secundarios dentro de Column. A continuación, se muestra una ilustración de diferentes disposiciones verticales:

   ![image](https://github.com/user-attachments/assets/665d1302-0f6a-4484-a6d8-a95b2d88b76d)
   
   De la misma manera, cuando el tamaño de Row es mayor que la suma de sus tamaños secundarios, se puede especificar un horizontalArrangement para definir el posicionamiento de la elementos secundarios dentro de Row. A continuación, se muestra una ilustración de diferentes disposiciones horizontales:
   
   ![image](https://github.com/user-attachments/assets/37f928d1-29ce-416f-9a79-cd235da277d2)


1. ## Sustituye las cadenas codificadas por recursos `string`.
   En el panel `Project`, abre el archivo strings.xml de la ruta `app > res > values > strings.xml`
   
   Siga las instrucciones de la siguiente URL para sustituir las cadenas codificadas por recursos `string`
   
   https://developer.android.com/codelabs/basic-android-kotlin-compose-add-images?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-3%3Fhl%3Dja&hl=es-419#6
   

1. ## minicuestionario:Text de la firma Composables alineados y centrados en la pantalla
   ¡Bien hecho! Agregaste la imagen a la app. Este es un desafío para ti:
   * Ordena o alinea el texto componible de la firma de modo que se alinee al centro de la pantalla.
   
   La visualización en la aplicación es la siguiente.

   ![image](https://github.com/user-attachments/assets/21249f76-78ac-4551-97d2-8cc91dbd14ed)


1. リファレンス
   https://developer.android.com/codelabs/basic-android-kotlin-compose-add-images?hl=ja&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-3%3Fhl%3Dja%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-add-images#0
