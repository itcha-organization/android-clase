# Cómo agregar botón a tu app para Android

En este codelab, crearás una app interactiva de Dice Roller que les permite a los usuarios presionar un elemento Button componible para lanzar un dado. El resultado del lanzamiento se muestra con un elemento Image componible en la pantalla.

![image](https://github.com/user-attachments/assets/c7644989-c568-4f6b-ba02-a0fb8d877b52)

Usa Jetpack Compose con Kotlin para compilar el diseño de tu app y, luego, escribe la lógica empresarial para controlar lo que sucede cuando se presiona el elemento Button componible.

## Repaso: Crear un proyecto
Crea un proyecto `Dice Roller` en Android Studio para este tutorial.
1. En Android Studio, haz clic en File > New > New Project.
1. En el diálogo New Project, selecciona Empty Activity y haz clic en Next.
1. En el campo Name, ingresa `Dice Roller`.
1. En el campo Minimum SDK, selecciona un nivel mínimo de API de 24 (Nougat) del menú y, luego, haz clic en Finish.

## La función `Button`

El `Button` toma el parámetro `onClick`, que define la acción a ejecutar cuando el botón es presionado, y dentro de él se coloca el contenido que puede ser un texto o un ícono, por ejemplo.

En la función `onCreate`, sustituye el código del bloque `DiceRollerTheme` por el siguiente código con `Button` y ejecuta la aplicación.
```kotlin
DiceRollerTheme {
    Button(
        // Acción que se ejecuta cuando se hace clic
        onClick = { Log.d("button", "Botón pulsado.") }
    ) {
        Text("Generar un registro") // Texto del botón
    }
}
```
Confirmamos que el registro se emite cuando se pulsa el botón.

Haga clic en el icono del gato para mostrar el panel `Logcat`. Introduzca `button` en la ventana de búsqueda para afinar la búsqueda.

![image](https://github.com/user-attachments/assets/17003884-5690-4c74-806e-dc59213b9e92)

## Creación de la interfaz de usuario de la aplicación

### Repaso: Añadir imágenes al proyecto

1. Abre esta [URL](https://github.com/google-developer-training/basic-android-kotlin-compose-training-dice-roller/raw/main/dice_images.zip) para descargar en tu computadora un archivo ZIP con imágenes de dados y, luego, espera a que se complete la descarga.Busca el archivo en tu computadora. Es probable que se encuentre en la carpeta Descargas.
1. Extrae el archivo ZIP para crear una nueva carpeta dice_images que contenga seis archivos de imagen de dados con valores de dado del 1 al 6.
   <br>`TODO:ダウンロードファイルスクショ`
   <br>`TODO:Zip解凍スクショ`
1. En Android Studio, haz clic en `View` > `Tool Windows` > `Resource Manager`.
1. Haz clic en `+` > `Import Drawables` para abrir un navegador de archivos.
   ![image](https://github.com/user-attachments/assets/f5476015-d011-4ddd-940a-9c53f4a34f07)
1. Busca y selecciona la carpeta de seis imágenes de dados. Luego, súbelas.
   <br>`TODO:フォルダの選択`
1. Haz clic en `Next`
1. Haz clic en `Import` para confirmar que deseas importar las seis imágenes.

### Crear función `DiceWithButtonAndImage`.

Como pudiste ver en la captura de pantalla de la app final, hay una imagen de un dado y un botón para lanzarlo. Asignarás una estructura a las funciones de componibilidad `DiceWithButtonAndImage` para reflejar esta arquitectura.

En primer lugar, defina una función componible para la vista previa `DiceRollerApp` como se muestra en el código siguiente.
Esta función no es sólo de previsualización, sino que se llama en la función final `onCreate`.

De este modo, algunas funciones componibles de una app pueden marcarse con `@Preview`.Esta es una forma de evitar la hinchazón en el código de sólo vista previa.

```kotlin
@Preview(showBackground = true)
@Composable
fun DiceRollerApp() {
    DiceWithButtonAndImage(modifier = Modifier
        .fillMaxSize()
        .wrapContentSize(Alignment.Center)
    )
}
```

Define la función `DiceWithButtonAndImage` como sigue.El argumento de `onClick` se da como un {} vacío ya que se añadirá la a lógica del dado más tarde.

```kotlin
@Composable
fun DiceWithButtonAndImage(modifier: Modifier = Modifier) {
    Column(
        modifier = modifier,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Image(
            painter = painterResource(R.drawable.dice_1),
            contentDescription = null
        )
        Spacer(modifier = Modifier.height(16.dp))
        Button(
            onClick = {
                /* TODO: La lógica del dado */
            }
        ) {
            Text(text = "Roll", fontSize = 24.sp)
        }
    }
}
```
- Coloque cada elemento en un bloque `Column` para disponer la imágen y el botón verticalmente.
- Para centrar los elementos de una columna en la pantalla, pasa `Alignment.CenterHorizontally` como argumento `horizontalAlignment` de `Column`.
- La función `Spacer` es una función componible para establecer espacios entre elementos.En función del valor dado al argumento `modifier`, puede establecer el espacio.

### Repaso: Sustituye las cadenas codificadas por recursos `string`.

1. Seleccione la cadena entre comillas.
![image](https://github.com/user-attachments/assets/8fad9fe7-9a74-4627-8c33-beb9a6c210b8)

1. Pulse las teclas `Alt` y `Enter` para mostrar las opciones.
1. Selecciona `Extract string resource`.

![image](https://github.com/user-attachments/assets/bb70a646-80c4-4718-9d73-295d9121be36)

1. Para `Resource name`, configure `roll` tal cual y pulse `OK`.

![image](https://github.com/user-attachments/assets/8d2281b8-f94e-4b46-b4f5-c6576d4d5999)

1. Asegúrese de que el código se ha cambiado para utilizar un recurso `string` en la función `stringResource`, de la siguiente manera.
    ```kotlin
    Text(text = stringResource(R.string.roll), fontSize = 24.sp)
    ```

## Creación de la interfaz de usuario de la aplicación

## Añadir la a lógica del dado a `onClick`

Modifica el código para que se añada la variable dado y se cambie el valor de la variable al pulsar el botón, como se muestra en el siguiente código.

```diff
@Composable
fun DiceWithButtonAndImage(modifier: Modifier = Modifier) {
    // Variable de la tirada de dado
+    var result = 1
    // Cambia la imagen pasada a `Image` según la tirada de dado
+    val imageResource = when(result) {
+        1 -> R.drawable.dice_1
+        2 -> R.drawable.dice_2
+        3 -> R.drawable.dice_3
+        4 -> R.drawable.dice_4
+        5 -> R.drawable.dice_5
+        else -> R.drawable.dice_6
+    }
    Column(
        modifier = modifier,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Image(
            // Cambia la imagen pasada a `Image` según la tirada de dado
+            painter = painterResource(imageResource),
            contentDescription = null
        )
        Spacer(modifier = Modifier.height(16.dp))
        Button(
            onClick = {
+                result = (1..6).random()
            }
        ) {
            Text(text = stringResource(R.string.roll), fontSize = 24.sp)
        }
    }
}
```
- Añade la variable `result` para guardar la tirada de dados. El valor inicial es 1.
- Asigna diferentes objetos imagen a la variable `imageResource` en función del valor de la variable `result`.
- A la función `Image` se le pasa la variable `imageResource` para poder cambiar la imagen.
- Ver `onClick`. `result = (1..6).random()`, la lógica que asigna aleatoriamente los números del 1 al 6 al `result` se ejecuta cuando se pulsa el botón.

Ejecuta la aplicación y pulsa el botón.
Con el código actual, no ocurre nada al pulsar el botón.

Esto se debe a que la IU de la aplicación no se redibuja.
Ahora mismo, la situación es tal que al pulsar un botón se actualiza el valor de una variable en segundo plano, pero no se refleja en la IU.

Para resolver este problema, es necesario definir `result` como un estado.
Jetpack Compose activa un redibujado de IU cuando se actualiza el valor del estado.

Para definir `result` como un estado, reescríbalo como sigue.
```kotlin
var result by remember { mutableStateOf(1) }
```

La historia se complica considerablemente cuando hablamos de `by`, `remember` y `mutableStateOf` con más detalle.
Por lo tanto, la siguiente sintaxis debe memorizarse como la "sintaxis para definir estados".
```kotlin
var `nombre de la variable` by remember { mutableStateOf(`valor inicial`) }
```

Ahora, vuelve a ejecutar la aplicación y comprueba que la imagen del dado cambia al pulsar el botón.


## プレビューのインタラクティブモード

## デバッガーを利用する
