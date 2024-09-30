# Fundamentos de `Navigation`: Cómo navegar entre pantallas con Compose
## Descripción general de `Navigation` en Jetpack Compose
¿Por qué es importante `Navigation`?
- **Función de `Navigation`**: Gestiona las transiciones entre pantallas y permite que el usuario navegue entre diferentes pantallas dentro de la aplicación.
- **Gestión de la UI**: Se utiliza para controlar cómo se organizan y transitan las pantallas dentro de la aplicación.
- **Diferencia en Jetpack Compose**: A diferencia del diseño XML tradicional, en Jetpack Compose las interfaces de usuario se definen como funciones Composable.

---
## **Componentes principales de `Navigation`**
- **NavController**: Controlador que gestiona las transiciones entre pantallas y el backstack.
  - Ejemplo: `val navController = rememberNavController()`
- **NavHost**: El lugar donde se configura la navegación. Define qué pantalla se muestra.
  - Ejemplo: `NavHost(navController = navController, startDestination = "home")`
- **composable**: Función Composable para definir cada pantalla.
  - Ejemplo: `composable("home") { HomeScreen(navController) }`

---
## Flujo básico de la navegación
1. **Creación de NavHost**:
   - `NavHost` gestiona toda la navegación de la aplicación y es controlado por `NavController`.
   - Ejemplo:
     ```kotlin
     val navController = rememberNavController()
     NavHost(navController = navController, startDestination = "home") {
         composable("home") { HomeScreen(navController) }
         composable("details") { DetailsScreen(navController) }
     }
     ```

2. **Transición entre pantallas**:
   - Se utiliza `navController.navigate(route)` para navegar a otra pantalla.
   - Ejemplo:
     ```kotlin
     navController.navigate("details")
     ```
---

## Ejemplos: Transición simple entre pantallas
Ejemplo de transición de `HomeScreen` a `DetailsScreen`.
```kotlin
@Composable
fun MyApp() {
    val navController = rememberNavController()

    NavHost(navController = navController, startDestination = "home") {
        composable("home") {
            HomeScreen(navController)
        }
        composable("details") {
            DetailsScreen()
        }
    }
}

@Composable
fun HomeScreen(navController: NavController) {
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Button(onClick = { navController.navigate("details") }) {
            Text("Go to Details")
        }
    }
}

@Composable
fun DetailsScreen() {
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("This is the Details Screen")
    }
}
```

---

#### **Diapositiva 5: Gestión del backstack**

**Título:** ¿Qué es el backstack?
- **Función**: Recuerda la pantalla anterior cuando se navega, permitiendo al usuario regresar a la pantalla anterior al hacer clic en "volver".
- **`popBackStack()`**: Función que elimina la pantalla actual del backstack y regresa a la pantalla anterior.
  - Ejemplo: `navController.popBackStack()`
- **Importancia**: Es fundamental para gestionar múltiples pantallas de manera efectiva y proporcionar una experiencia de usuario fluida.

---

#### **Diapositiva 6: Explicación breve de los deep links**

**Título:** ¿Qué es un deep link?
- Un deep link es un enlace que permite acceder directamente a una pantalla específica desde una aplicación externa o un navegador.
- **Ejemplo de uso**:
  - Implementación para saltar a una pantalla específica desde una app de mensajería o un sitio web.
  - En Jetpack Compose, se puede configurar un deep link en el `NavHost`.

**Ejemplo de código:**
```kotlin
NavHost(navController = navController, startDestination = "home") {
    composable("home") { HomeScreen(navController) }
    composable("details/{itemId}", deepLinks = listOf(navDeepLink { uriPattern = "myapp://details/{itemId}" })) { backStackEntry ->
        DetailsScreen(itemId = backStackEntry.arguments?.getString("itemId"))
    }
}
```

---

#### **Diapositiva 7: Demostración de la navegación**

**Título:** Demostración de una app real
- En este punto, muestra una demostración de la navegación básica, exhibiendo el comportamiento de las transiciones de pantalla y la interacción con los botones.
- **Contenido de la demo**:
  1. Transición de la pantalla principal a la de detalles.
  2. Al hacer clic en el botón de retroceso, se regresa a la pantalla principal.

---

#### **Diapositiva 8: Preguntas y siguientes pasos**

**Título:** Preguntas y resumen de lo aprendido
- **Puntos clave**:
  - Función de la navegación y su uso básico.
  - Entender el rol de `NavController`, `NavHost` y las funciones `composable`.
  - Comprender el backstack y los deep links.

- **Próximos pasos**:
  - Resolver ejercicios para reforzar el flujo de navegación.
  - En la próxima clase, abordaremos temas más avanzados como la navegación con parámetros y la navegación con un bottom navigation.

---

### **Puntos clave para la explicación verbal**
- El `NavController` es como el "gestor de navegación" de toda la aplicación. Al igual que un sistema de navegación en un coche que nos guía hacia nuestro destino, el `NavController` controla la transición entre las pantallas de la aplicación.
- El `NavHost` es como una "estación de trenes", donde cada pantalla es una estación. A medida que el tren (la aplicación) sigue su ruta, el usuario se mueve entre las estaciones.
- La función `composable` representa cada "estación específica", es decir, la pantalla que se muestra en un momento dado.

---

Este material puede utilizarse para una explicación más detallada y organizada del concepto de navegación en Jetpack Compose, con ejemplos claros y una estructura que facilita la comprensión paso a paso.
