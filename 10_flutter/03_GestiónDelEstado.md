# Gestión del estado con `StatefulWidget`

## 1. Estructura de StatefulWidget

En Flutter, los widgets se dividen en dos categorías: `StatelessWidget` y `StatefulWidget`. Un `StatefulWidget`, como su nombre indica, puede tener "estado". Cada vez que el estado cambia, la interfaz de usuario se actualiza.

Un `StatefulWidget` consta de dos clases:

- **Clase `StatefulWidget`**: No gestiona los cambios de estado, sino que proporciona la estructura del widget.
- **Clase `State`**: Define el estado del widget y gestiona la actualización de la interfaz de usuario cuando el estado cambia. El método `build` de esta clase se ejecuta cada vez que el estado se actualiza.

A continuación se muestra un ejemplo simple de la relación entre `StatefulWidget` y `State`:

```dart
// Definir StatefulWidget
class ContadorWidget extends StatefulWidget {
  // Crear una instancia de la clase State emparejado
  @override
  State<ContadorWidget> createState() => _ContadorWidgetState();
}

// Definir clase de State emparejado
class _ContadorWidgetState extends State<ContadorWidget> {
  // Variables que mantienen el estado
  int _count = 0;

  void _incrementCounter() {
    // El estado se actualiza con el método `setState`.
    setState(() {
      _count++; // Actualizar estado
    });
  }

  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        ElevatedButton(
          onPressed: () {
            _incrementCounter();
          },
          child: const Text("Haz clic para contar"),
        ),
        const SizedBox(height: 16),
        Text("Cantidad de clics: $_count"),
      ],
    );
  }
}
```
- En el ejemplo anterior, el `ContadorWidget` es un `StatefulWidget` y la clase `State` correspondiente, `_ContadorWidgetState`, contiene el estado `_count`.
- El estado `_count` se cambia en el método `setState` y la interfaz de usuario se redibuja cuando se cambia.
- `setState` notifica a Flutter que el estado ha cambiado, lo que provoca que el método `build` se ejecute de nuevo y la UI se actualice.

## 2. Pasos para Implementar un StatefulWidget

1. **Definir el StatefulWidget**
   - Crea una clase que extienda de `StatefulWidget`. Esta clase será responsable de construir el widget.
   - Implementa el método `createState`, que debe devolver una instancia de la clase `State` asociada.

   ```dart
   class MiWidgetStateful extends StatefulWidget {
     @override
     _MiWidgetState createState() => _MiWidgetState();
   }
   ```

2. **Definir el Estado**
   - Crea una clase que extienda de `State<MiWidgetStateful>`. Esta clase manejará el estado y la lógica del widget.
   - Define las variables que representarán el estado.

   ```dart
   class _MiWidgetState extends State<MiWidgetStateful> {
     int contador = 0; // Ejemplo de variable de estado
   }
   ```

3. **Construir el Método build**
   - Implementa el método `build` dentro de la clase de estado. Este método es donde se construye la UI del widget y se actualiza cuando cambia el estado.

   ```dart
   @override
   Widget build(BuildContext context) {
     return Column(
       children: [
         Text('Contador: $contador'),
         ElevatedButton(
           onPressed: () {
             setState(() {
               contador++; // Actualiza el estado
             });
           },
           child: Text('Incrementar'),
         ),
       ],
     );
   }
   ```

## Ejemplos
### **Ejemplo: Crear un campo de texto básico**
Crea un campo de texto simple utilizando `TextField` y muestra en tiempo real el texto que el usuario ingresa en la pantalla.
```dart
class MyTextField extends StatefulWidget {
  @override
  State<MyTextField> createState() => _MyTextFieldState();
}

class _MyTextFieldState extends State<MyTextField> {
  String text = "";

  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        TextField(
          onChanged: (value) {
            setState(() {
              text = value;
            });
          },
          decoration: InputDecoration(
            labelText: 'Introduce aquí',
          ),
        ),
        const SizedBox(height: 16),
        Text('Texto ingresado: $text'),
      ],
    );
  }
}
```

