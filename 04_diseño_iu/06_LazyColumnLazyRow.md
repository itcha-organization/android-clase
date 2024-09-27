# LazyColumn, LazyRow

`LazyColumn` y `LazyRow` son componentes para la visualización eficiente de listas en Jetpack Compose.

La diferencia con `Column` y `Row` es si todos los elementos se dibujan cuando se dibuja la pantalla - `Column` y `Low` dibujan todos los elementos cuando se inicializa la pantalla, mientras que `LazyColumn` y `LazyRow` sólo dibujan los elementos que son visibles en la pantalla. Los elementos ocultos sólo se dibujan cuando se hacen visibles en la pantalla debido al desplazamiento. De este modo, el sistema no se sobrecarga aunque el número de elementos sea elevado. Utilice `LazyColumn` y `LazyRow` cuando el número de elementos a mostrar sea grande o cuando el número de elementos no esté predeterminado.

---

## **LazyColumn: Estructura básica**

`LazyColumn` se utiliza para mostrar una lista en dirección vertical. Los elementos solo se renderizan cuando son visibles en pantalla, lo que mejora el rendimiento.

### Estructura básica:

```kotlin
@Composable
fun SimpleLazyColumn() {
    LazyColumn {
        items(100) { index ->
            Text(text = "Elemento $index")
        }
    }
}
```

### Puntos clave:
- `LazyColumn` actúa como una lista.
- Usamos la función `items(count)` para especificar la cantidad de elementos en la lista.
- Cada elemento se define dentro de una lambda con el índice `index`.

---

## **LazyRow: Estructura básica**

`LazyRow` es similar a `LazyColumn`, pero los elementos se desplazan horizontalmente.

### Estructura básica:

```kotlin
@Composable
fun SimpleLazyRow() {
    LazyRow {
        items(100) { index ->
            Text(text = "Elemento $index")
        }
    }
}
```

### Puntos clave:
- `LazyRow` renderiza los elementos solo cuando son visibles, pero en una disposición horizontal.

---

## **Ejemplos**

### **Ejemplo 1: Crear una lista vertical sencilla**
Usa `LazyColumn` para crear una lista de 100 elementos. Cada elemento debe mostrar "Elemento #" seguido del número de índice.
```kotlin
@Composable
fun ListaVertical() {
    LazyColumn {
        items(100) { index ->
            Text(text = "Elemento $index", modifier = Modifier.padding(16.dp))
        }
    }
}
```

### Puntos clave:
- La función `items` toma el número de elementos que deseas mostrar, en este caso, 100. Para cada elemento de la lista, se ejecuta el contenido que está dentro de las llaves `{ index -> ... }`.
- Dentro de la lista, se renderiza un componente `Text` para mostrar el texto en cada fila de la columna. El texto es dinámico y cambia en función del índice de la lista, de modo que cada línea mostrará "Elemento 0", "Elemento 1", "Elemento 2", y así sucesivamente hasta "Elemento 99".

---

### **Ejemplo 2: Crear una lista horizontal sencilla**
Usa `LazyRow` para crear una lista de 50 elementos que se desplacen horizontalmente. Cada elemento debe mostrar "Elemento #" seguido del número de índice.
```kotlin
@Composable
fun ListaHorizontal() {
    LazyRow {
        items(50) { index ->
            Text(text = "Elemento $index", modifier = Modifier.padding(16.dp))
        }
    }
}
```

### Puntos clave:
- La función `items(50)` indica que se generarán 50 elementos en la lista. Para cada elemento, se ejecuta el bloque de código que sigue, creando dinámicamente el contenido para cada índice.
- El componente `Text` es el contenido principal de cada elemento de la fila horizontal. El texto se adapta al índice del elemento, de manera que los elementos se etiquetan como "Elemento 0", "Elemento 1", "Elemento 2", y así sucesivamente hasta "Elemento 49".

---

### **Ejemplo 3: Añadir espacio entre los elementos**
Usa `LazyColumn` para mostrar 30 elementos y añade un `Spacer` de 20dp entre cada uno de ellos para separar visualmente los elementos.
```kotlin
@Composable
fun ListaConEspaciado() {
    LazyColumn {
        items(30) { index ->
            Text(text = "Elemento $index", modifier = Modifier.padding(16.dp))
            Spacer(modifier = Modifier.height(20.dp))
        }
    }
}
```

### Puntos clave:
- La función `items(30)` define que se crearán 10 elementos en la lista. Para cada elemento, se ejecuta el bloque de código dentro de las llaves `{ index -> ... }`, generando el contenido correspondiente para cada índice.
- El componente `Text` muestra un texto por cada elemento de la lista. El texto se adapta dinámicamente según el índice, mostrando "Elemento 0", "Elemento 1", y así sucesivamente hasta "Elemento 9". Además, el modificador `Modifier.padding(16.dp)` agrega un margen interno de 16 puntos (dp) alrededor del texto, proporcionando espacio adicional para mejorar la legibilidad.
- El componente `Spacer` se utiliza para insertar un espacio vertical adicional entre los elementos de la lista. En este caso, se agrega un espaciado de 20 puntos (dp) de altura después de cada `Text`. Esto crea un espacio visual que separa claramente cada uno de los elementos de la lista.

---

### **Ejemplo 4: Crear una lista vertical de tarjetas**
Usa `LazyColumn` para mostrar 10 tarjetas (cards) dispuestas verticalmente. Cada tarjeta debe mostrar "Tarjeta #" seguido de una breve descripción.
```kotlin
@Composable
fun ListaDeTarjetasVertical() {
    LazyColumn {
        items(10) { index ->
            Card(modifier = Modifier
                .padding(8.dp)
                .width(150.dp)
            ) {
                Column(modifier = Modifier.padding(16.dp)) {
                    Text(text = "Tarjeta $index")
                    Text(text = "Breve descripción")
                }
            }
        }
    }
}
```

### Puntos clave:
- La función `items(10)` genera 10 elementos en la lista. Para cada elemento, se ejecuta el bloque de código que crea el contenido de la tarjeta.
- El componente `Card` es una tarjeta que proporciona un contenedor visualmente atractivo con esquinas redondeadas y una sombra. Aquí, el `Modifier.padding(8.dp)` agrega un margen de 8 puntos (dp) alrededor de cada tarjeta, y `Modifier.width(150.dp)` establece un ancho fijo de 150 puntos para la tarjeta.
- Dentro de cada tarjeta, se utiliza una `Column` para alinear verticalmente los elementos (en este caso, dos textos). El `Modifier.padding(16.dp)` en la columna agrega un margen interno de 16 puntos alrededor del contenido de la tarjeta, lo que mejora su apariencia.
- Hay dos componentes `Text` dentro de la tarjeta. El primero muestra el texto "Tarjeta $index", donde `$index` es el número de la tarjeta, lo que la hace dinámica. El segundo `Text` muestra una breve descripción fija, "Breve descripción", para cada tarjeta.

---

## Ejercicio
### Enunciado:
Usa `LazyColumn` para mostrar 30 tarjetas (cards) dispuestas verticalmente. Cada tarjeta debe mostrar "Tarjeta #" seguido de una breve descripción. Personaliza el diseño de las tarjetas a tu gusto.
