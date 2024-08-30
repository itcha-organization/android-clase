# Práctica de componentes básicos.

He creado algunos ejercicios que combinan `Text`, `Image`, `Column` y `Row`. A través de estos problemas, puede aprender los conceptos básicos de cómo usar los diseños en Jetpack Compose.

## Instrucciones generales.

* Crea un nuevo proyecto llamado `Basic Component Practice`.
* Puede descargar y utilizar cualquier imagen que desee de los siguientes sitios web.
  https://www.iconfinder.com/
* Pega el siguiente código inicial en el archivo `MainActivity.kt` para comenzar el ejercicio.
```kotlin
package com.example.basiccomponentpractice

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.activity.enableEdgeToEdge
import androidx.compose.foundation.Image
import androidx.compose.foundation.layout.BoxWithConstraints
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.Row
import androidx.compose.foundation.layout.Spacer
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.height
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.layout.size
import androidx.compose.foundation.layout.width
import androidx.compose.material3.Scaffold
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.layout.ContentScale
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import com.example.basiccomponentpractice.ui.theme.BasicComponentPracticeTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            BasicComponentPracticeTheme {
                ResponsiveImageWithText()
            }
        }
    }
}

/**
 * Ejercicio 1: Diseño simple de imagen y texto
 */
@Composable
fun SimpleImageWithText() {
    // TODO: Implementar el diseño de una imagen y un texto
}

@Preview(showBackground = true)
@Composable
fun SimpleImageWithTextPreview() {
        SimpleImageWithText()
}

/**
 * Ejercicio 2: Imagen y texto alineados horizontalmente
 */
@Composable
fun ImageWithTextRow() {
    // TODO: Implementar el diseño de una imagen y un texto alineados horizontalmente
}

@Preview(showBackground = true)
@Composable
fun ImageWithTextRowPreview() {
    ImageWithTextRow()
}

/**
 * Ejercicio 3: Galería de imágenes
 */
@Composable
fun ImageGallery() {
    // TODO: Implementar el diseño de una galería de imágenes
}

@Preview(showBackground = true)
@Composable
fun ImageGalleryPreview() {
    ImageGallery()
}

/**
 * Ejercicio 4: Diseño de cuadrícula
 */
@Composable
fun ImageGrid() {
    // TODO: Implementar el diseño de una cuadrícula de imágenes
}

@Preview(showBackground = true)
@Composable
fun ImageGridPreview() {
    ImageGrid()
}

/**
 * Ejercicio 5: Diseño responsivo de imagen y texto
 */
@Composable
fun ResponsiveImageWithText() {
    // TODO: Implementar el diseño de una imagen y un texto responsivo
}

// TODO: El ejercicio 5 debe comprobarse ejecutando la aplicación y cambiando la orientación de la pantalla.
@Preview(showBackground = true)
@Composable
fun ResponsiveImageWithTextPreview() {
    ResponsiveImageWithText()
}
```

### Ejercicio 1: Diseño simple de imagen y texto

Crea un diseño que muestre una imagen en el centro de la pantalla y, debajo de ella, una descripción relacionada con la imagen. Utiliza una `Column` para alinear verticalmente la imagen y el texto.

**Pista:**
- Usa el componente `Image` para mostrar la imagen y el componente `Text` para mostrar el texto.
- Dentro de la `Column`, utiliza `Modifier.align(Alignment.CenterHorizontally)` para centrar el contenido horizontalmente.

**Pantalla de la aplicación:**

![image](https://github.com/user-attachments/assets/8cdfdfcd-405c-4dd8-b3b8-5594f4e4fac3)

### Ejercicio 2: Imagen y texto alineados horizontalmente

Crea un diseño que muestre una imagen y un texto alineados horizontalmente en la pantalla. Utiliza una `Row` para colocar la imagen a la izquierda y el texto a la derecha.

**Pista:**
- Utiliza `Modifier.size` para controlar el tamaño de la imagen.
- Dentro de la `Row`, usa `Modifier.padding` para ajustar el espacio entre los elementos.

**Pantalla de la aplicación:**

![image](https://github.com/user-attachments/assets/818b6f65-4460-440d-9935-e998df7d1175)

### Ejercicio 3: Galería de imágenes

Crea una galería que muestre tres imágenes diferentes alineadas verticalmente en la pantalla. Debajo de cada imagen, muestra un pie de foto correspondiente. Usa una `Column` para alinear cada par de imagen y texto verticalmente.

**Pista:**
- Coloca las tres parejas de imagen y texto de forma consecutiva dentro de una `Column`.
- Utiliza `Modifier.padding` para añadir espacio entre cada pareja.

**Pantalla de la aplicación:**

![image](https://github.com/user-attachments/assets/cfeadb9b-6e65-4c79-a196-9917f42ccef5)

### Ejercicio 4: Diseño de cuadrícula

Crea un diseño de cuadrícula de dos columnas que muestre cuatro imágenes. Debajo de cada imagen, muestra un pie de foto correspondiente. Combina `Column` y `Row` para crear la cuadrícula.

**Pista:**
- Crea dos `Row`, cada una con dos `Column` para formar una cuadrícula de dos columnas.
- Dentro de cada `Column`, alinea verticalmente la imagen y el pie de foto.

**Pantalla de la aplicación:**

![image](https://github.com/user-attachments/assets/cd85d419-4ed3-459b-a298-12accdc09a19)

### Ejercicio 5: Diseño responsivo de imagen y texto

Crea un diseño donde la imagen y el texto estén alineados horizontalmente, pero cuando el ancho de la pantalla se reduce, la imagen y el texto se alineen verticalmente. Combina `Row` y `Column` para aprender cómo cambiar el diseño según el tamaño de la pantalla.

**Pista:**
- Utiliza `BoxWithConstraints` para verificar el ancho de la pantalla.
- Si el ancho es amplio, usa `Row`; si es estrecho, usa `Column` para cambiar el diseño.

**Pantalla de la aplicación:**

![image](https://github.com/user-attachments/assets/d9141a4a-f598-4b1e-8983-eab438801ca4)

![image](https://github.com/user-attachments/assets/2a8a2179-151c-4d31-a8cd-f8c866717db9)
