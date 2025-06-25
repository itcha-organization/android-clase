# Utilice Retrofit para consumir las API de creación y actualización.

# Implementar función de Agregar nuevo producto

## 1. Crear método en la interface `ApiProduct`
```kotlin
// Método para registrar un nuevo producto
@POST(ENDPOINT)
suspend fun createProduct(@Body product: ProductModel): Response<ProductModel>
```

## 2. Programar método en el repositorio `ProductRepository`
```kotlin
suspend fun createProduct(product: ProductModel): ProductModel? {
    val response = apiProduct.createProduct(product)
    if (response.isSuccessful) {
        return response.body()
    }
    Log.e("ProductRepository", "Error createProduct: ${response.code()}")
    return null
}
```

## 3. Crear método en `ProductViewModel`
```kotlin
fun createProduct(product: ProductModel) {
    viewModelScope.launch {
        withContext(Dispatchers.IO) {
            // Intentar crear el nuevo producto llamando al repositorio
            val result = repository.createProduct(product)
            if (result != null) {
                // Actualizar el estado del ViewModel si la creación fue exitosa
                val updatedList = _products.value.toMutableList().apply {
                    add(product)  // Agregamos el nuevo producto a la lista
                }
                _products.value = updatedList  // Emitimos la nueva lista
                state = state.copy(successMessage = "Producto creado con éxito")
            } else {
                state = state.copy(errorMessage = "Error al crear el producto")
            }
        }
    }
}
```

## 4. Crear archivo `AddProductView` en el paquete `components` y pegar los siguiente código
```kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun AddView(navController: NavController, viewModel: ProductViewModel){
    Scaffold(
        topBar = {
            CenterAlignedTopAppBar(title = {
                Text(text = "Agregar Producto", color = Color.White,fontWeight = FontWeight.Bold) },
                colors = TopAppBarDefaults.centerAlignedTopAppBarColors(
                    containerColor = MaterialTheme.colorScheme.primary
                ),
                navigationIcon = {
                    IconButton(onClick = { navController.popBackStack()}) {
                        Icon(imageVector = Icons.AutoMirrored.Filled.ArrowBack, contentDescription = "Back", tint = Color.White)
                    }
                }
            )
        }
    ) {
        RegisterProductScreen(it, navController, viewModel)
    }
}

@Composable
fun RegisterProductScreen(
    paddingValues: PaddingValues, navController: NavController, viewModel: ProductViewModel
) {
    var title by remember { mutableStateOf("") }
    var price by remember { mutableStateOf("") }
    var description by remember { mutableStateOf("") }
    var category by remember { mutableStateOf("") }
    var rating by remember { mutableFloatStateOf(0f) }
    var imageUri by remember { mutableStateOf<Uri?>(null) }
    val context = LocalContext.current

    // Launcher para seleccionar la imagen de la galería
    val galleryLauncher = rememberLauncherForActivityResult(
        contract = ActivityResultContracts.GetContent(),
        onResult = { uri: Uri? ->
            imageUri = uri
        }
    )

    // Launcher para solicitar el permiso
    val permissionLauncher = rememberLauncherForActivityResult(
        contract = ActivityResultContracts.RequestPermission(),
        onResult = { isGranted: Boolean ->
            if (isGranted) {
                // Permiso concedido, lanzar la galería
                galleryLauncher.launch("image/*")
            } else {
                // Permiso denegado
                Toast.makeText(context, "Permiso denegado", Toast.LENGTH_SHORT).show()
            }
        }
    )

    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(paddingValues)
            .padding(top = 30.dp),
        verticalArrangement = Arrangement.spacedBy(8.dp),
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        TextField(
            value = title,
            onValueChange = { title = it },
            label = { Text("Title") },
            modifier = Modifier.fillMaxWidth()
                .padding(horizontal = 16.dp)
                .padding(top = 8.dp)
        )
        TextField(
            value = price,
            onValueChange = { price = it },
            label = { Text("Price") },
            modifier = Modifier.fillMaxWidth()
                .padding(horizontal = 16.dp)
                .padding(top = 8.dp),
            keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Number)
        )
        TextField(
            value = description,
            onValueChange = { description = it },
            label = { Text("Description") },
            modifier = Modifier.fillMaxWidth()
                .padding(horizontal = 16.dp)
                .padding(top = 8.dp)
        )
        TextField(
            value = category,
            onValueChange = { category = it },
            label = { Text("Category") },
            modifier = Modifier.fillMaxWidth()
                .padding(horizontal = 16.dp)
                .padding(top = 8.dp),
            maxLines = 3,
            singleLine = false
        )
        Column {
            Text(text = "Calificación: ${rating.toInt()} Estrellas",
                modifier = Modifier.fillMaxWidth()
                    .padding(horizontal = 16.dp)
            )
            Slider(
                value = rating,
                onValueChange = { newRating -> rating = newRating },
                valueRange = 0f..5f,  // Rango del rating de 0 a 5
                steps = 4,  // Cantidad de pasos, para permitir medias estrellas
                modifier = Modifier.padding(horizontal = 16.dp)
            )
        }

        imageUri?.let {
            Image(
                painter = rememberAsyncImagePainter(it),
                contentDescription = null,
                modifier = Modifier
                    .size(200.dp)
                    .clip(RoundedCornerShape(8.dp))
                    .background(Color.Gray),
                contentScale = ContentScale.Crop
            )
        }

        Button(
            onClick = {
                // Verificar versión de Android y solicitar permiso adecuado
                if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {
                    permissionLauncher.launch(Manifest.permission.READ_MEDIA_IMAGES)
                } else {
                    // Para versiones anteriores a Android 13
                    permissionLauncher.launch(Manifest.permission.READ_EXTERNAL_STORAGE)
                }
            }
        ) {
            Text("Seleccionar Imagen")
        }

        Button(
            onClick = {
                if (title.isNotEmpty() && price.isNotEmpty() && description.isNotEmpty() && category.isNotEmpty() && imageUri != null) {
                    // Convertir el precio a Double
                    val priceValue = price.toDoubleOrNull() ?: 0.0

                    // Crear el nuevo producto
                    val newProduct = ProductModel(
                        id = 0,
                        title = title,
                        price = priceValue,
                        description = description,
                        category = category,
                        image = imageUri.toString(), // Guardamos la URI de la imagen seleccionada
                        rating = Rating(rating.toDouble(), 0)
                    )
                    // Registrar el producto
                    viewModel.createProduct(newProduct)

                    Toast.makeText(context, "Producto registrado", Toast.LENGTH_SHORT).show()
                    navController.popBackStack()
                } else {
                    Toast.makeText(context, "Completa todos los campos", Toast.LENGTH_SHORT).show()
                }
            }
        ) {
            Text("Registrar Producto")
        }
    }
}
```

### 5. Crear la ruta de navegación en `NavManager`
```kotlin
composable("agregar"){
   AddView(navController, viewModel)
}
```

### 6. Habilitar permisos para utilizar la galeria de imágenes del dispositivo en el archivo AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.READ_MEDIA_IMAGES" /> <!-- ★Agregar -->
```
