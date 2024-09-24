# Uso de componentes básicos en Jetpack Compose

## 4. **OutlinedButton** – Botón con borde
**OutlinedButton** es un botón con un borde alrededor.

```kotlin
@Composable
fun OutlinedButtonExample() {
    OutlinedButton(onClick = { /* Acción al pulsar el botón */ }) {
        Text("Haz clic aquí")
    }
}
```
## Puntos clave:
- Usa la propiedad `onClick` para definir la acción al pulsar el botón.
- Puedes colocar texto o íconos dentro del botón.

**Ejemplo: boton con icono**
```kotlin
@Composable
fun OutlinedButtonExampleIcono() {
    OutlinedButton(onClick = { /* Acción al pulsar el botón */ }) {
        Icon(
            Icons.Filled.Favorite,
            contentDescription = null,
            modifier = Modifier.size(ButtonDefaults.IconSize)
        )
        Spacer(Modifier.size(ButtonDefaults.IconSpacing))
        Text("Like")
    }
}
```
Puntos clave:
- Dentro del `OutlinedButton`, se utiliza un composable `Icon` para mostrar un icono. El composable `Icon` toma un icono de la colección `Icons.Filled`, específicamente el icono `Favorite`.
- Un composable `Spacer` se utiliza para agregar espacio entre el icono y el texto. El tamaño del espaciador se establece al espaciado predeterminado del icono del botón.
- Finalmente, un composable `Text` se utiliza para mostrar el texto "Like" junto al icono. Este texto se muestra dentro del `OutlinedButton`, creando un botón con un icono y texto.

---

## 5. **OutlinedTextField** – Campo de texto con borde
**OutlinedTextField** es un campo de entrada de texto con borde.

```kotlin
@Composable
fun OutlinedTextFieldExample() {
    var text by remember { mutableStateOf("") }

    OutlinedTextField(
        value = text,
        onValueChange = { text = it },
        label = { Text("Introduce tu nombre") }
    )
}
```
## Puntos clave:
- `value` mantiene el texto ingresado y `onValueChange` refleja los cambios en el texto.
- Usa la propiedad `label` para agregar una etiqueta descriptiva al campo de texto.

**Ejemplo: boton con icono**
```kotlin
@Composable
fun OutlinedTextFieldExampleTecladoNumerico() {
    var text by remember { mutableStateOf("") }

    OutlinedTextField(
        value = text,
        onValueChange = { text = it },
        label = { Text("Introduce numero") },
        //mostrando el teclado numerico
        keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Number),
    )
}
```
Puntos clave:
-  El parámetro `keyboardOptions` se establece en `KeyboardOptions(keyboardType = KeyboardType.Number)`, lo que configura el campo de texto para mostrar un teclado numérico cuando está enfocado.

---

## **Ejercicios: Crear diseños usando Column, Row, OutlinedButton y OutlinedTextField**

### **Ejercicio 1: Formulario de entrada de nombre y botón de envío**

#### Enunciado:
Coloca un `OutlinedTextField` para ingresar el nombre y un `OutlinedButton` para enviar, **en forma vertical**.

