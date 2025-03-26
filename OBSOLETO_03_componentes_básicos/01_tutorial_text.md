# Cómo utilizar la función componible Text

Creamos una app para Android que muestra un saludo de cumpleaños en formato de texto, que se verá como esta captura de pantalla:

![image](https://github.com/user-attachments/assets/5b9ddbdd-94c3-4423-ae7d-d1e9ce266e2b)

## REPASO: crear un proyecto de Empty Activity

1.En el diálogo Welcome to Android Studio, selecciona la opción New Project.<br>
Si ya tiene un proyecto abierto, seleccione `File` > `New` > `New Project`.

![image](https://github.com/user-attachments/assets/4142660e-4d63-45df-900d-9ec329d6b00a)


2.En el diálogo New Project, selecciona `Empty Activity` y haz clic en Next.

![image](https://github.com/user-attachments/assets/65817ddb-f61e-47cb-a011-8e4407d56eb9)

3.En el campo Name, ingresa `Happy Birthday`, selecciona un nivel de API mínimo de 24 (Nougat) en el campo Minimum SDK y haz clic en Finish.

![image](https://github.com/user-attachments/assets/e8778189-f5ff-4d65-b515-ecbdaf20c6b8)

4.Espera a que Android Studio cree los archivos del proyecto y compílalo.

5.Haz clic en ▶ `Run app`.

![image](https://github.com/user-attachments/assets/1f9861f3-3196-4907-a54b-0d67e7038f5b)

Cuando creaste esta app de Feliz cumpleaños con la plantilla de Empty Activity, Android Studio configuró recursos para una app básica para Android, que incluía un mensaje de `Hello Android!` (¡Hola, Android!) en la pantalla.<br>
En este tutorial, aprenderás cómo llega ese mensaje, cómo cambiar el texto por un saludo de cumpleaños y cómo agregar mensajes adicionales y aplicarles formato.

## ¿Qué es Jetpack Compose?

Jetpack Compose es un kit de herramientas moderno para crear IUs de Android.<br>
Con Compose, puedes compilar tu IU a partir de la definición de un conjunto de funciones, llamadas funciones componibles, que toman datos y describen elementos de la IU.

### Ejemplo de una función componible
La función componible tiene la anotación `@Composable`. Todas estas funciones deben tener esta anotación.<br>
La anotación informa al compilador de Compose que esta función está diseñada para convertir datos en IU.<br>
Te recordamos que un compilador es un programa especial que toma el código que escribiste, lo analiza línea por línea y lo traduce a algo que la computadora puede comprender (lenguaje automático).

Este fragmento de código es un ejemplo de una función componible simple a la que le pasan datos (el parámetro de la función name) y los usa para renderizar un elemento de texto en la pantalla.

```kotlin
@Composable
fun Greeting(name: String) {
    Text(text = "Hello $name!")
}
```

Algunas notas sobre las funciones componibles:

* Jetpack Compose se basa en funciones componibles. Estas funciones te permiten definir la IU de tu app de manera programática describiendo cómo debería verse, en lugar de enfocarse en el proceso de construcción de la IU. Para crear una función de componibilidad, agrega la anotación @Composable al nombre de la función.
* Estas funciones pueden aceptar parámetros, que permiten que la lógica de la app describa o modifique la IU. En este caso, tu elemento de la IU acepta una String para que pueda saludar al usuario por su nombre.

Las funciones componibles son similares a las piezas de un rompecabezas que conectas para formar la estructura visual de tu interfaz de usuario.<br>
Veamos ejemplos de componentes UI, que son funciones componibles estándar del Jetpack Compose.

[Componentes UI (funciones componibles) en Compose](https://developer.android.com/develop/ui/compose/components?hl=es-419)

## Cómo previsualizar funciones componibles.

Android Studio te permite obtener una vista previa de las funciones de componibilidad dentro del IDE, en lugar de instalar la app en un emulador o dispositivo Android.<br>
Puedes obtener una vista previa de la apariencia de tu app en el panel Design de Android Studio.<br>
Esta vez, haga clic en el icono `Split` para ver tanto el código como la vista previa del diseño.

Puede definir qué previsualizar creando una función con la anotación `@Preview` como el siguiente codigo.<br>
En el código inicial se define una función de vista previa llamada `GreetingPreview()`.<br>
Cambie el nombre a `BirthdayCardPreview()` y cambia el argumento "Android" en la función `Greeting()` por su nombre.

```kotlin
@Preview(showBackground = true)
@Composable
fun BirthdayCardPreview() {
    HappyBirthdayTheme {
        Greeting("Kyo")
    }
}
```

> [!NOTE]  
>  El código que agregaste a la función BirthdayCardPreview() con la anotación `@Preview` solo muestra una vista previa en el panel Design de Android Studio. Estos cambios no se reflejan en la app.

## Cómo agregar un nuevo elemento de texto

En este parte, quitarás el saludo de `Hello $name!` y agregarás un saludo de cumpleaños.

### Cómo agregar una nueva función de componibilidad

1.En el archivo `MainActivity.kt`, borra la definición de la función `Greeting()`. Más adelante, agregarás tu propia función para mostrar el saludo.<br>

**Quita el siguiente código:**

```kotlin
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Text(
        text = "Hello $name!",
        modifier = modifier
    )
}
```

2.Borra la llamada a función `Greeting()` junto con sus argumentos de las funciones `onCreate()` y `BirthdayCardPreview()`.

**Tu archivo MainActivity.kt será similar al siguiente:**
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            HappyBirthdayTheme {
                Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                }
            }
        }
    }
}

@Preview(showBackground = true)
@Composable
fun BirthdayCardPreview() {
    HappyBirthdayTheme {
    }
}
```

3.Para simplificar el ejemplo, la función `Scaffold` de la función `onCreate()` se cambia por una función `Surface`. Estas funciones se explicarán con más detalle en la siguiente sección.

**Tu codigo de la función `onCreate()` será similar al siguiente:**
```kotlin
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            HappyBirthdayTheme {
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = MaterialTheme.colorScheme.background
                ) {
                }
            }
        }
    }
