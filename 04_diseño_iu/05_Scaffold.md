# Scaffold

[`Scaffold`](https://developer.android.com/develop/ui/compose/components/scaffold?hl=es-419) es un componente básico de diseño en Jetpack Compose que se utiliza para estructurar la interfaz de usuario. Facilita la creación de áreas como `topBar`, `bottomBar` y `floatingActionButton`.  
En esta lección, aprenderemos cómo utilizar `topBar` para configurar un encabezado en la parte superior de la aplicación.

## Objetivos
- Aprender el uso básico del componente `Scaffold`.
- Comprender cómo configurar la barra superior (topBar) para mostrar una barra de herramientas en la parte superior de la aplicación.
- Comprender cómo `innerPadding` funciona.

---

## **Paso 1: Crear la estructura básica de Scaffold**

Primero, crearemos un uso básico de `Scaffold` para entender su estructura.

```kotlin
@Composable
fun BasicScaffoldExample() {
    Scaffold() { innerPadding ->
        Text(
            text = "Estructura básica de Scaffold",
            modifier = Modifier
                .fillMaxSize()
                .padding(innerPadding),
        )
    }
}
```

**Explicación**:  
- `Scaffold` es un contenedor que organiza toda la pantalla de la aplicación.
- El parámetro `content` define el contenido principal, en este caso, un simple `Text` que ocupa toda la pantalla.

---

## **Paso 2: Configurar `topBar`**

Ahora agregaremos una barra superior (topBar) a `Scaffold` usando `TopAppBar` para crear una barra de herramientas en la parte superior de la aplicación.

```kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun ScaffoldConTopBar() {
    Scaffold(
        // Añadir una barra de herramientas en la parte superior
        topBar = {
            TopAppBar(
                title = { Text(text = "ScaffoldConTopBar", color = Color.White) },
                colors = TopAppBarDefaults.topAppBarColors(
                    containerColor = Color.Blue
                )
            )
        }) { innerPadding ->
            Text(
                text = "Estructura básica de Scaffold",
                modifier = Modifier
                    .fillMaxSize()
                    .padding(innerPadding),
            )
        }
}
```

**Explicación**:  
- El parámetro `topBar` define una barra en la parte superior de la pantalla.
- `TopAppBar` proporciona la barra de herramientas, donde hemos configurado un título y un color de fondo.
- La barra se mantiene fija en la parte superior, incluso cuando el usuario se desplaza.

---

## ¿Qué es `innerPadding`?

El `innerPadding` en `Scaffold` se utiliza principalmente para aplicar un relleno (padding) al área de contenido cuando se construyen las interfaces en Jetpack Compose. Dado que `Scaffold` suele incorporar múltiples elementos de UI, como el `topBar` o el `bottomBar`, el uso de `innerPadding` asegura que el contenido no se superponga con estos elementos.

Este padding es útil cuando se agregan barras como `topBar` o `bottomBar`, ya que se ajusta automáticamente para evitar que el contenido se superponga con ellos.

### Uso básico de `innerPadding`

En el siguiente ejemplo, el padding se aplica al componente `Text` dentro de un `Column`, usando los valores de `innerPadding` proporcionados por el `Scaffold`:

```kotlin
@Composable
fun ScaffoldWithInnerPaddingExample() {
    Scaffold(
        topBar = {
            TopAppBar(title = { Text("Ejemplo de Scaffold") })
        },
        content = { innerPadding ->
            // Se aplica el innerPadding
            Column(modifier = Modifier.padding(innerPadding)) {
                Text(text = "Este es el contenido del Scaffold.")
            }
        }
    )
}
```
**Explicación:**
- En este caso, el `topBar` del `Scaffold` usa un `TopAppBar` que aparece en la parte superior de la pantalla.
- Dentro del bloque `content`, el `innerPadding` ajusta automáticamente el contenido, como el `Column`, aplicando un relleno que evita que el `Text` se superponga con el `TopAppBar`.

### Puntos clave sobre el `innerPadding`:
1. **Aplicación automática**: Cuando se utilizan elementos como `topBar` o `bottomBar` en el `Scaffold`, el relleno necesario se pasa automáticamente como `innerPadding` al bloque `content`.
2. **Ajuste de la disposición**: Para asegurarse de que el contenido no se superponga con las barras de la interfaz, se debe aplicar `Modifier.padding(innerPadding)` a los componentes dentro del `content`.
3. **Personalización posible**: Si es necesario, puedes añadir más padding además del `innerPadding` por defecto para ajustar aún más el diseño.

Ejemplo de añadir padding adicional:
```kotlin
Column(modifier = Modifier.padding(innerPadding).padding(16.dp)) {
    Text(text = "Con padding adicional")
}
```

El `innerPadding` es especialmente útil para evitar que los componentes de la interfaz se superpongan con elementos fijos como las barras de la aplicación, asegurando que la disposición sea limpia y funcional.

## **4. Ejercicios**

### **Ejercicio 1**
**Problema**: Modifique el siguiente código inicial para que la barra superior muestre la cadena "Ejercicio 1".

**Ejemplo de diseño:**
<br>
![image](https://github.com/user-attachments/assets/6b83d8a7-54c4-4071-b4cf-0d45aeca3a6b)

```kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun ScaffoldEjercicio1() {
    Scaffold(
        // Añadir una barra de herramientas en la parte superior
        topBar = {
            TopAppBar(
                title = { Text(text = "ScaffoldConTopBar", color = Color.White) },
                colors = TopAppBarDefaults.topAppBarColors(
                    containerColor = Color.Blue
                )
            )
        }) { innerPadding ->
        Text(
            text = "Estructura básica de Scaffold",
            modifier = Modifier
                .fillMaxSize()
                .padding(innerPadding),
        )
    }
}
```

<details>
  <summary>Ejemplo de solución</summary>
    
  ```diff
  @OptIn(ExperimentalMaterial3Api::class)
  @Composable
  fun ScaffoldEjercicio1() {
      Scaffold(
          // Añadir una barra de herramientas en la parte superior
          topBar = {
              TopAppBar(
  +                title = { Text(text = "Ejercicio 1", color = Color.White) },
                  colors = TopAppBarDefaults.topAppBarColors(
                      containerColor = Color.Blue
                  )
              )
          }) { innerPadding ->
          Text(
              text = "Estructura básica de Scaffold",
              modifier = Modifier
                  .fillMaxSize()
                  .padding(innerPadding),
          )
      }
  }
  ```
</details>

### **Ejercicio 2**
**Problema**: Modifique el siguiente código inicial para cambiar el color de la barra superior a `Color.Gray`.

**Ejemplo de diseño:**
<br>
![image](https://github.com/user-attachments/assets/2c4a143c-6693-4070-a028-02e0ad1985f9)

```kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun ScaffoldEjercicio2() {
    Scaffold(
        // Añadir una barra de herramientas en la parte superior
        topBar = {
            TopAppBar(
                title = { Text(text = "ScaffoldConTopBar", color = Color.White) },
                colors = TopAppBarDefaults.topAppBarColors(
                    containerColor = Color.Blue
                )
            )
        }) { innerPadding ->
        Text(
            text = "Estructura básica de Scaffold",
            modifier = Modifier
                .fillMaxSize()
                .padding(innerPadding),
        )
    }
}
```

<details>
  <summary>Ejemplo de solución</summary>
    
  ```diff
  @OptIn(ExperimentalMaterial3Api::class)
  @Composable
  fun ScaffoldEjercicio2() {
      Scaffold(
          // Añadir una barra de herramientas en la parte superior
          topBar = {
              TopAppBar(
                  title = { Text(text = "ScaffoldConTopBar", color = Color.White) },
                  colors = TopAppBarDefaults.topAppBarColors(
  +                    containerColor = Color.Gray
                  )
              )
          }) { innerPadding ->
          Text(
              text = "Estructura básica de Scaffold",
              modifier = Modifier
                  .fillMaxSize()
                  .padding(innerPadding),
          )
      }
  }
  ```
</details>


### **Ejercicio 3**
**Problema**: Modifique el siguiente código inicial para agregar `TopBar`(la barra superior).

**Ejemplo de diseño:**
<br>
![image](https://github.com/user-attachments/assets/5c61fb1c-021e-45d1-94ea-9591c4dc626f)

```kotlin
@Composable
fun ScaffoldEjercicio3() {
    Scaffold() { innerPadding ->
        Text(
            text = "Estructura básica de Scaffold",
            modifier = Modifier
                .fillMaxSize()
                .padding(innerPadding),
        )
    }
}
```

<details>
  <summary>Ejemplo de solución</summary>
    
  ```diff
  + @OptIn(ExperimentalMaterial3Api::class)
  @Composable
  fun ScaffoldEjercicio3() {
  +    Scaffold(
  +        // Añadir una barra de herramientas en la parte superior
  +        topBar = {
  +            TopAppBar(
  +                title = { Text(text = "TopBarColorMagenta", color = Color.White) },
  +                colors = TopAppBarDefaults.topAppBarColors(
  +                    containerColor = Color.Magenta
  +                )
  +            )
  +        }
  +    ) { innerPadding ->
          Text(
              text = "Estructura básica de Scaffold",
              modifier = Modifier
                  .fillMaxSize()
                  .padding(innerPadding),
          )
      }
  }
  ```
</details>
