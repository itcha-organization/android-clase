# Introducción de Flutter

Flutter es un software development kit para interfaces de usuario de código abierto creado por Google.<br>
Se usa para desarrollar aplicaciones cross platform desde una sola base de código para web, Android, iOS, Fuchsia, Linux, macOS y Windows.

## Características principales

Estas características hacen de Flutter una opción muy poderosa para el desarrollo de aplicaciones móviles y proyectos que requieran compatibilidad multiplataforma.

### 1. **Desarrollo multiplataforma**
   - Con una sola base de código, es posible crear aplicaciones para iOS, Android, Web, Windows, macOS y Linux, lo que permite desarrollar aplicaciones para múltiples plataformas de manera eficiente.
   - No es necesario realizar desarrollos separados para cada plataforma, lo que reduce el tiempo de mantenimiento y actualización.

### 2. **Alto rendimiento**
   - Flutter se compila en código nativo, lo que minimiza los problemas de rendimiento que suelen tener las herramientas de desarrollo multiplataforma.

### 3. **Hot Reload (Recarga en caliente)**
   - Durante el desarrollo, cualquier cambio en el código se refleja de inmediato en la aplicación sin perder su estado actual. Esto facilita la ajuste de la interfaz de usuario y la depuración de errores.
   - Mejora la productividad del desarrollador y permite iterar rápidamente en el diseño y funcionalidad de la aplicación.

### 4. **Amplia biblioteca de widgets**
   - Flutter es un framework basado en widgets y ofrece una variedad de ellos, desde componentes básicos de interfaz de usuario hasta widgets personalizados avanzados.
   - Soporta de manera nativa widgets de Material Design y estilo iOS, lo que facilita la creación de interfaces adaptadas a cada plataforma.

### 5. **Uso del lenguaje Dart**
   - Flutter utiliza el lenguaje Dart, que es simple y fácil de aprender, con una sintaxis similar a C# o Java, lo que facilita su adopción por desarrolladores con experiencia en estos lenguajes.

## Experimente el widget

Experimenta el widget Fultter con DartPad.
DartPad es un IDE sencillo que te permite ejecutar aplicaciones Dart y Fultter sencillas en tu navegador.

DartPad：https://dartpad.dev/

Abra DartPad en su navegador y ejecute el siguiente código.

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Hello World'),
        ),
        body: Text('Hello, World!'),
      ),
    );
  }
}
```
Este código muestra cómo crear una aplicación simple en Flutter. Tiene una barra de aplicaciones con un título y un cuerpo que muestra el texto "Hello, World!". Es un buen ejemplo para aprender cómo usar los widgets básicos de Flutter en la construcción de la interfaz de usuario.

### Explicación del Código

1. **Importación**
   ```dart
   import 'package:flutter/material.dart';
   ```
   - Se importa el paquete `flutter/material.dart`. Esto permite el uso de los widgets de diseño material de Flutter, que proporcionan los elementos básicos para construir la interfaz de usuario de la aplicación.

2. **Función main**
   ```dart
   void main() {
     runApp(MyApp());
   }
   ```
   - La función `main()` es el punto de entrada de la aplicación Flutter. Esta función es la primera que se llama cuando la aplicación se inicia.
   - `runApp(MyApp())` crea una instancia de la clase `MyApp` y la ejecuta. Esta función indica a Flutter que dibuje el árbol de widgets.

3. **Clase MyApp**
   ```dart
   class MyApp extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return MaterialApp(
         home: Scaffold(
           appBar: AppBar(
             title: Text('Hello World'),
           ),
           body: Text('Hello, World!'),
         ),
       );
     }
   }
   ```
   - La clase `MyApp` extiende `StatelessWidget`, lo que significa que es un widget que no mantiene estado. Esta clase define la estructura de la aplicación.
   - El método `build` define cómo se mostrará este widget. `context` proporciona información sobre la ubicación del widget.

4. **Widget MaterialApp**
   ```dart
   return MaterialApp(
   ```
   - El widget `MaterialApp` proporciona la configuración básica para una aplicación de diseño material, gestionando características como la navegación, el tema y la localización.
   - La propiedad `home` contiene el widget que se muestra en la pantalla de inicio de la aplicación.

5. **Widget Scaffold**
   ```dart
   home: Scaffold(
     appBar: AppBar(
       title: Text('Hello World'),
     ),
     body: Text('Hello, World!'),
   ),
   ```
   - El widget `Scaffold` proporciona la estructura básica para el diseño de la aplicación. Puede incluir elementos como la barra de aplicaciones, el cuerpo, y un botón de acción flotante.
     - El widget `AppBar` crea la barra de título que se muestra en la parte superior de la aplicación. En este caso, `Text('Hello World')` se muestra como el título.
     - La propiedad `body` contiene el widget principal que se mostrará en la aplicación. En este caso, `Text('Hello, World!')` muestra el texto "Hello, World!" en el centro de la pantalla.

## Vamos a definir un Widget personalizado utilizando `StatelessWidget`.

`StatelessWidget` es un tipo de widget en Flutter que se utiliza para crear widgets que no mantienen estado. A continuación se explica el uso básico de `StatelessWidget`.

### Uso Básico

1. **Creación de la Clase**
   Crea una clase que extienda de `StatelessWidget`. Esta clase debe sobreescribir el método `build` para definir la apariencia del widget.

2. **Método build**
   El método `build` se utiliza para definir cómo se mostrará el widget. Este método toma un objeto `BuildContext` como argumento y devuelve un árbol de widgets.

### Práctico: Crear un Widget que muestre `Hello, World!`

```diff
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Hello World'),
        ),
+        body: TextWidget(),
      ),
    );
  }
}

+ class TextWidget extends StatelessWidget {
+  @override
+  Widget build(BuildContext context) {
+    return Text('Hello, World!');
+  }
+ }
```

### Puntos Importantes

- `StatelessWidget` se utiliza para crear widgets que no mantienen estado. Es decir, se utiliza cuando la apariencia o los datos del widget no cambian.
- Para widgets que mantienen estado (que cambian según la interacción del usuario, por ejemplo), se debe usar `StatefulWidget`.