### **Ejemplo: Restablecer el contenido del campo de texto**
Crea un campo de texto y un botón de "Restablecer". Al hacer clic en el botón, el contenido del campo de texto debe quedar vacío.

```dart
class ResetTextField extends StatefulWidget {
  @override
  State<ResetTextField> createState() => _ResetTextFieldState();
}

class _ResetTextFieldState extends State<ResetTextField> {
  String text = "";

  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        TextField(
          controller:
              TextEditingController(text: text), // Pre-fill with initial text
          onChanged: (value) {
            setState(() {
              text = value;
            });
          },
          decoration: InputDecoration(
            labelText: 'Ingresa texto',
          ),
        ),
        const SizedBox(height: 16),
        ElevatedButton(
          onPressed: () {
            setState(() {
              text = "";
            });
          },
          child: const Text('Restablecer'),
        ),
      ],
    );
  }
}
```

### **Ejemplo: Múltiples campos**
Crea dos `OutlinedTextField` donde el usuario pueda ingresar su nombre y edad. Al presionar el botón de "Enviar", debería mostrarse en la pantalla: "[Nombre] tiene [Edad] años".

```dart
class MultipleFieldsExample extends StatefulWidget {
  @override
  _MultipleFieldsExampleState createState() => _MultipleFieldsExampleState();
}

class _MultipleFieldsExampleState extends State<MultipleFieldsExample> {
  String name = '';
  String age = '';
  String result = '';

  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        TextField(
          onChanged: (text) {
            setState(() {
              name = text;
            });
          },
          decoration: InputDecoration(
            labelText: 'Nombre',
          ),
        ),
        SizedBox(height: 16),
        TextField(
          onChanged: (text) {
            setState(() {
              age = text;
            });
          },
          decoration: InputDecoration(
            labelText: 'Edad',
          ),
          keyboardType: TextInputType.number,
        ),
        SizedBox(height: 16),
        ElevatedButton(
          onPressed: () {
            setState(() {
              result = '$name tiene $age años';
            });
          },
          child: Text('Enviar'),
        ),
        SizedBox(height: 16),
        Text(result),
      ],
    );
  }
}
```

## Ejercicios

### Ejercicio 1: Entrada de texto simple y visualización

1. crear un `StatefulWidget` y permitir al usuario introducir texto utilizando `TextField`.
2. definir variables para almacenar el valor introducido en el `TextField` y el valor a mostrar en el `Text`.
3. crear un `ElevatedButton` para reflejar el contenido del TextField en el `Text` cuando se pulse el botón.

![image](https://github.com/user-attachments/assets/e98bd74d-bdec-4a78-a091-f1881cf03d50)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio1 extends StatefulWidget {
     @override
     _Ejercicio1State createState() => _Ejercicio1State();
   }

   class _Ejercicio1State extends State<Ejercicio1> {
     String _textoIngresado = ''; // Guardar el texto introducido en variables.
     String _textoMostrado = ''; // Guardar el texto introducido en variables.

     @override
     Widget build(BuildContext context) {
       return Padding(
         padding: const EdgeInsets.all(16.0),
         child: Column(
           children: [
             TextField(
               onChanged: (texto) {
                 setState(() {
                   _textoIngresado = texto; // Actualizar texto de entrada.
                 });
               },
               decoration: InputDecoration(
                 labelText: 'Ingrese texto',
               ),
             ),
             SizedBox(height: 20),
             ElevatedButton(
               onPressed: () {
                 setState(() {
                   _textoMostrado =
                       _textoIngresado; // Actualizar texto para mostrar.
                 });
               },
               child: Text('Mostrar texto'),
             ),
             const SizedBox(height: 16),
             Text('Texto ingresado: $_textoMostrado'),
           ],
         ),
       );
     }
   }

   ```
</details>
---

### Ejercicio 2: Función de conteo ascendente

1. Crea un StatefulWidget que contenga un ElevatedButton para una aplicación de conteo ascendente.
2. Cada vez que se presione el botón, el contador debe incrementarse en 1 y mostrarse en pantalla.
3. Establece el valor inicial del contador en 0.

![image](https://github.com/user-attachments/assets/79a1d51b-9232-408d-8a83-e020fd9f39b3)


<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio2 extends StatefulWidget {
     @override
     _Ejercicio2State createState() => _Ejercicio2State();
   }

   class _Ejercicio2State extends State<Ejercicio2> {
     int _contador = 0;

     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           Text('Contador: $_contador'),
           SizedBox(height: 20),
           ElevatedButton(
             onPressed: () {
               setState(() {
                 _contador++;
               });
             },
             child: Text('Incrementar'),
           ),
         ],
       );
     }
   }
   ```
