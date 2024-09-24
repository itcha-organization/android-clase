# **Uso de componentes básicos en Jetpack Compose**

## 1. **Text** – Mostrar texto
**Text** es el componente básico para mostrar texto en pantalla.

```kotlin
@Composable
fun TextExample() {
    Text(text = "Hola, Kyo Onuma", fontSize = 24.sp)
}
```
## Puntos clave:
- Usa la propiedad `text` para especificar el texto a mostrar.
- Con `fontSize` puedes cambiar el tamaño de la fuente.

---

## 2. **Column** – Layout en dirección vertical
**Column** organiza sus hijos de forma vertical.

```kotlin
@Composable
fun ColumnExample() {
    Column(
        modifier = Modifier.padding(16.dp)
    ) {
        Text(text = "Nombre: Kyo Onuma")
        Text(text = "Profesión: Profesor")
    }
}
```
## Puntos clave:
- `Column` organiza varios componentes en una disposición vertical.
- Usa `padding` para ajustar el espacio interior alrededor de los componentes.

**Ejemplo: lleva sus hijos alineados**
```kotlin
@Composable
fun ColumnExampleAlineado() {
    Column(
        modifier = Modifier.padding(16.dp).fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally

    ) {
        Text(text = "Nombre: Kyo Onuma")
        Text(text = "Profesión: Profesor")
    }
}
```
## Puntos clave:
- Usa `fillMaxSize` para llenar el tamaño máximo disponible de su contenedor padre.
- El parámetro `verticalArrangement` se establece en `Arrangement.Center`, lo que centra los elementos hijos verticalmente dentro de la columna.
- De manera similar, el parámetro `horizontalAlignment` se establece en `Alignment.CenterHorizontally`, lo que centra los elementos hijos horizontalmente.

---

## 3. **Row** – Layout en dirección horizontal
**Row** organiza sus hijos de forma horizontal.

```kotlin
@Composable
fun RowExample() {
    Row(
        modifier = Modifier.padding(16.dp)
    ) {
        Text(text = "Nombre:")
        Text(text = "Kyo Onuma")
    }
}
```
## Puntos clave:
- `Row` permite alinear componentes horizontalmente.
- Usa `Modifier` para personalizar el diseño y estilo.

**Ejemplo: lleva sus hijos alineados**
```kotlin
@Composable
fun RowExampleAlineado() {
    Row(
        modifier = Modifier.padding(16.dp).fillMaxSize(),
        horizontalArrangement = Arrangement.Center,
        verticalAlignment = Alignment.CenterVertically
    ) {
        Text(text = "Nombre:")
        Text(text = "Kyo Onuma")
    }
}
```
## Puntos clave:
- Usa `fillMaxSize` para llenar el tamaño máximo disponible de su contenedor padre.
- El parámetro horizontalArrangement se establece en Arrangement.Center, lo que centra los elementos hijos horizontalmente dentro de la fila.
- De manera similar, el parámetro verticalAlignment se establece en Alignment.CenterVertically, lo que centra los elementos hijos verticalmente.

---
