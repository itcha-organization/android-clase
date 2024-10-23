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
