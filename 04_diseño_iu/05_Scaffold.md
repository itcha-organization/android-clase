# Scaffold y `topBar`

`Scaffold` es un componente básico de diseño en Jetpack Compose que se utiliza para estructurar la interfaz de usuario. Facilita la creación de áreas como `topBar`, `bottomBar` y `floatingActionButton`.  
En esta lección, aprenderemos cómo utilizar `topBar` para configurar un encabezado en la parte superior de la aplicación.

## Objetivos
- Aprender el uso básico del componente `Scaffold`.
- Comprender cómo configurar la barra superior (topBar) para mostrar una barra de herramientas en la parte superior de la aplicación.

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