#### Ejemplo de diseño:
![image](https://github.com/user-attachments/assets/6a489a75-f0a7-4c04-b94d-35b78719fdb3)

#### Pista:
- Utiliza `Column` para organizar el `OutlinedTextField` y el `OutlinedButton` verticalmente.
- Utiliza `Spacer` para insertar un espacio de altura `16.dp` entre los componentes.

<details>
  <summary>Ejemplo de solución</summary>
  
   ```kotlin
   @Composable
   fun NombreYBoton() {
       Column {
           OutlinedTextField(value = "", onValueChange = {}, label = { Text("Nombre") })
           Spacer(modifier = Modifier.height(16.dp))
           OutlinedButton(onClick = {}) {
               Text("Enviar")
           }
       }
   }
   ```
</details>

---

### **Ejercicio 2: Entrada de información del usuario en horizontal**

#### Enunciado:
Coloca dos `OutlinedTextField` para ingresar el nombre y la edad, junto con un botón de envío, **en forma horizontal**.

#### Ejemplo de diseño:
![image](https://github.com/user-attachments/assets/79cdfafd-a582-491c-bc55-815c35c07d55)

#### Pista:
- Utiliza `Row` para alinear los tres componentes horizontalmente.
- Utiliza `Spacer` para insertar un espacio de ancho `16.dp` entre los componentes.

<details>
  <summary>Ejemplo de solución</summary>
  
   ```kotlin
   @Composable
   fun InformacionUsuario() {
       Row {
           OutlinedTextField(value = "", onValueChange = {}, label = { Text("Nombre") })
           Spacer(modifier = Modifier.width(16.dp))
           OutlinedTextField(value = "", onValueChange = {}, label = { Text("Edad") })
           Spacer(modifier = Modifier.width(16.dp))
           OutlinedButton(onClick = {}) {
               Text("Enviar")
           }
       }
   }
   ```
</details>

---

### **Ejercicio 3: Formulario de dirección**

#### Enunciado:
Crea un formulario con varios `OutlinedTextField` para ingresar direcciones, y coloca el botón de envío **en la parte inferior**.

#### Ejemplo de diseño:
![image](https://github.com/user-attachments/assets/0b785794-6ecf-49bb-b53b-546af72ba9d7)

#### Pista:
- Utiliza `Column` para organizar los campos y el botón en una lista vertical.
- Utiliza `Spacer` para insertar un espacio de altura `16.dp` entre los componentes.

<details>
  <summary>Ejemplo de solución</summary>
  
   ```kotlin
   @Composable
   fun FormularioDireccion() {
       Column {
           OutlinedTextField(value = "", onValueChange = {}, label = { Text("Dirección 1") })
           Spacer(modifier = Modifier.height(16.dp))
           OutlinedTextField(value = "", onValueChange = {}, label = { Text("Dirección 2") })
           Spacer(modifier = Modifier.height(16.dp))
           OutlinedTextField(value = "", onValueChange = {}, label = { Text("Ciudad") })
           Spacer(modifier = Modifier.height(16.dp))
           OutlinedButton(onClick = {}) {
               Text("Enviar")
           }
       }
   }
   ```
</details>

---

### **Ejercicio 4: Crear un formulario de inicio de sesión**

#### Enunciado:
Coloca un `OutlinedTextField` para el nombre de usuario y otro para la contraseña, y coloca un botón de inicio de sesión **en la parte inferior**.

#### Ejemplo de diseño:
![image](https://github.com/user-attachments/assets/a35e69a9-d47d-4150-8b34-9ea6bc616a2d)

#### Pista:
- Utiliza `Column` para organizar los campos y el botón verticalmente.
- Utiliza `Spacer` para insertar un espacio de altura `16.dp` entre los componentes.

<details>
  <summary>Ejemplo de solución</summary>
  
   ```kotlin
   @Composable
   fun FormularioLogin() {
       Column {
           OutlinedTextField(value = "", onValueChange = {}, label = { Text("Usuario") })
           Spacer(modifier = Modifier.height(16.dp))
           OutlinedTextField(value = "", onValueChange = {}, label = { Text("Contraseña") })
           Spacer(modifier = Modifier.height(16.dp))
           OutlinedButton(onClick = {}) {
               Text("Iniciar sesión")
           }
       }
   }
   ```
</details>

---

### **Ejercicio 5: Formulario de búsqueda**

#### Enunciado:
Crea un `OutlinedTextField` para ingresar una búsqueda y un botón de búsqueda **en la misma línea**. Agrega un texto que diga "Resultados de la búsqueda" debajo del botón.

#### Ejemplo de diseño:
![image](https://github.com/user-attachments/assets/edf05a38-cf32-4313-a289-bc2d75ec7e66)

#### Pista:
- Utiliza `Row` para alinear el campo de búsqueda y el botón, y `Column` para agregar el texto debajo.
- Utiliza `Spacer` para insertar un espacio de ancho `16.dp` entre `OutlinedTextField` y `OutlinedButton`.
- Utiliza `Spacer` para insertar un espacio de altura `16.dp` entre `Row` y `Text`.

<details>
  <summary>Ejemplo de solución</summary>
  
   ```kotlin
   @Composable
   fun FormularioBusqueda() {
       Column {
           Row {
               OutlinedTextField(value = "", onValueChange = {}, label = { Text("Buscar") })
               Spacer(modifier = Modifier.width(16.dp))
               OutlinedButton(onClick = {}) {
                   Text("Buscar")
               }
           }
           Spacer(modifier = Modifier.height(16.dp))
           Text("Resultados de la búsqueda")
       }
   }
   ```
</details>
