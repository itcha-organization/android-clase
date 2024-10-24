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
