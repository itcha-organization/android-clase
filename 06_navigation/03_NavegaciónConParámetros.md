# Navegación con parámetros utilizando `navArgument` en Jetpack Compose

### **Objetivo:**
El objetivo de este material es aprender cómo utilizar `navArgument` en Jetpack Compose para pasar parámetros entre pantallas durante la navegación. Esta es una técnica importante que se usa comúnmente en proyectos reales.

### **Requisitos previos:**
- Conocimiento básico de Jetpack Compose (como las funciones `Composable` y el uso de `Modifier`)
- Familiaridad con la navegación usando `NavController`

### **Contenido de aprendizaje:**
- Navegación con parámetros utilizando `navArgument`
- Especificar el tipo de parámetro con `NavType`

---

## **1. Sintaxis básica y pasar parámetros**

Primero, aprenderemos cómo pasar parámetros de una pantalla a otra utilizando `navArgument`. En este ejemplo, se pasará un parámetro de texto desde una pantalla A a una pantalla B.

### **Ejemplo de código:**
```kotlin
@Composable
fun NavManager() {
    val navController = rememberNavController()
    NavHost(navController = navController, startDestination = "home") {

        composable("home") {
            HomeScreen(navController)
        }
        composable(
            route = "details/{nombre}",
            arguments = listOf(navArgument("nombre") { type = NavType.StringType })
        ) { backStackEntry ->
            val nombre = backStackEntry.arguments?.getString("nombre") ?: ""
            DetailsScreen(nombre)
        }
    }
}

@Composable
fun HomeScreen(navController: NavController) {
    var nombre by remember { mutableStateOf("") }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        OutlinedTextField(
            value = nombre,
            onValueChange = {nombre = it},
            label = { Text(text = "Nombre")},
            modifier = Modifier
                .fillMaxWidth()
                .padding(horizontal = 16.dp)
                .padding(bottom = 12.dp)
        )
        Button(onClick = { navController.navigate("details/$nombre") }) {
            Text("Go to Details")
        }
    }
}

@Composable
fun DetailsScreen(nombre: String) {
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("Nombre: $nombre")
    }
}
```

### **Explicacion:**
Este código muestra un ejemplo sencillo de navegación y paso de parámetros utilizando Jetpack Compose. La función `NavManager` gestiona toda la navegación de la aplicación, donde se ingresa un nombre en la pantalla principal (`HomeScreen`) y se pasa a la pantalla de detalles (`DetailsScreen`) para ser mostrado. A continuación, se explica cada parte del código:

#### 1. Función `NavManager`

- **`composable(route = "details/{nombre}")`**: La ruta `"details/{nombre}"` está asociada a la pantalla `DetailsScreen`, que recibe un parámetro llamado `nombre`.  
  - **`navArgument("nombre")`**: Define el argumento `nombre` como de tipo cadena (`StringType`).
  - **`backStackEntry`**: Contiene los argumentos de navegación. Utilizamos `backStackEntry.arguments` para obtener el parámetro `nombre` pasado desde la pantalla anterior.
  - **`DetailsScreen(nombre)`**: Llama a la pantalla de detalles y le pasa el valor de `nombre` para que sea mostrado.

#### 2. Función `HomeScreen`
- **`var nombre by remember { mutableStateOf("") }`**: La variable `nombre` almacena el valor ingresado por el usuario. Usamos `remember` y `mutableStateOf` para conservar el estado del nombre incluso después de la recomposición de la UI.
  
- **`OutlinedTextField`**: Es un campo de texto donde el usuario puede ingresar su nombre. El valor del campo es controlado por la variable `nombre` y se actualiza cuando el usuario escribe.
  
- **`Button(onClick)`**: Al hacer clic en el botón, se navega a la pantalla `DetailsScreen` utilizando la función `navController.navigate("details/$nombre")`. El nombre ingresado es pasado como parte de la ruta.

#### 3. Función `DetailsScreen`
- **`DetailsScreen(nombre: String)`**: Esta pantalla recibe el parámetro `nombre` desde la pantalla `HomeScreen` y lo muestra en un texto.
- **`Text("Nombre: $nombre")`**: Muestra el nombre recibido como parámetro en la pantalla.

---

## **2. Pasar múltiples parámetros**

Ahora aprenderemos cómo pasar múltiples parámetros entre pantallas. En este caso, pasaremos el nombre y el ID de un usuario.

### **Ejemplo de código:**
```kotlin
@Composable
fun NavManager() {
    val navController = rememberNavController()
    NavHost(navController = navController, startDestination = "home") {

        composable("home") {
            HomeScreen(navController)
        }
        composable(
            route = "details/{nombre}/{edad}",
            arguments = listOf(
                navArgument("nombre") { type = NavType.StringType },
                navArgument("edad") { type = NavType.IntType }
            )
        ) { backStackEntry ->
            val nombre = backStackEntry.arguments?.getString("nombre") ?: ""
            val edad = backStackEntry.arguments?.getInt("edad") ?: 0
            DetailsScreen(nombre, edad)
        }
    }
}

@Composable
fun HomeScreen(navController: NavController) {
    var nombre by remember { mutableStateOf("") }
    var edad by remember { mutableStateOf("") }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        OutlinedTextField(
            value = nombre,
            onValueChange = {nombre = it},
            label = { Text(text = "Nombre")},
            modifier = Modifier
                .fillMaxWidth()
                .padding(horizontal = 16.dp)
                .padding(bottom = 12.dp)
        )
        OutlinedTextField(
            value = edad,
            onValueChange = {edad = it},
            label = { Text(text = "Edad")},
            modifier = Modifier
                .fillMaxWidth()
                .padding(horizontal = 16.dp)
                .padding(bottom = 12.dp)
        )
        Button(onClick = { navController.navigate("details/$nombre/$edad") }) {
            Text("Go to Details")
        }
    }
}

@Composable
fun DetailsScreen(nombre: String, edad: Int) {
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("Nombre: $nombre")
        Text("Edad: $edad")
    }
}
```

### **Puntos clave:**
- Para pasar múltiples parámetros, especificamos `"details/{nombre}/{edad}"` en la ruta.
- Usamos `navArgument` para definir el tipo de cada parámetro.


