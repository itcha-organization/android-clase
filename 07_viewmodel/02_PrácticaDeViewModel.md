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

## Usar ViewModel en funciones Composable

```kotlin
@Composable
fun PrimeraPantalla(
    viewModel: VistaCompartidaViewModel = viewModel(),
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
    viewModel: VistaCompartidaViewModel = viewModel(),
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
fun NavManager() {
    val navController = rememberNavController()

    NavHost(navController = navController, startDestination = "primera") {
        composable(route = "primera") {
            PrimeraPantalla(navController = navController)
        }
        composable(
            route = "segunda",
        ) {
            SegundaPantalla(navController = navController)
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
+                NavManager()
            }
        }
    }
}
```
