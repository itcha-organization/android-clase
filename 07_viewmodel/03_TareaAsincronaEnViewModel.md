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

もちろん、スペイン語に翻訳した教材を作成します！以下がスペイン語での説明です。

---

## 🎯 Objetivo

- Ejecutar tareas pesadas (como solicitudes de red o acceso a base de datos) de manera asincrónica en el `ViewModel` sin bloquear el hilo principal (UI).
- Gestionar el estado y notificar a la UI cuando cambie.

---

## 🪜 Pasos (5 pasos)

---

### ✅ Paso 1: Configurar el entorno de Coroutines en `ViewModel`

`ViewModel` ya tiene `viewModelScope` listo para usar, lo cual permite lanzar corutinas de manera segura.

```kotlin
import androidx.lifecycle.ViewModel
import androidx.lifecycle.viewModelScope
import kotlinx.coroutines.launch
```

---

### ✅ Paso 2: Hacer las funciones de procesamiento asincrónico `suspend`

Funciones como `delay()` o las que involucran solicitudes de red deben ser declaradas como `suspend` para que puedan ejecutarse de manera asincrónica.

```kotlin
suspend fun cargarDatos(): String {
    delay(2000) // Espera de 2 segundos
    return "Datos cargados"
}
```

---

### ✅ Paso 3: Llamar la función `suspend` en `launch`

Como las funciones `suspend` no se pueden ejecutar directamente en un hilo normal, usaremos `viewModelScope.launch {}` para ejecutarlas dentro del `ViewModel`.

```kotlin
fun obtenerDatos() {
    viewModelScope.launch {
        val resultado = cargarDatos()
        // Actualizar el estado para mostrarlo en la UI
    }
}
```

---

### ✅ Paso 4: Usar `withContext` para cambiar de hilo si es necesario

Si la tarea requiere cambiar de hilo, por ejemplo para acceso a red o a base de datos, usaremos `withContext` con el `Dispatchers.IO`.

```kotlin
import kotlinx.coroutines.Dispatchers
import kotlinx.coroutines.withContext

fun obtenerDatos() {
    viewModelScope.launch {
        val resultado = withContext(Dispatchers.IO) {
            cargarDatos()
        }
    }
}
```

---

### ✅ Paso 5: Notificar el estado a la UI con `StateFlow`

Usamos `MutableStateFlow` para manejar el estado (como el mensaje que se muestra en la UI), y lo exponemos como `StateFlow` para que sea solo de lectura.

```kotlin
import kotlinx.coroutines.flow.MutableStateFlow
import kotlinx.coroutines.flow.StateFlow

private val _mensaje = MutableStateFlow("Estado inicial")
val mensaje: StateFlow<String> = _mensaje

fun obtenerDatos() {
    viewModelScope.launch {
        _mensaje.value = "Cargando..."

        val resultado = withContext(Dispatchers.IO) {
            cargarDatos()
        }

        _mensaje.value = resultado
    }
}
```

---

## 📦 Código completo del `ViewModel`

```kotlin
class MiViewModel : ViewModel() {

    private val _mensaje = MutableStateFlow("Estado inicial")
    val mensaje: StateFlow<String> = _mensaje

    fun obtenerDatos() {
        viewModelScope.launch {
            _mensaje.value = "Cargando..."

            val resultado = withContext(Dispatchers.IO) {
                delay(2000) // Simulamos una tarea pesada
                "¡Datos cargados!"
            }

            _mensaje.value = resultado
        }
    }
}
```

---

## 💡 Uso en la UI (Jetpack Compose)

```kotlin
val viewModel: MiViewModel = viewModel()
val mensaje by viewModel.mensaje.collectAsState()

Text(text = mensaje)
Button(onClick = { viewModel.obtenerDatos() }) {
    Text("Obtener datos")
}
```

---

## ✅ Resumen

| Elemento                        | Descripción |
|----------------------------------|-------------|
| `viewModelScope.launch`          | Lanza una corutina (dentro del ciclo de vida del `ViewModel`) |
| Función `suspend`                | Define tareas asincrónicas, puede usar `delay()` o procesos que no bloquean el hilo principal |
| `withContext(Dispatchers.IO)`    | Ejecuta tareas en un hilo de entrada/salida (para redes, bases de datos) |
| `MutableStateFlow` / `StateFlow` | Gestiona el estado de manera reactiva, manteniendo los datos actualizados para la UI |
| `collectAsState()`               | Suscribe la UI a un `Flow` para observar cambios en los datos |