</details>
---

### Ejercicio 3: Función de limpieza de texto

1. crear un `StatefulWidget` y permitir al usuario introducir texto utilizando `TextField`.
2. definir variables para almacenar el valor introducido en el `TextField` y el valor a mostrar en el `Text`.
3. crear un `ElevatedButton` para reflejar el contenido del TextField en el `Text` cuando se pulse el botón.
4. Añade otro botón e implementa una función para borrar la cadena mostrada en `Text` cuando se pulse el botón. (La cadena en el `TextField` no tiene que ser borrada).

![image](https://github.com/user-attachments/assets/bdc9d931-e080-4a18-bdd8-f358b41f72eb)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio3 extends StatefulWidget {
     @override
     _Ejercicio3State createState() => _Ejercicio3State();
   }

   class _Ejercicio3State extends State<Ejercicio3> {
     String _textoIngresado = '';
     String _textoMostrado = '';

     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           TextField(
             onChanged: (texto) {
               setState(() {
                 _textoIngresado = texto;
               });
             },
             decoration: InputDecoration(
               labelText: 'Ingrese texto',
             ),
           ),
           SizedBox(height: 16),
           Text('Texto ingresado: $_textoMostrado'),
           SizedBox(height: 20),
           ElevatedButton(
             onPressed: () {
               setState(() {
                 _textoMostrado = _textoIngresado;
               });
             },
             child: Text('Mostrar texto'),
           ),
           SizedBox(height: 20),
           ElevatedButton(
             onPressed: () {
               setState(() {
                 _textoMostrado = '';
               });
             },
             child: Text('Limpiar texto mostrado'),
           ),
         ],
       );
     }
   }
   ```
</details>
---

### Ejercicio 4: Múltiples entradas y visualización

1. Crea un StatefulWidget que contenga dos TextField (por ejemplo, uno para nombre y otro para correo electrónico).
2. crear un `ElevatedButton` y mostrar el contenido de ambos campos de texto en un `Text` situado debajo del botón cuando éste se pulse.
3. La visualización debe tener el formato: "Nombre: [nombre], Correo: [correo electrónico]".

![image](https://github.com/user-attachments/assets/717aaa2e-7313-47b9-ab62-49b2dce31bfa)


<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio4 extends StatefulWidget {
     @override
     _Ejercicio4State createState() => _Ejercicio4State();
   }

   class _Ejercicio4State extends State<Ejercicio4> {
     String _nombre = '';
     String _correo = '';
     String _result = '';

     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           TextField(
             onChanged: (texto) {
               setState(() {
                 _nombre = texto;
               });
             },
             decoration: InputDecoration(
               labelText: 'Ingrese su nombre',
             ),
           ),
           TextField(
             onChanged: (texto) {
               setState(() {
                 _correo = texto;
               });
             },
             decoration: InputDecoration(
               labelText: 'Ingrese su correo',
             ),
           ),
           SizedBox(height: 20),
           ElevatedButton(
             onPressed: () {
               setState(() {
                 _result = 'Nombre: $_nombre, Correo: $_correo';
               });
             },
             child: Text('Mostrar información'),
           ),
           SizedBox(height: 16),
           Text(_result),
         ],
       );
     }
   }
   ```
</details>
