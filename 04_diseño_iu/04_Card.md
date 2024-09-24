# Uso de componentes básicos en Jetpack Compose

## 6. **Card** – Contenedor en forma de tarjeta
**Card** es un contenedor que enmarca su contenido con un estilo elevado.

```kotlin
@Composable
fun CardExample() {
    Card(
        modifier = Modifier.padding(16.dp),
        elevation = 4.dp
    ) {
        Column(
            modifier = Modifier.padding(16.dp)
        ) {
            Text("Título")
            Text("Aquí puedes agregar una descripción.")
        }
    }
}
```
## Puntos clave:
- Usa `Card` para encapsular contenido y darle una apariencia estructurada.
- La propiedad `elevation` ajusta la sombra, agregando un efecto de elevación.

---

## Ejercicio

## **Ejercicio 1: Crear una tarjeta con nombre**

### Enunciado:
Utiliza una `Card` para mostrar un nombre utilizando un componente `Text`, organizándolo en un `Column`.

#### Ejemplo de diseño:
```
[--------------------]
|     [ Nombre: John ]  |
[--------------------]
```

### Pista:
- Coloca un `Column` dentro de la `Card`, y dentro de esta un `Text` para mostrar el nombre.

<details>
  <summary>Ejemplo de solución</summary>

   ```kotlin
   @Composable
   fun NombreCard() {
       Card(elevation = 4.dp) {
           Column(modifier = Modifier.padding(16.dp)) {
               Text("Nombre: John")
           }
       }
   }
   ```
</details>
---

## **Ejercicio 2: Tarjeta con información de usuario**

### Enunciado:
Utiliza una `Card` para mostrar el nombre y la edad. Ambos deben mostrarse usando componentes `Text` dentro de un `Column`, uno debajo del otro.

#### Ejemplo de diseño:
```
[--------------------]
| Nombre: Maria      |
| Edad: 25           |
[--------------------]
```

### Pista:
- Usa un `Column` dentro de la `Card` y organiza el nombre y la edad con `Text`.

<details>
  <summary>Ejemplo de solución</summary>

   ```kotlin
   @Composable
   fun UsuarioCard() {
       Card(elevation = 4.dp) {
           Column(modifier = Modifier.padding(16.dp)) {
               Text("Nombre: Maria")
               Text("Edad: 25")
           }
       }
   }
   ```
</details>


---

## **Ejercicio 3: Información de usuario en una sola fila**

### Enunciado:
Muestra el nombre y la edad **horizontalmente** dentro de una `Card`, usando un `Row`. Ambos valores deben ser mostrados con componentes `Text`.

#### Ejemplo de diseño:
```
[-------------------------]
| Nombre: Carlos   Edad: 30 |
[-------------------------]
```

### Pista:
- Usa un `Row` dentro de la `Card` y coloca los componentes `Text` horizontalmente.

<details>
  <summary>Ejemplo de solución</summary>

   ```kotlin
   @Composable
   fun UsuarioRowCard() {
       Card(elevation = 4.dp) {
           Row(modifier = Modifier.padding(16.dp)) {
               Text("Nombre: Carlos")
               Spacer(modifier = Modifier.width(16.dp))
               Text("Edad: 30")
           }
       }
   }
   ```

</details>

---

## **Ejercicio 4: Tarjeta con múltiples datos**

### Enunciado:
Utiliza una `Card` para mostrar el nombre, la edad y la dirección, organizados verticalmente con `Text`. Cada línea debe mostrarse con un componente `Text` diferente.

#### Ejemplo de diseño:
```
[--------------------]
| Nombre: Ana        |
| Edad: 22           |
| Dirección: Madrid  |
[--------------------]
```

### Pista:
- Usa un `Column` dentro de la `Card` para organizar los componentes `Text` verticalmente.

<details>
  <summary>Ejemplo de solución</summary>

  ```kotlin
   @Composable
   fun InformacionCard() {
       Card(elevation = 4.dp) {
           Column(modifier = Modifier.padding(16.dp)) {
               Text("Nombre: Ana")
               Text("Edad: 22")
               Text("Dirección: Madrid")
           }
       }
   }
   ```  
</details>

---

## **Ejercicio 5: Tarjeta de perfil**

### Enunciado:
Crea una `Card` para mostrar un perfil con el nombre y una breve introducción. El nombre debe aparecer en la parte superior dentro de un `Row`, y la introducción debe aparecer debajo usando `Text`.

#### Ejemplo de diseño:
```
[---------------------------]
| Nombre: Luis               |
| Breve introducción:        |
| Soy un desarrollador móvil |
[---------------------------]
```

### Pista:
- Usa un `Column` dentro de la `Card`. El nombre debe estar dentro de un `Row` en la parte superior, y la introducción debe aparecer debajo.

<details>
  <summary>Ejemplo de solución</summary>

  ```kotlin
   @Composable
   fun PerfilCard() {
       Card(elevation = 4.dp) {
           Column(modifier = Modifier.padding(16.dp)) {
               Row {
                   Text("Nombre: Luis")
               }
               Spacer(modifier = Modifier.height(8.dp))
               Text("Breve introducción:")
               Text("Soy un desarrollador móvil.")
           }
       }
   }
   ```  
</details>

