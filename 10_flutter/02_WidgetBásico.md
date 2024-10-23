# WidgetBásico

### 1. Text
El widget `Text` se usa para mostrar texto en la pantalla.

**Uso básico:**
```dart
Text(
  '¡Hola, Flutter!',
  style: TextStyle(fontSize: 24, color: Colors.blue),
)
```
- El parámetro `style` se utiliza para especificar el tamaño de la fuente, el color, el estilo de la fuente, entre otros.

**Propiedades principales:**
- `textAlign`: Especifica la alineación del texto (por ejemplo, `TextAlign.center`).
- `overflow`: Define cómo manejar el texto cuando no cabe en el espacio disponible.

### 2. SizedBox
El widget `SizedBox` crea un espacio con un ancho y alto específicos.

**Uso básico:**
```dart
SizedBox(
  width: 20,
  height: 50,
)
```
- En este ejemplo, se crea un espacio de 20 píxeles de ancho y 50 píxeles de alto.

**Usos comunes:**
- Para añadir espacio entre widgets.
- Para cambiar el tamaño de un widget de forma explícita.

**Ejemplo: Cambiar el tamaño de un widget de forma explícita**
```dart
class SizeBoxWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SizedBox(
      width: 100,
      height: 20,
      child: Text(
        '¡Hola, Flutter!',
        style: TextStyle(fontSize: 24, color: Colors.blue),
      ),
    );
  }
}
```

### 3. Column
El widget `Column` organiza widgets secundarios en una columna (de forma vertical).

**Uso básico:**
```dart
class ColumnEjemplo extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      children: <Widget>[
        Text('Este es el primer texto'),
        Text('Este es el segundo texto'),
        Text('Este es el tercer texto'),
      ],
    );
  }
}
```
- El parámetro `children` recibe una lista de widgets que se organizan en vertical.

**Propiedades principales:**
- `mainAxisAlignment`: Especifica la alineación de los widgets secundarios en el eje principal (vertical).
- `crossAxisAlignment`: Especifica la alineación en el eje cruzado (horizontal).

**Maximizar el espacio para los elementos hijos:**
```dart
class ColumnEjemplo2 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      children: <Widget>[
        // Maximizar el espacio en la dirección del eje principal(vertical).
        Expanded(
          child: Container(
            decoration: const BoxDecoration(
              color: Colors.blue,
            ),
            child: Text('Este es el primer texto'),
          )
        ),
        // Maximizar el espacio en la dirección del eje cruzado (horizontal).
        SizedBox(
          width: double.infinity,
          child: Container(
            decoration: const BoxDecoration(
              color: Colors.blue,
            ),
            child: Text('Este es el segundo texto'),

          )
        ),
        Text('Este es el tercer texto'),
      ],
    );
  }
}
```


### 4. Row
El widget `Row` organiza widgets secundarios en una fila (de forma horizontal).

**Uso básico:**
```dart
class RowEjemplo extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Row(
      children: <Widget>[
        Text('Izquierda'),
        SizedBox(width: 10), // Espacio entre los textos
        Text('Derecha'),
      ],
    );
  }
}
```
- Similar a `Column`, el parámetro `children` recibe una lista de widgets que se organizan horizontalmente.

**Propiedades principales:**
- `mainAxisAlignment`: Alineación de los widgets en el eje principal (horizontal).
- `crossAxisAlignment`: Alineación en el eje cruzado (vertical).

**Maximizar el espacio para los elementos hijos:**
```dart
class RowEjemplo2 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Row(
      children: <Widget>[
        Expanded(
          child: Container(
            decoration: const BoxDecoration(
              color: Colors.blue,
            ),
            child: Text('Este es el primer texto'),
          )
        ),
        SizedBox(
          height: double.infinity,
          child: Container(
            decoration: const BoxDecoration(
              color: Colors.blue,
            ),
            child: Text('Este es el segundo texto'),

          )
        ),
        Text('Este es el tercer texto'),
      ],
    );
  }
}
```

### 5. Padding
El widget `Padding` se usa para añadir espacio alrededor de un widget.

**Uso básico:**
```dart
Padding(
  padding: const EdgeInsets.all(8.0),
  child: Text('Texto con espacio añadido'),
)
```
- El parámetro `padding` especifica el espacio en cada dirección (arriba, abajo, izquierda, derecha).
- `EdgeInsets.all` añade el mismo espacio en todas las direcciones, mientras que `EdgeInsets.only` permite especificar espacio en direcciones particulares.

**Ejemplo:**
```dart
class PaddingEjemplo extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      children: <Widget>[
        Text('Este es el primer texto'),
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: Text('Texto con espacio añadido'),
        ),
        Text('Este es el tercer texto'),
      ],
    );
  }
}
```

### Resumen
Estos widgets básicos son esenciales para construir la interfaz de usuario en Flutter. A continuación, un ejemplo que muestra cómo combinar estos widgets para crear una disposición sencilla:

