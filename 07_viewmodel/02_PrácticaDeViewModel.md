# ViewModel en la práctica

## Creación de paquetes y archivos.

- Crear los paquetes `components`, `navigation` y `viewmodels`.
- Crear los archivos `PrimeraPantalla` y `SegundaPantalla` en el paquete `components`.
- Crear los archivos `NavManager` en el paquete `navigation`.
- Crear los archivos `VistaCompartidaViewModel` en el paquete `viewmodels`.

![image](https://github.com/user-attachments/assets/1b91006c-35ef-486d-aa86-6fc10fca7ce7)

## Crear la clase ViewModel

```kotlin
class VistaCompartidaViewModel : ViewModel() {

    var textos by mutableStateOf(listOf<String>())
        private set

    fun addTexto(nuevoTexto: String) {
        textos = textos + nuevoTexto
    }
}
```
Este código es un ejemplo simple de cómo usar `ViewModel` en Jetpack Compose para gestionar una lista de datos (una lista de cadenas de texto) y agregar nuevos datos. Aquí se explica cada parte en detalle.

### Definición de la clase: `VistaCompartidaViewModel`
```kotlin
class VistaCompartidaViewModel : ViewModel() {
```
- **`VistaCompartidaViewModel`**: Esta clase hereda de `ViewModel`. El `ViewModel` mantiene el estado de la pantalla y evita que se pierda durante eventos del ciclo de vida, como la rotación de la pantalla o la recreación de la interfaz de usuario. En este caso, esta clase mantiene una lista de cadenas de texto (`textos`).

### Variable: `textos`
```kotlin
    var textos by mutableStateOf(listOf<String>())
        private set
```

- **`var textos`**: Esta es una variable que almacena una lista de cadenas de texto (`List<String>`) y contiene los datos de texto que se muestran en la UI. La variable `textos` se define usando **MutableState**.
- **`by mutableStateOf`**: `mutableStateOf` permite que Compose detecte los cambios en la variable `textos` y redibuje automáticamente la UI cuando su valor cambie. Aquí, `textos` se inicializa como una lista vacía (`listOf<String>()`).
- **`private set`**: El modificador `private set` hace que la variable solo pueda ser modificada dentro del `ViewModel`, evitando que el estado se modifique directamente desde fuera de la clase. Esto asegura que la gestión del estado sea segura y controlada.

### Método: `addTexto`
```kotlin
    fun addTexto(nuevoTexto: String) {
        textos = textos + nuevoTexto
    }
```

- **`addTexto`**: Esta función toma como parámetro un nuevo texto (`nuevoTexto`) y lo agrega a la lista `textos`.
- **`textos = textos + nuevoTexto`**: En Kotlin, el operador `+` se puede usar para añadir elementos a una lista. En este caso, `nuevoTexto` se añade a la lista `textos` existente, creando una nueva lista con el valor añadido. Aunque las listas en Kotlin son inmutables, se está generando una nueva lista y asignándola a `textos`.

### Flujo general

1. La clase `VistaCompartidaViewModel` hereda de `ViewModel` para mantener el estado de la pantalla.
2. La variable `textos` contiene una lista de cadenas de texto. Al usar `mutableStateOf`, Compose puede redibujar la UI automáticamente cuando se cambia esta lista.
3. Aunque `textos` no se puede modificar directamente desde fuera del `ViewModel`, la función `addTexto` permite agregar nuevos textos a la lista de manera controlada.

### Ejemplo de uso

Este `ViewModel` puede ser utilizado en una aplicación que gestione mensajes o notas. Cada vez que un usuario introduce un nuevo texto, se agrega a la lista usando `addTexto`, y la UI se actualiza automáticamente para reflejar el nuevo contenido.

### Resumen

- El uso de `ViewModel` permite gestionar de manera eficiente el estado de la UI en Compose, asegurando que los datos se mantengan incluso durante la rotación de pantalla o la recreación de la interfaz.
- La variable `textos` es inmutable desde fuera del `ViewModel`, lo que garantiza una gestión segura del estado.
- La función `addTexto` permite agregar nuevos textos a la lista de manera controlada, asegurando que la UI se actualice automáticamente cuando los datos cambian.


## Usar ViewModel en funciones Composable

```kotlin
@Composable
fun PrimeraPantalla(
    viewModel: VistaCompartidaViewModel,
    navController: NavController
) {
    Column(
        horizontalAlignment = Alignment.CenterHorizontally,
        modifier = Modifier
            .fillMaxSize()
            .padding(top = 48.dp)
    ) {
        var texto by remember{ mutableStateOf("") }

        Text(text = "Primera Pantalla", fontSize = 20.sp)
        Row(
            modifier = Modifier.padding(horizontal = 8.dp)
        ) {
            OutlinedTextField(
                value = texto,
                onValueChange = { texto = it },
                label = { Text("Introduce Texto Nuevo") },
                colors = OutlinedTextFieldDefaults.colors(
                    focusedTextColor = Color.Black,
                    unfocusedTextColor = Color.Black,
                )
            )
            OutlinedButton(
                onClick = {
                    viewModel.addTexto(texto)
                    texto = ""
                },
                modifier = Modifier.padding(8.dp),
                enabled = texto.isNotBlank()
            ) {
                Text("Añadir")
            }
        }

        OutlinedButton(
            onClick = { navController.navigate("segunda") }
        ) {
            Text("Navegar a la Segunda")
        }
        HorizontalDivider(thickness = 4.dp, color = Color.Black)
        LazyColumn {
            items(viewModel.textos) { texto: String ->
                Text(texto, fontSize = 20.sp)
            }
        }
    }
}
```

```kotlin
@Composable
fun SegundaPantalla(
    viewModel: VistaCompartidaViewModel,
    navController: NavController
) {
    Column(
        horizontalAlignment = Alignment.CenterHorizontally,
        modifier = Modifier
            .fillMaxSize()
            .padding(top = 48.dp)
    ) {
        var texto by remember{ mutableStateOf("") }

        Text(text = "Segunda Pantalla", fontSize = 20.sp)
        Row(
            modifier = Modifier.padding(horizontal = 8.dp)
        ) {
            OutlinedTextField(
                value = texto,
                onValueChange = { texto = it },
                label = { Text("Introduce Texto Nuevo") },
                colors = OutlinedTextFieldDefaults.colors(
                    focusedTextColor = Color.Black,
                    unfocusedTextColor = Color.Black,
                )
            )
            OutlinedButton(
                onClick = {
                    viewModel.addTexto(texto)
                    texto = ""
                },
                modifier = Modifier.padding(8.dp),
                enabled = texto.isNotBlank()
            ) {
                Text("Añadir")
            }
        }

        OutlinedButton(
            onClick = { navController.navigate("primera") }
        ) {
            Text("Navegar a la Primera")
        }
        HorizontalDivider(thickness = 4.dp, color = Color.Black)
        LazyColumn {
            items(viewModel.textos) { texto: String ->
                Text(text = texto)
            }
        }
    }
}
```

## Configurar la navegación para mostrar las funciones Composable que usa ViewModel en la aplicación

```kotlin
@Composable
fun NavManager(viewModel: VistaCompartidaViewModel) {
    val navController = rememberNavController()

    NavHost(navController = navController, startDestination = "primera") {
        composable(route = "primera") {
            PrimeraPantalla(viewModel, navController)
        }
        composable(
            route = "segunda",
        ) {
            SegundaPantalla(viewModel, navController)
        }
    }
}
```

```diff
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            ViewModelSampleTheme {
+                val viewModel: VistaCompartidaViewModel = viewModel()
+                NavManager(viewModel)
            }
        }
    }
}
```
