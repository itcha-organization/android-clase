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
- En la dirección del eje principal (vertical), utilice `Expanded` para maximizar el espacio.
- En la dirección del eje cruzado (horizontal), utilice `SizedBox` con `width: double.infinity` para maximizar el espacio.

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
- En la dirección del eje principal (horizontal), utilice `Expanded` para maximizar el espacio.
- En la dirección del eje cruzado (vertical), utilice `SizedBox` con `height: double.infinity` para maximizar el espacio.

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
   class Ejercicio4Widget extends StatelessWidget {
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

![image](https://github.com/user-attachments/assets/b16e16eb-7652-4043-b72b-67aaa5240825)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio5Widget extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Row(
         mainAxisAlignment: MainAxisAlignment.spaceBetween, 
         children: [
           Text('Texto Izquierdo'),
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
   class Ejercicio6Widget extends StatelessWidget {
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


### 6. `Card`

El widget `Card` representa un componente de tarjeta en el diseño de Material Design. El widget `Card` es útil para mostrar contenido visualmente separado.

#### Estructura básica del `Card`

El widget `Card` generalmente contiene otros widgets (por ejemplo, `Text`) como hijos. Además, se pueden configurar la redondez de las esquinas (`borderRadius`) y la sombra (`elevation`) para aplicar un estilo acorde al diseño.

#### Propiedades principales

- **`elevation`**: Establece la profundidad de la sombra de la tarjeta. Cuanto mayor sea el valor, más oscura será la sombra.
- **`shape`**: Define la forma de la tarjeta. Normalmente, se usa `RoundedRectangleBorder` para especificar el redondeo de las esquinas.
- **`margin`**: Establece el margen exterior de la tarjeta.
- **`color`**: Configura el color de fondo de la tarjeta.

#### Ejemplo básico de uso

El siguiente código muestra cómo utilizar `Card`. En este ejemplo, se coloca un widget `Text` dentro de la tarjeta y se configuran la sombra (`elevation`) y el redondeo de las esquinas (`shape`).

```dart
class CardWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Card(
      elevation: 4.0, // Configuración de la sombra
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(10.0), // Configuración del redondeo
      ),
      child: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Text('¡Hola, esto es una tarjeta!'),
      ),
    );
  }
}
```

## Ejercicios

### Ejercicio 1: Diseño simple con tarjeta
- Crea un widget `Card` y dentro de él utiliza un widget `Text` para mostrar el mensaje "Bienvenido a Flutter".
- Agrega `Padding` para añadir espacio alrededor del texto.

![image](https://github.com/user-attachments/assets/74f18d83-6a80-4741-ae40-8a1c918dda8a)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio1 extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Card(
         child: Padding(
           padding: EdgeInsets.all(16.0), // Espacio alrededor del texto
           child: Text('Bienvenido a Flutter'),
         ),
       );
     }
   }
   ```
</details>

### Ejercicio 2: Colocar elementos en fila dentro de una tarjeta
- Dentro del `Card`, utiliza un `Row` para alinear dos widgets `Text` de forma horizontal.
- Añade `Padding` alrededor de la `Row` para crear un espacio de 16 píxeles.
- Añade `Padding` alrededor de cada texto para crear espacio.

![image](https://github.com/user-attachments/assets/21727b25-dd93-4afb-b083-3e4ffb8ba85d)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Exercise2 extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Card(
         child: Padding(
           padding: EdgeInsets.all(16.0),
           child: Row(
             children: [
               Padding(
                 padding: EdgeInsets.only(right: 8.0),
                 child: Text('Hello'),
               ),
               Padding(
                 padding: EdgeInsets.only(left: 8.0),
                 child: Text('World'),
               ),
             ],
           ),
         ),
       );
     }
   }
   ```
</details>

### Ejercicio 3: Colocar múltiples tarjetas en forma vertical
- Coloca tres widgets `Card` diferentes dentro de un `Column` para alinearlos de manera vertical.
- Cada `Card` debe mostrar un texto diferente y tener `Padding` alrededor del texto para crear espacio.
- Añade un `SizedBox` y deja un espacio entre cada `Card`.

![image](https://github.com/user-attachments/assets/950219b6-a6bf-4d5a-834a-a31de1a5c35d)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio3 extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           Card(
             child: Padding(
               padding: EdgeInsets.all(16.0),
               child: Text('Tarjeta 1'),
             ),
           ),
           SizedBox(height: 10), // Espacio entre las tarjetas
           Card(
             child: Padding(
               padding: EdgeInsets.all(16.0),
               child: Text('Tarjeta 2'),
             ),
           ),
           SizedBox(height: 10),
           Card(
             child: Padding(
               padding: EdgeInsets.all(16.0),
               child: Text('Tarjeta 3'),
             ),
           ),
         ],
       );
     }
   }
   ```
</details>

### Ejercicio 4: Crear un diseño anidado dentro de la tarjeta
- Dentro del `Card`, coloca un `Column` y luego combina un `Row` y un `Column` para crear un diseño complejo anidado.
- Agrega `Padding` a cada elemento para ajustar el diseño general.
- Cambia el color de fondo estableciendo `Colours.amber` a la propiedad `color` de la `Card`.

![image](https://github.com/user-attachments/assets/a9343a6c-617f-495b-a553-945ab89d98e8)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio4 extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Card(
         color: Colors.amber,
         child: Padding(
           padding: EdgeInsets.all(16.0),
           child: Column(
             children: [
               Row(
                 children: [
                   Text('Fila 1, Elemento 1'),
                   SizedBox(width: 10),
                   Text('Fila 1, Elemento 2'),
                 ],
               ),
               SizedBox(height: 10),
               Column(
                 children: [
                   Text('Columna 1, Elemento 1'),
                   SizedBox(height: 5),
                   Text('Columna 1, Elemento 2'),
                 ],
               ),
             ],
           ),
         ),
       );
     }
   }
   ```
</details>

### Ejercicio 5: Cambiar el color de fondo de la tarjeta
- Utiliza la propiedad `color` del widget `Card` para crear varias tarjetas con diferentes colores de fondo y colócalas en un `Column` de forma vertical.
- Cada tarjeta debe mostrar un texto diferente y tener `Padding` para hacer el diseño más legible.

![image](https://github.com/user-attachments/assets/4de78711-8660-44d2-86a6-3bb7d92830c7)

<details>
  <summary>Respuesta</summary>
   
   ```dart
   class Ejercicio5 extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Column(
         children: [
           Card(
             color: Colors.lightBlueAccent, // Cambio del color de fondo
             child: Padding(
               padding: EdgeInsets.all(16.0),
               child: Text('Tarjeta con fondo azul'),
             ),
           ),
           SizedBox(height: 10),
           Card(
             color: Colors.greenAccent,
             child: Padding(
               padding: EdgeInsets.all(16.0),
               child: Text('Tarjeta con fondo verde'),
             ),
           ),
         ],
       );
     }
   }
   ```
</details>
