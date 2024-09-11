# Cómo agregar botón a tu app para Android

En este codelab, crearás una app interactiva de Dice Roller que les permite a los usuarios presionar un elemento Button componible para lanzar un dado. El resultado del lanzamiento se muestra con un elemento Image componible en la pantalla.

![image](https://github.com/user-attachments/assets/c7644989-c568-4f6b-ba02-a0fb8d877b52)

Usa Jetpack Compose con Kotlin para compilar el diseño de tu app y, luego, escribe la lógica empresarial para controlar lo que sucede cuando se presiona el elemento Button componible.

## Repaso: Crear un proyecto
Crea un proyecto `Dice Roller` en Android Studio para este tutorial.
1. En Android Studio, haz clic en File > New > New Project.
1. En el diálogo New Project, selecciona Empty Activity y haz clic en Next.
1. En el campo Name, ingresa `Dice Roller`.
1. En el campo Minimum SDK, selecciona un nivel mínimo de API de 24 (Nougat) del menú y, luego, haz clic en Finish.

## La función `Button`

El `Button` toma el parámetro `onClick`, que define la acción a ejecutar cuando el botón es presionado, y dentro de él se coloca el contenido que puede ser un texto o un ícono, por ejemplo.

En la función `onCreate`, sustituye el código del bloque `DiceRollerTheme` por el siguiente código con `Button` y ejecuta la aplicación.
```kotlin
DiceRollerTheme {
    Button(
        // Acción que se ejecuta cuando se hace clic
        onClick = { Log.d("button", "Botón pulsado.") }
    ) {
        Text("Generar un registro") // Texto del botón
    }
}
```
Confirmamos que el registro se emite cuando se pulsa el botón.

Haga clic en el icono del gato para mostrar el panel `Logcat`. Introduzca `button` en la ventana de búsqueda para afinar la búsqueda.

![image](https://github.com/user-attachments/assets/17003884-5690-4c74-806e-dc59213b9e92)

## Creación de la interfaz de usuario de la aplicación
・画像を追加する
  ・フォルダごと選択して一括で画像をアップロード
  ・とりあえず1の画像を使ってImage定義

[ダウンロード](https://github.com/google-developer-training/basic-android-kotlin-compose-training-dice-roller/raw/main/dice_images.zip)
  
・DiceWithButtonAndImageを宣言
・Columnを追加
・Button定義（表示するTextも）
・Spacer関数
・strings.xml
　→最初ハードコードしておいて、抽出する方法が良い

## ボタン押下時のロジックを設定する
・onClick実装
→クリックできるけど、しても何も起きない
・Imageの画像に変数を代入して動的にする
→再描画されないので何も起きない
・ステートを使う

・インタラクティブモード
・デバッガ―
