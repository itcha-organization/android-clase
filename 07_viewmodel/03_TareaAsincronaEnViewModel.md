# Tarea Asincrona En ViewModel

## Kotlin Coroutines

**Kotlin Coroutines** es una librería oficial de Kotlin para manejar tareas asíncronas.

### Características principales:
1. **Escritura sencilla de procesamiento asíncrono**: Permite escribir código asíncrono de manera secuencial, sin necesidad de callbacks o manejo directo de hilos.
2. **Fácil manejo de tareas asíncronas**: Usando funciones `suspend`, puedes escribir tareas asíncronas como funciones normales.

### Elementos básicos:
- **Funciones `suspend`**: Funciones que realizan tareas asíncronas.
- **`launch`**: Método para iniciar coroutines(tareas asíncronas).

### Ejemplo:

La función de `delay`, que suspende el procesamiento durante un número de segundos dado como argumento, se utiliza para simular un procesamiento que requiere mucho tiempo.
<br>El proceso se interrumpe durante 1 segundo por `delay`, por lo que 3 sale antes que 2.

https://pl.kotl.in/aedeR4JQu

```kotlin
import kotlinx.coroutines.*

fun main() {
    runBlocking {
        launch {
            println("1")
            delay(1000L)
            println("2")
        }
        launch {
            println("3")
        }
    }
}
```

## Realización de tareas asíncronas en ViewModel

### Repaso: Pantallas simples usando ViewModel.

#### 0. Crea un nuevo proyecto llamado `EjemploAsincrona`.
Crea un nuevo proyecto. Una vez compilado, elimina la función por defecto `Greeting` y su punto de llamada en la `MainActivity`.

#### 1. **Agregar dependencias de ViewModel al proyecto**  
Primero, necesitas agregar la biblioteca para utilizar `ViewModel`. Añade lo siguiente a las dependencias en tu archivo `build.gradle.kts` (:app).

```diff
dependencies {
    ...

+    implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.6.1")
}
```

#### 2. **Crear la clase ViewModel**  
A continuación, crea una clase `ViewModel` para mantener los datos necesarios.

```kotlin
// Clase ViewModel
class CargarDatoViewModel : ViewModel() {
    // Mantener el estado del contador
    var contador by mutableStateOf(0)
        private set

    // Función para incrementar el contador
    fun incrementarContador() {
        contador++
    }
}
```
#### Explicación:
- Se crea la clase `ViewModel` y se define la variable entera `contador` utilizando `mutableStateOf`. Esto permite que Compose redibuje la interfaz automáticamente.
- La función `incrementarContador()` incrementa el valor de `contador`.

### 3. **Usar ViewModel en una función Composable**  
Ahora, utiliza `ViewModel` dentro de una función `Composable`. Se puede obtener una instancia del `ViewModel` usando la función `viewModel()`.
```kotlin
// Utilizar ViewModel dentro de una función Composable.
// Se puede obtener una instancia del ViewModel usando la función viewModel()
@Composable
fun PantallaContador(viewModel: ContadorViewModel = viewModel()) {
    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(16.dp),
        horizontalAlignment = Alignment.CenterHorizontally,
        verticalArrangement = Arrangement.Center
    ) {
        // Mostrar el valor del contador
        Text(text = "Contador: ${viewModel.contador}", fontSize = 32.sp)
        Spacer(modifier = Modifier.height(16.dp))

        // Botón para incrementar el contador
        Button(onClick = { viewModel.incrementarContador() }) {
            Text(text = "Incrementar Contador")
        }
    }
}
```
#### Explicación:
- Se usa `viewModel()` para obtener una instancia de `ContadorViewModel`.
- La función `Text` muestra el valor de `viewModel.contador` y el botón llama a `incrementarContador()` para incrementar el contador.
- Al usar la función `viewModel()` en Compose, el estado se mantiene incluso cuando se producen eventos como la rotación de la pantalla o el redibujado.

### 4. **Mostrar la función Composable que usa ViewModel en la aplicación**  
Finalmente, incluye la función `PantallaContador` en la actividad o en otras funciones `Composable` para mostrarla en la aplicación.
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            EjemploViewModelTheme {
                PantallaContador()
            }
        }
    }
}
```
#### Explicación:
- Dentro de la clase `MainActivity`, se utiliza `setContent` para mostrar `PantallaContador`.
- Argumento por defecto `PantallaContador`, establecido para asignar el valor de retorno del método `viewModel()`. Por lo tanto, el constructor puede ser llamado sin argumentos.

### Resumen

- **Creación de ViewModel**: Se crea una clase `ViewModel` y se definen las variables de estado y funciones para operar sobre ellas.
- **Uso de ViewModel en Composable**: Se utiliza la función `viewModel()` para aprovechar el `ViewModel` dentro de las funciones `Composable`.
- **Retención de estado**: Usando `ViewModel`, el estado se mantiene incluso durante eventos del ciclo de vida como la rotación de la pantalla o redibujos.
