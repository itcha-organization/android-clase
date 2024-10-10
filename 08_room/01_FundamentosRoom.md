# Room

Room es una biblioteca de persistencias. Es una capa de abstracción que se ubica sobre una base de datos SQLite.En lugar de usar SQLite directamente, Room simplifica las tareas de configuración de la base de datos, así como las interacciones con la app. 

## Componentes principales de Room
Room está compuesto por tres componentes clave:

1. **Entidad (Entity)**: Es una clase que define una tabla en la base de datos. Cada instancia representa una fila dentro de la tabla de la base de datos.

2. **DAO (Objeto de Acceso a Datos)**: Es una interfaz que define las operaciones de acceso a la base de datos. Aquí se definen los métodos para leer y escribir datos.

3. **Base de Datos (Database)**: Es la clase principal que crea la base de datos y proporciona acceso a los DAOs.

## Pasos para implementar app con Room

Existen varios protocolos para crear aplicaciones vinculadas a bases de datos utilizando Room.
Revise el procedimiento mientras crea una aplicación que almacena una lista de usuarios en una base de datos.

![image](https://github.com/user-attachments/assets/0d3df638-56f9-481d-bf7c-53ae84891457)

### 0. **Crear un Proyecto `EjemploRoom`**

### 1. **Agregar plug-in y dependencias**

Primero, necesitas agregar plug-in.
Abre `libs.versions.toml` y comprueba que la versión de kotlin es `1.9.0`.

![image](https://github.com/user-attachments/assets/56dade67-21e5-4f0f-a154-1851146de0ba)

Si la versión de Kotlin es `1.9.0`, añade siguiente codigo en tu archivo `build.gradle.kts` (:app).
```kotlin
plugins {
    ...Arriba omitido...
    id("com.google.devtools.ksp") version "1.9.0-1.0.12"
}
```
<details>
  <summary>Si Kotlin versión es `2.0.0`</summary>

  ```kotlin
  plugins {
      ...Arriba omitido...
      id("com.google.devtools.ksp") version "2.0.20-1.0.24"
  }
  ```
</details>

Haz clic en `Sync Now` para sincronizar.
![image](https://github.com/user-attachments/assets/958888f1-9a14-4cba-b0e5-fae6214b8ff7)

Necesitas agregar dependencias. Añade siguiente codigo en tu archivo build.gradle.kts (:app).
```kotlin
dependencies {
    ...Arriba omitido...
    val room_version = "2.6.1"
    implementation("androidx.room:room-runtime:$room_version")
    ksp("androidx.room:room-compiler:$room_version")
    implementation("androidx.room:room-ktx:$room_version")
}
```
Haz clic en `Sync Now` para sincronizar.
![image](https://github.com/user-attachments/assets/85874ffe-2187-451f-94f1-ba4e9a29018c)

### 2. **Crear Entity**

Utiliza la anotación `@Entity` para definir la tabla de la base de datos. Por ejemplo, para crear una tabla llamada `Usuario`:

```kotlin
import androidx.room.Entity
import androidx.room.PrimaryKey

@Entity(tableName = "tabla_usuario")
data class Usuario(
    @PrimaryKey(autoGenerate = true) val id: Int = 0,
    val nombre: String,
    val edad: Int
)
```
- **`@PrimaryKey(autoGenerate = true)`**
  - Al especificar `autoGenerate = true`, se indica que cuando se crea un nuevo objeto Usuario, este `id` se generará automáticamente. Esto significa que el desarrollador no necesita establecer manualmente el valor de `id`.

### 3. **Crear DAO**

Define los métodos de acceso a la base de datos (CRUD). Por ejemplo, un DAO para insertar y obtener usuarios sería:

```kotlin
import androidx.room.Dao
import androidx.room.Delete
import androidx.room.Insert
import androidx.room.Query
import androidx.room.Update
import kotlinx.coroutines.flow.Flow

@Dao
interface UsuarioDao {
    @Insert
    suspend fun insert(usuario: Usuario)

    @Query("SELECT * FROM tabla_usuario")
    fun getAll(): Flow<List<Usuario>>

    @Delete
    suspend fun delete(usuario: Usuario)

    @Update
    suspend fun update(usuario: Usuario)
}
```
- **`@Dao`**:
  - Indica que esta interfaz es un Data Access Object (DAO).La interfaz `UsuarioDao` define métodos para interactuar con la tabla `tabla_usuario` de la base de datos.
- **`suspend`**:
  - Al utilizar `suspend`, estos métodos pueden ejecutarse de forma asíncrona sin bloquear el hilo principal de la aplicación, mejorando la eficiencia de la aplicación.

- **`Flow<List<Usuario>>`**:
  - **`Flow`** es tipo de la programación reactiva, lo que significa que puede monitorear cambios en los datos y notificarlos cuando estos ocurren.
  - Al devolver un **`Flow`** en el método `getAll()`, puedes obtener actualizaciones en tiempo real de los datos dentro de la tabla `tabla_usuario`. Cada vez que los datos cambien (por ejemplo, si se inserta o elimina un usuario), la lista se actualizará automáticamente

### 4. **Crear clase de Base de Datos**

Extiende la clase `RoomDatabase` y define la base de datos. Se recomienda que esta clase tenga una única instancia en toda la aplicación.

```kotlin
import androidx.room.Database
import androidx.room.RoomDatabase

@Database(entities = [Usuario::class], version = 1, exportSchema = false)
abstract class UsuarioDatabase: RoomDatabase() {
    abstract fun usuarioDao(): UsuarioDao
}
```
- **`entities = [Usuario::class]`**:
  - Aquí se especifica qué **entidades (tablas)** se utilizarán en la base de datos. En este ejemplo, la clase `Usuario` es la entidad. La clase `Usuario` representa una tabla en la base de datos, con cada columna (campo) definida como una propiedad.
  
  - Si quieres especificar varias tablas, puedes añadir más clases en el array `entities`.

- **`version = 1`**:
  - El número de versión de la base de datos. Si en el futuro cambias la estructura de la base de datos (tablas o columnas), deberás actualizar este número de versión. Room usará este número para realizar las migraciones cuando la estructura de la base de datos cambie.

- **`exportSchema = false`**:
  - Especifica si deseas exportar el esquema de la base de datos. Normalmente se pone `true` para que Room exporte el esquema en formato JSON, que suele ser útil en entornos de desarrollo para realizar verificaciones. En este caso, se ha configurado como `false`.

- **`usuarioDao()`**:
  - Este método devuelve una instancia de `UsuarioDao` (Data Access Object). El DAO es la interfaz que realiza las operaciones sobre la base de datos (consultas, inserciones, eliminaciones, etc.). Room genera automáticamente la implementación del DAO basado en este método abstracto.

- **¿Qué es un DAO?**
  - El DAO (Data Access Object) es la interfaz que realiza las operaciones sobre la base de datos (lectura, escritura, etc.). Por ejemplo, puedes definir métodos como `insert()` o `getAll()` en el DAO, y usar estos métodos para interactuar con la base de datos.

### 5. **Conectar con ViewModel**

Room se puede integrar con ViewModel para gestionar correctamente el ciclo de vida de los datos.

```kotlin
import androidx.compose.runtime.getValue
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.setValue
import androidx.lifecycle.ViewModel
import androidx.lifecycle.viewModelScope
import kotlinx.coroutines.flow.collectLatest
import kotlinx.coroutines.launch

class UsuarioViewModel(
    private val dao: UsuarioDao
) : ViewModel() {
    // Estado para gestionar la lista de usuario
    var listaUsuario by mutableStateOf(listOf<Usuario>())

    init {
        viewModelScope.launch {
            //obtenemos el listado de usuarios y lo convertimos a una coleccion
            dao.getAll().collectLatest {
                listaUsuario = it
            }
        }
    }

    fun addUsuario(usuario: Usuario) = viewModelScope.launch {
        dao.insert(usuario)
    }
}
```
- **`viewModelScope.launch{ }`**:
  - Utiliza `viewModelScope.launch{ }` para iniciar un procesamiento asíncrono. Este ámbito está asociado al ciclo de vida del ViewModel, permitiendo así que las corrutinas se ejecuten en función de este ciclo de vida.

- **`dao.getAll().collectLatest`**:
  - obtiene la lista de usuarios de la base de datos y actualiza `listaUsuario` cada vez que se recibe una nueva lista.
  - Al usar `collectLatest`, se optimiza la actualización de datos, manteniendo siempre el estado más reciente.

### 6. **Construir la UI con Jetpack Compose**
Crear una pantalla de registro de usuarios.Los componentes de interfaz de usuario pueden realizar el registro de la base de datos a través de `ViewModel`.

```kotlin
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.fillMaxWidth
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.lazy.LazyColumn
import androidx.compose.foundation.lazy.items
import androidx.compose.foundation.text.KeyboardOptions
import androidx.compose.material3.Button
import androidx.compose.material3.HorizontalDivider
import androidx.compose.material3.OutlinedTextField
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.getValue
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.remember
import androidx.compose.runtime.setValue
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.text.input.KeyboardType
import androidx.compose.ui.unit.dp

@Composable
fun ListaUsuariosView(viewModel: UsuarioViewModel) {
    val usuarios = viewModel.listaUsuario
    var nombre by remember { mutableStateOf("") }
    var edad by remember { mutableStateOf("") }

    Column(
        modifier = Modifier
            .padding(top = 50.dp),
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        //OutlinedTextField para capturar nombre de usuario
        OutlinedTextField(
            value = nombre,
            onValueChange = {nombre = it},
            label = { Text(text = "Usuario") },
            modifier = Modifier
                .fillMaxWidth()
                .padding(horizontal = 8.dp),
        )
        //OutlinedTextField para capturar el edad
        OutlinedTextField(
            value = edad,
            onValueChange = {edad = it},
            label = { Text(text = "Edad") },
            modifier = Modifier
                .fillMaxWidth()
                .padding(horizontal = 8.dp),
            keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Number)
        )
        Button(
            onClick = {
                val usuario = Usuario(nombre = nombre, edad = edad.toInt())
                viewModel.addUsuario(usuario)
                nombre = ""
                edad = ""
            },
            enabled = nombre.isNotBlank() && edad.isNotBlank()
        ) {
            Text(text = "Agregar", color = Color.Blue)
        }
        HorizontalDivider(thickness = 4.dp, color = Color.Blue)
        LazyColumn {
            items(usuarios) { usuario: Usuario ->
                Text(
                    text = "Nombre:${usuario.nombre}, Edad:${usuario.edad}"
                )
                HorizontalDivider(thickness = 1.dp, color = Color.Black)
            }
        }
    }
}
```

### 7. **Construir la UI con Jetpack Compose**
Finalmente, debes crear una instancia de la base de datos, que se usará durante todo el ciclo de vida de la aplicación.
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            EjemploRoomTheme {
                //creamos la variable para definir la db
                val database = Room.databaseBuilder(
                    this,
                    UsuarioDatabase::class.java,
                    "db_usuarios"
                ).build()
                //definimos nuestro dao
                val dao = database.usuarioDao()
                //creamos el viewModel
                val viewModel = UsuarioViewModel(dao)
                ListaUsuariosView(viewModel)
            }
        }
    }
}
```
- **`Room.databaseBuilder()`**:
  - Se utiliza el método `databaseBuilder()` de la clase `Room` para construir una instancia de la base de datos. Esto se hace proporcionando el contexto de la aplicación y la clase de base de datos (en este caso, `UsuarioDatabase::class.java`), que se usará para crear la base de datos.

- **`"db_usuarios"`**:
  - Este es el nombre que se le da a la base de datos, y bajo este nombre se almacenará el archivo de la base de datos en el almacenamiento del dispositivo.

## Visualización del contenido de la BD en las herramientas de AndroidStudio

### Comprobación del contenido de la BD con `AppInspection`.

Se puede utilizar `AppInspection` para comprobar los datos almacenados en la BD.

![image](https://github.com/user-attachments/assets/55401840-2f75-445f-9485-89d2b78becfd)

Active `Actualizaciones en directo` para observar las actualizaciones de datos en tiempo real.

![image](https://github.com/user-attachments/assets/175a7cd1-2cc8-465c-bd31-907e38c4afa5)

## Añadir funcionalidad a la aplicación

### Uso de componentes `Card` para mejorar el diseño

Utilice el componente `Card` para mejorar el diseño de los elementos de la lista de la siguiente manera.

![image](https://github.com/user-attachments/assets/41badd90-8d46-4361-af24-e1ca16beee9b)

Abre `ListaUsuariosView` y cambia el código del componente UI en el bloque del método `items` de la `LazyColumn` como sigue.

```kotlin
LazyColumn {
    items(usuarios) { usuario: Usuario ->
        Card(
            modifier = Modifier
                .padding(8.dp)
                .fillMaxWidth()
        ) {
            Column(
                modifier = Modifier.padding(8.dp)
            ) {
                Text(text = "Nombre: ${usuario.nombre}", fontWeight = FontWeight.Bold)
                Text(text = "Edad: ${usuario.edad}")
            }
        }

    }
}
```

### Añade una función de borrado.

Añade un botón con el icono de eliminar como se muestra en el diagrama de abajo.

![image](https://github.com/user-attachments/assets/001db441-d240-4652-bf36-365d7a48083a)

Añade `Row` e `IconButton` a `ListaUsuariosView`.

```diff
LazyColumn {
    items(usuarios) { usuario: Usuario ->
        Card(
            modifier = Modifier
                .padding(8.dp)
                .fillMaxWidth()
        ) {
+            Row(
+                modifier = Modifier.fillMaxWidth(),
+                horizontalArrangement = Arrangement.SpaceBetween
+            ){
                Column(
                    modifier = Modifier.padding(8.dp)
                ) {
                    Text(text = "Nombre: ${usuario.nombre}", fontWeight = FontWeight.Bold)
                    Text(text = "Edad: ${usuario.edad}")
                }
+                IconButton(
+                    onClick = { viewModel.deleteUsuario(usuario) }
+                ) {
+                    Icon(
+                        imageVector = Icons.Default.Delete,
+                        contentDescription = "delete"
+                    )
+                }
            }
        }
    }
}
```

Añade un método al `UsuarioViewModel` para acceder al método de borrado del DAO.

```kotlin
// delete
fun deleteUsuario(usuario: Usuario) = viewModelScope.launch {
    dao.delete(usuario)
}
```