```dart
class ResumenEjemplo extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: Text(
            'Ejemplo de Layout en Flutter',
            style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
          ),
        ),
        Row(
          mainAxisAlignment: MainAxisAlignment.spaceBetween,
          children: [
            Text('Texto a la izquierda'),
            Text('Texto a la derecha'),
          ],
        ),
        SizedBox(height: 20), // Espacio entre los widgets
        Text('Aquí continúa otro contenido...'),
      ],
    );
  }
}
```
## Ejercicios

1. **Ejercicio 1**
   - Coloca 3 widgets de `Text` dentro de un `Column`.
   - Agrega un `SizedBox` entre cada `Text` para crear un espacio uniforme.

![image](https://github.com/user-attachments/assets/37c10d27-ef64-4b41-a60e-5fb420dce867)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio1Widget extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           Text('Texto 1'),
           SizedBox(height: 20), // Añade espacio
           Text('Texto 2'),
           SizedBox(height: 20), // Añade espacio
           Text('Texto 3'),
         ],
       );
     }
   }
   ```
</details>

2. **Ejercicio 2**
   - Coloca 2 widgets de `Text` dentro de un `Row`.
   - Agrega `Padding` al primer widget de `Text` para ajustar el espacio de 24 píxeles.

![image](https://github.com/user-attachments/assets/3d1db61f-51d4-457b-a318-7d9a13d8a771)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio2Widget extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Row(
         children: [
           Padding(
             padding: EdgeInsets.all(24.0),
             child: Text('Texto 1'),
           ),
           Text('Texto 2'),
         ],
       );
     }
   }
   ```
</details>

3. **Ejercicio 3**
   - Utiliza un `Column` para colocar 5 widgets de `Text` en forma vertical.
   - Inserta un `SizedBox` entre cada texto para crear un espacio uniforme.

![image](https://github.com/user-attachments/assets/4cf47d1b-d123-4979-a6c6-c323dc2b68eb)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio3Widget extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           Text('Texto 1'),
           SizedBox(height: 10),
           Text('Texto 2'),
           SizedBox(height: 10),
           Text('Texto 3'),
           SizedBox(height: 10),
           Text('Texto 4'),
           SizedBox(height: 10),
           Text('Texto 5'),
         ],
       );
     }
   }
   ```
</details>

4. **Ejercicio 4**
   - Coloca 3 widgets de `Text` diferentes dentro de un `Column`.
   - Agrega `Padding` alrededor de cada texto para crear espacio adicional.
   - Además, coloca un `SizedBox` grande debajo del primer texto para crear un espacio más grande.

![image](https://github.com/user-attachments/assets/4dea0e75-aa29-4e36-bfc1-bba57dcf5195)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio7Widget extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           Padding(
             padding: const EdgeInsets.all(8.0), 
             child: Text('Texto 1'),
           ),
           SizedBox(height: 30),
           Padding(
             padding: const EdgeInsets.all(8.0),
             child: Text('Texto 2'),
           ),
           Padding(
             padding: const EdgeInsets.all(8.0),
             child: Text('Texto 3'),
           ),
         ],
       );
     }
   }
   ```
</details>

5. **Ejercicio 5**
   - Dentro de un `Row`, coloca un widget de `Text` en el extremo izquierdo, un widget de `Text` con `Padding` en el centro, y otro widget de `Text` en el extremo derecho.
   - Agrega un `SizedBox` para crear espacio entre los textos.

![image](https://github.com/user-attachments/assets/86b6af35-67db-4752-8e0d-1f108c1dbc62)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio8Widget extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Row(
         mainAxisAlignment: MainAxisAlignment.spaceBetween, 
         children: [
           Text('Texto Izquierdo'),
           Padding(
             padding: const EdgeInsets.all(8.0), 
             child: Text('Texto Central'),
           ),
           Text('Texto Derecho'),
         ],
       );
     }
   }
   ```
</details>

6. **Ejercicio 6**
   - Crea un `Column` con un `Text` en la parte superior, seguido de un `SizedBox` para agregar espacio.
   - Luego, añade otro `Column` debajo con 2 widgets de `Text`.
   - Configura el `Padding` en el `Column` interno para ajustar los márgenes.

![image](https://github.com/user-attachments/assets/8fdfe7e4-1b76-4d40-b0a2-338caf3eb27e)

<details>
  <summary>Respuesta</summary>

   ```dart
   class Ejercicio9Widget extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           Text('Texto Superior'),
           SizedBox(height: 20), 
           Padding(
             padding: const EdgeInsets.all(8.0), 
             child: Column(
               children: [
                 Text('Texto 1'),
                 Text('Texto 2'),
               ],
             ),
           ),
         ],
       );
     }
   }
   ```
</details>