```

4.Antes de la función BirthdayCardPreview(), agrega una nueva función llamada GreetingText().<br>
No olvides agregar la anotación @Composable antes de la función, ya que será una función de Compose que describirá un elemento componible Text.

Explico más sobre `Modifier` en las clases posteriores.

```kotlin
@Composable
fun GreetingText(modifier: Modifier = Modifier) {
}
```

5.Agrega un parámetro message de tipo String a la función de componibilidad GreetingText().

```kotlin
@Composable
fun GreetingText(message: String, modifier: Modifier = Modifier) {
}
```

6.En la función GreetingText(), agrega una función componible [Text](https://developer.android.com/develop/ui/compose/text?hl=es-419) que pase el mensaje de texto como un argumento con nombre.

```kotlin
@Composable
fun GreetingText(message: String, modifier: Modifier = Modifier) {
    Text(
        text = message
    )
}
```

Esta función GreetingText() muestra texto en la IU. Para ello, llama a la función de componibilidad Text().

### Cómo obtener una vista previa de la función

1.Llama a la función GreetingText() dentro de la función BirthdayCardPreview().

2.Pasa un argumento de tipo String a la función GreetingText(), un saludo de cumpleaños a tu amigo. Si lo deseas, puedes personalizarlo con su nombre, como `"Happy Birthday Sam!"`.


3.El panel Design, se actualiza automáticamente. Obtén una vista previa de tus cambios.

```kotlin
@Preview(showBackground = true)
@Composable
fun BirthdayCardPreview() {
    HappyBirthdayTheme {
        GreetingText(message = "Happy Birthday Sam!")
    }
}
```

## Cómo cambiar el tamaño de la fuente

Agregaste texto a tu interfaz de usuario, pero aún no parece la app final.<br>
En este parte, aprenderás a cambiar el tamaño del texto y otros atributos que afectan el aspecto del elemento de texto.<br>
También puedes experimentar con diferentes tamaños de fuente.

1.Pase el argumento `fontSize` como segundo argumento a la función `Text()` que acaba de añadir.Establece su valor en `100.sp`.

```kotlin
@Composable
fun GreetingText(message: String, modifier: Modifier = Modifier) {
    Text(
        text = message,
        fontSize = 100.sp
    )
}
```

2.Desplázate hasta la parte superior del archivo y observa las sentencias `import`, donde deberías ver una sentencia `import androidx.compose.ui.unit.sp`, lo que significa que Android Studio agrega el paquete a tu archivo.

![image](https://github.com/user-attachments/assets/c5387ea0-cb2e-4657-b25d-650d753c9332)

> [!NOTE]
> Los `sp`(píxeles escalables) son una unidad de medida para el tamaño de fuente.
> Los elementos de la IU en apps para Android usan dos unidades de medición diferentes: los `dp`(píxeles independientes de la densidad), que usarás más tarde para el diseño, y los `sp`(píxeles escalables).
> De forma predeterminada, la unidad de `sp` tiene el mismo tamaño que la unidad de `dp`, pero cambia según el tamaño de texto que prefiera el usuario en la configuración del teléfono.

3.Observa la vista previa actualizada del tamaño de fuente. El motivo de la superposición del mensaje es que debes especificar la altura de la línea.

![image](https://github.com/user-attachments/assets/673440d1-6637-4c17-b52a-a05f53967a4f)

4.Pase el argumento `lineHeight` como segundo argumento a la función `Text()` de modo que incluya la altura de la línea.

```kotlin
@Composable
fun GreetingText(message: String, modifier: Modifier = Modifier) {
    Text(
        text = message,
        fontSize = 100.sp,
        lineHeight = 116.sp,
    )
}
```

Ahora puedes experimentar con diferentes tamaños de fuente.

## Cómo agregar otro elemento de texto

En las tareas anteriores, agregaste un mensaje de cumpleaños para tu amigo. En esta tarea, firmarás la tarjeta con tu nombre.

1.En el archivo `MainActivity.kt`, pasa a la función `GreetingText()` un parámetro `from` de tipo `String` para tu firma.

```kotlin
fun GreetingText(message: String, from: String, modifier: Modifier = Modifier)
```

2.Después de la función componible `Text` del mensaje de cumpleaños, agrega otro elemento `Text`  que acepte un argumento de `text` establecido en el valor `from`.

```kotlin
@Composable
fun GreetingText(message: String, from: String, modifier: Modifier = Modifier) {
    Text(
        // ...
    )
    Text(
        text = from
    )
}
```

3.Agrega un argumento `fontSize` establecido en un valor de 36.sp.

```kotlin
Text(
    text = from,
    fontSize = 36.sp
)
```

4.En la función `BirthdayCardPreview()`, agrega otro argumento `String` para firmar la tarjeta, como `"From Emma"`.

5.La vista previa está actualizada.

![image](https://github.com/user-attachments/assets/5ec766ea-9528-48c0-bc4a-a5e4cc8668b1)

Una función de componibilidad podría describir varios elementos de la IU. Sin embargo, si no proporcionas un lineamiento para organizarlos, Compose podría ordenarlos de una forma que no te guste. Por ejemplo, el código anterior genera dos elementos de texto que se superponen entre sí porque no hay un lineamiento para organizar los dos elementos componibles.

En tu próxima tarea, aprenderás a organizar estos elementos en una fila y en una columna.

## Cómo organizar los elementos de texto en una fila y columna

### Jerarquía de la IU

La jerarquía de la IU se basa en la contención, es decir, un componente puede contener uno o más componentes. A veces, se usan los términos superior y secundario. El contexto aquí es que los elementos superiores de la IU contienen elementos secundarios de la IU, los cuales, a su vez, pueden contener elementos secundarios de la IU. En esta sección, aprenderás sobre las funciones componibles `Column`, `Row` y `Box`, que pueden actuar como elementos superiores de la IU.

![image](https://github.com/user-attachments/assets/2ec3a8cb-e290-4f42-89ac-963126270dc0)

Los tres elementos de diseño estándar básicos en Compose son las funciones componibles `Column`, `Row` y `Box`.<br>
En el siguiente tutorial, obtendrás más información sobre `Box`.

![image](https://github.com/user-attachments/assets/2e620802-55ff-4731-9d16-7cc53ea9e0f6)

Column, Row y Box son funciones de componibilidad, y toman funciones de componibilidad como argumentos, por lo que puedes colocar elementos dentro de estos componentes de diseño.<br>
Por ejemplo, cada elemento secundario dentro de un elemento `Row` que admite composición se coloca de forma horizontal uno al lado del otro en una fila.

```kotlin
// Don't copy.
Row {
    Text("First Column")
    Text("Second Column")
}
```

![image](https://github.com/user-attachments/assets/4a9f7b3e-6ae4-48cf-9f27-340eb635a1e7)

### Sintaxis de expresión lambda final

Kotlin ofrece una sintaxis especial para pasar funciones como parámetros a funciones cuando el último parámetro es una función.

![image](https://github.com/user-attachments/assets/743a1f0b-60e8-41dc-8ce2-f586f166247e)

Cuando pasas una función como ese parámetro, puedes usar la sintaxis de expresión lambda final. En lugar de colocar la función dentro de los paréntesis, puedes colocarla fuera de los paréntesis y entre llaves. Esta práctica es recomendada y común en Compose, por lo que debes familiarizarte con la apariencia del código.

Por ejemplo, el último parámetro en la función de componibilidad `Row()` es el parámetro `content`, una función que describe los elementos secundarios de la IU.<br>
Supongamos que deseas crear una fila que contenga tres elementos de texto.<br>
Este código funcionaría, pero es muy engorroso usar el parámetro con nombre para la expresión lambda final:

```kotlin
Row(
    content = {
        Text("Some text")
        Text("Some more text")
        Text("Last text")
    }
)
```

Como el parámetro content es el último de la firma de la función y pasas su valor como una expresión lambda, puedes quitar el parámetro content y los paréntesis de la siguiente manera:

```kotlin
Row {
    Text("Some text")
    Text("Some more text")
    Text("Last text")
}
```

### Cómo organizar los elementos de texto en una fila

En esta tarea, organizarás los elementos de texto de tu app en una fila para evitar la superposición.

1.Selecciona los dos elementos componibles Text y teclea Alt y Enter.<br>
Selecciona `Surround with widget` > `Surround with Row`.<br>
Despues aparece el elemento `Row` alrededor de los elementos de `Text`.

![image](https://github.com/user-attachments/assets/314c1c93-b421-40ce-8f1b-f65936c2b73f)

![image](https://github.com/user-attachments/assets/1bfb299d-870c-416c-88c5-724aaa5bb3c1)

**Ahora la función debería verse como este fragmento de código:**

```kotlin
@Composable
fun GreetingText(message: String, from: String, modifier: Modifier = Modifier) {
    Row {
        Text(
            text = message,
            fontSize = 100.sp,
            lineHeight = 116.sp,
        )
        Text(
            text = from,
            fontSize = 36.sp
        )
    }
}
```

2.Observa la vista previa actualizada en el panel Design. Cambia temporalmente el tamaño de la fuente del mensaje de cumpleaños a `30.sp`.

La vista previa se ve mucho mejor ahora que no hay superposición. Sin embargo, esto no es lo que quieres, ya que no hay suficiente espacio para tu firma. En la próxima tarea, organizarás los elementos de texto en una columna para resolver este problema.

### Cómo organizar los elementos de texto en una columna

Modifique la función `GreetingText()` para colocar elementos de texto en columnas.<br>
La vista previa debería verse tal como se muestra en la siguiente captura de pantalla:

![image](https://github.com/user-attachments/assets/a7014881-99cc-4550-9ee7-65018a3deb05)

Ahora que intentaste hacerlo por tu cuenta, no dudes en comparar tu código con el de la solución en este fragmento:

```kotlin
@Composable
fun GreetingText(message: String, from: String, modifier: Modifier = Modifier) {
    Column {
        Text(
            text = message,
            fontSize = 100.sp,
            lineHeight = 116.sp,
        )
        Text(
            text = from,
            fontSize = 36.sp
        )
    }
}
```

Pasa el parámetro modificador al elemento secundario en los elementos componibles.

```kotlin
@Composable
fun GreetingText(message: String, from: String, modifier: Modifier = Modifier) {
    Column(modifier = modifier) {
        Text(
            text = message,
            fontSize = 100.sp,
            lineHeight = 116.sp,
        )
        Text(
            text = from,
            fontSize = 36.sp
        )
    }
}
```

## Cómo agregar un saludo a la app

Una vez que estés conforme con la vista previa, es momento de agregar el elemento componible a tu app en el dispositivo o el emulador.

1.En el archivo `MainActivity.kt`, desplázate hasta la función `onCreate()`.
2.Llama a la función `GreetingText()` desde el bloque `Surface`.
3.Pasa la función `GreetingText()`, tu saludo de cumpleaños y la firma.

**La función onCreate() completa debería verse como este fragmento de código:**

4.Haz clic en ▶ `Run app` para ejecutar tu app. 

![image](https://github.com/user-attachments/assets/f86a1157-003a-4618-b908-951c6bcf94be)

### Cómo centrar el saludo

1.Para alinear el saludo en el centro de la pantalla, agrega un parámetro llamado `verticalArrangement` y configúralo en `Arrangement.Center`.<br>
Obtendrás más información sobre verticalArrangement en un tutorial posterior.

```kotlin
@Composable
fun GreetingText(message: String, from: String, modifier: Modifier = Modifier) {
    Column(
        verticalArrangement = Arrangement.Center,
        modifier = modifier
    ) {
        // ...
    }
}
```

2.Agrega un padding de `8.dp` en la columna. Una práctica recomendada es usar valores de padding en incrementos de `4.dp`.

```kotlin
@Composable
fun GreetingText(message: String, from: String, modifier: Modifier = Modifier) {
    Column(
        verticalArrangement = Arrangement.Center,
        modifier = modifier.padding(8.dp)
    ) {
        // ...
    }
}
```

3.Para embellecer aún más tu app, centra el texto del saludo usando `textAlign`.

```kotlin
Text(
    text = message,
    fontSize = 100.sp,
    lineHeight = 116.sp,
    textAlign = TextAlign.Center
)
```

![image](https://github.com/user-attachments/assets/8b6e518d-4b32-4907-bf09-729d2e85035a)

En la captura de pantalla anterior, solo el saludo está centrado debido al parámetro textAlign. La firma, From Emma, tiene la alineación predeterminada a la izquierda.

4.Agrega padding a la firma y alinea la derecha usando `Alignment.End`.

```kotlin
Text(
    text = from,
    fontSize = 36.sp,
    modifier = Modifier
        .padding(16.dp)
        .align(alignment = Alignment.End)
)
```

![image](https://github.com/user-attachments/assets/01f6279d-c627-464e-b4f8-607f333f644f)

### Padding

Un elemento de la IU se une a su contenido. Para evitar que la contracción sea demasiado marcada, puedes especificar una cantidad de padding a cada lado.

![image](https://github.com/user-attachments/assets/ec38c0ea-6849-4afb-b70e-31db4072c9b4)

El padding se usa como modificador, lo que significa que puedes aplicarlo a cualquier elemento componible.<br>
Para cada lado del elemento componible, el modificador `padding` toma un argumento opcional que define la cantidad de padding.

![image](https://github.com/user-attachments/assets/114db1dc-36fc-43c4-8dca-97f8c3941850)

```kotlin
// Este es un ejemplo.
Modifier.padding(
    start = 16.dp,
    top = 16.dp,
    end = 16.dp,
    bottom = 16.dp
)
```
