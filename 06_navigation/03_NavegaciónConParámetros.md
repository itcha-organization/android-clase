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

### **Puntos clave:**
- `"details/{itemName}"` indica que `{itemName}` es un parámetro que se pasará a la pantalla.
- `navArgument("itemName") { type = NavType.StringType }` especifica que `itemName` es de tipo cadena (`String`).
- Durante la navegación, se pasa el parámetro utilizando `navController.navigate("details/Apple")`.

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
- Para pasar múltiples parámetros, especificamos `"profile/{userName}/{userId}"` en la ruta.
- Usamos `navArgument` para definir el tipo de cada parámetro.
