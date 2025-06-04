# Consumir APIs con Retrofit

Retrofit es una potente librería de Android para realizar solicitudes HTTP de forma sencilla y eficiente. Permite interactuar con APIs REST y procesar sus respuestas de manera automática, convirtiéndolas en objetos Kotlin. En aplicaciones que usan Jetpack Compose, Retrofit es una excelente opción para manejar datos de servidores y mostrarlos en las interfaces modernas y reactivas que Compose ofrece.

Para este ejemplo vamos a consumir [Fake Store API](https://fakestoreapi.com/), que esta en linea y se puede usar para propósitos de aprendizaje.

# Pasos para consumir APIs con Retrofit

## Preparación Previa: Creación de una aplicación sin llamada al API

Crear un Proyecto `ProductsApiApp`

Necesita agregar dependencias. Añade siguiente codigo en tu archivo `build.gradle.kts (:app)`.

```kotlin
dependencies {
    ...Arriba omitido...
    // ViewModel
    implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.9.0")
    // Navigation
    implementation("androidx.navigation:navigation-compose:2.9.0")
}
```
Haga clic en `Sync Now` para sincronizar.
![image](https://github.com/user-attachments/assets/79dcefdd-b5c2-49d2-ac7a-020075ea255e)

Crear un paquete `components` bajo `ui`.

Crear archivos `RatingBar`, `MainTopBar`, `HomeView`, `DetailView` en el paquete `components` y pegar los siguiente código.
- RatingBar
```kotlin
@Composable
fun RatingBar(rating: Double) {
    Row(
        verticalAlignment = Alignment.CenterVertically,
        horizontalArrangement = Arrangement.Start,
        modifier = Modifier.padding(horizontal = 8.dp)
    ) {
        // Mostrar estrellas según el rating (entre 0 y 5)
        repeat(5) { index ->
            Icon(
                imageVector = Icons.Default.Star,
                contentDescription = null,
                tint = if (index < rating.toInt()) Color.Blue else Color.Gray,
                modifier = Modifier.size(20.dp)
            )
        }
        Spacer(modifier = Modifier.width(8.dp))
        Text(text = String.format("%.1f", rating))
    }
}
```
- MainTopBar
```kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun MainTopBar(
    title: String,
    showBackButton: Boolean = false,
    onCickBackButton: () -> Unit,
    onCickAction: () -> Unit
) {
    TopAppBar(
        title = { Text(text = title, color = Color.White, fontWeight = FontWeight.ExtraBold) },
        colors = TopAppBarDefaults.centerAlignedTopAppBarColors(
            containerColor = MaterialTheme.colorScheme.primary
        ),
        navigationIcon = {
            if (showBackButton) {
                IconButton(onClick = { onCickBackButton() }) {
                    Icon(
                        imageVector = Icons.AutoMirrored.Filled.ArrowBack,
                        contentDescription = "Back",
                        tint = Color.White
                    )
                }
            }
        },
        actions = {
            if (!showBackButton) {
                IconButton(onClick = { onCickAction() }) {
                    Icon(
                        imageVector = Icons.Default.Search,
                        contentDescription = "Search",
                        tint = Color.White
                    )
                }
            }
        }
    )
}
```
- HomeView
```kotlin
@Composable
fun HomeView(viewModel: ProductViewModel, navController: NavController) {
    Scaffold(
        topBar = {
            MainTopBar(
                title = "API Products",
                onCickBackButton = { },
                onCickAction = { }
            )
        },
        floatingActionButton = {
            FloatingActionButton(
                onClick = { navController.navigate("agregar") },
                containerColor = MaterialTheme.colorScheme.primary,
                contentColor = Color.White
            ) {
                Icon(imageVector = Icons.Default.Add, contentDescription = "Agregar")
            }
        }
    ) {
        ContentHomeView(viewModel, it, navController)
    }
}

@Composable
fun ContentHomeView(
    viewModel: ProductViewModel,
    paddingValues: PaddingValues,
    navController: NavController
) {
    val products = viewModel.products

    Column(
        modifier = Modifier.padding(paddingValues),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        LazyColumn() {
            items(products) { product ->
                Card(
                    shape = RoundedCornerShape(8.dp),
                    modifier = Modifier
                        .fillMaxWidth()
                        .padding(10.dp)
                        .shadow(elevation = 10.dp)
                        .clickable { navController.navigate("DetailView/0") }
                ) {
                    Column(
                        modifier = Modifier
                            .fillMaxWidth()
                            .padding(8.dp)
                    ) {
                        // Imagen del producto
                        Image(
                            painter = painterResource(id = R.drawable.star_on),
                            contentDescription = null,
                            contentScale = ContentScale.Fit, // Para evitar que la imagen se corte
                            modifier = Modifier
                                .fillMaxWidth()
                                .height(250.dp)
                                .padding(8.dp)
                        )

                        // Detalles del producto
                        Text(
                            text = product,
                            style = MaterialTheme.typography.titleLarge,
                            modifier = Modifier.padding(horizontal = 8.dp)
                        )
                        Text(
                            text = "$${product.length}",
                            fontWeight = FontWeight.ExtraBold,
                            style = MaterialTheme.typography.titleMedium.copy(color = Color.Black),
                            modifier = Modifier.padding(horizontal = 8.dp),
                        )
                        RatingBar(rating = 1.0)

                        // Botones de Editar y Eliminar
                        Row(
                            horizontalArrangement = Arrangement.SpaceBetween,
                            modifier = Modifier
                                .fillMaxWidth()
                                .padding(horizontal = 8.dp)
                        ) {
                            IconButton(onClick = { }) {
                                Icon(
                                    imageVector = Icons.Default.Edit,
                                    contentDescription = "Editar",
                                    tint = Color.White
                                )
                            }
                            IconButton(onClick = { }) {
                                Icon(
                                    imageVector = Icons.Default.Delete,
                                    contentDescription = "Eliminar",
                                    tint = Color.Red
                                )
                            }
                        }
                    }
                }
            }
        }
    }
}
```
- DetailView
```kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun DetailView(viewModel: ProductViewModel, navController: NavController, id: Int) {
    Scaffold(
        topBar = {
            MainTopBar(
                title = "Product Detail",
                showBackButton = true,
                onCickBackButton = { navController.popBackStack() },
                onCickAction = {}
            )
        }
    ) {
        ContentDetailView(it, viewModel)
    }
}

@Composable
fun ContentDetailView(padd: PaddingValues, viewModel: ProductViewModel) {
    Column(
        modifier = Modifier
            .padding(padd)
    ) {
        Image(
            painter = painterResource(id = R.drawable.star_on),
            contentDescription = null,
            contentScale = ContentScale.Fit, // Para evitar que la imagen se corte
            modifier = Modifier
                .fillMaxWidth()
                .height(250.dp)
                .padding(8.dp)
        )
        Row(
            horizontalArrangement = Arrangement.Center,
            modifier = Modifier.fillMaxWidth()
        ) {
            Text(text = "Price: ", color = Color.Green, style = MaterialTheme.typography.titleLarge)
            Text(
                text = "1",
                color = Color.Green,
                style = MaterialTheme.typography.titleLarge
            )
        }

        //creando el text para la descripcion del producto
        Column(modifier = Modifier.fillMaxWidth()) {
            Text(
                text = "Description",
                color = Color.Red,
                style = MaterialTheme.typography.bodyLarge,
                modifier = Modifier.padding(start = 15.dp),
            )
            Text(
                text = "description producto",
                color = Color.White,
                textAlign = TextAlign.Justify,
                modifier = Modifier.padding(start = 15.dp, end = 15.dp, bottom = 10.dp)
            )
        }
        Row(
            horizontalArrangement = Arrangement.SpaceBetween,
            verticalAlignment = Alignment.CenterVertically,
            modifier = Modifier
                .fillMaxWidth()
                .padding(start = 20.dp, end = 10.dp, bottom = 10.dp)
        ) {
            RatingBar(rating = 1.0)
            Text(
                text = "Cat: category producto",
                color = Color.Green,
                style = MaterialTheme.typography.bodyLarge
            )
        }
    }
}
```

Crear archivos `NavManager`, `ProductViewModel` en el paquete `ui` y pegar los siguiente código.
- NavManager
```kotlin
@Composable
fun NavManager(viewModel: ProductViewModel) {
    val navController = rememberNavController()
    NavHost(navController = navController, startDestination = "Home") {
        composable("Home") {
            HomeView(viewModel, navController)
        }
        composable(
            "DetailView/{id}", arguments = listOf(
            navArgument("id") { type = NavType.IntType }
        )) {
            val id = it.arguments?.getInt("id") ?: 0
            DetailView(viewModel, navController, id)
        }
    }
}
```
- ProductViewModel
```kotlin
class ProductViewModel() : ViewModel() {

    // Lista de productos
    val products = listOf<String>("Producto 1", "Producto 2", "Producto 3")
}
```

En `MainActivity`, sustituye el código del bloque `ProductsApiAppTheme` por el siguiente código.
```kotlin
Surface(
    modifier = Modifier.fillMaxSize(),
    color = MaterialTheme.colorScheme.background
)
{
    val productViewModel: ProductViewModel = viewModel()
    NavManager(productViewModel)
}
```
