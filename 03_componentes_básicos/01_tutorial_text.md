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
