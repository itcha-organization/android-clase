# Cómo agregar imágenes a tu app para Android

Practicamos el siguiente codelab.
元ネタ

https://developer.android.com/codelabs/basic-android-kotlin-compose-add-images

___

1. ②アプリを準備する
   1. プロジェクトに画像追加(丸コピ)
      * QUALIFIER TYPE等、画面サイズに応じて解像度変更するための設定は、「スマホのみ対象のため説明省く、もっと知りたかったら公式見てね」とする
画像を追加するためにコンポーズ可能な関数を追加する
1. ③Image コンポーザブルを追加する
   1. Jetpack Compose のリソース
      * リソースの概要、アクセスの仕方Rクラスを説明
      * Imageだけのプレビューを作って、説明
        ```kotlin
        @Preview(showBackground = true)
        @Composable
        fun ImagePreview() {
            Image(
                painter = painterResource(id = R.drawable.androidparty),
                contentDescription = null
            )
        }
        ```
1. ④Box レイアウトを追加する
   * Boxの概要説明
     
     ![image](https://github.com/user-attachments/assets/ff07a5a7-6fe1-4992-860a-7018a0c61486)
   * GreetingImage関数作成&呼び出し箇所修正、Boxの実践
      ```kotlin
      @Composable
      fun GreetingImage(message: String, from: String, modifier: Modifier = Modifier) {
          val image = painterResource(R.drawable.androidparty)
          Box(modifier) {
              Image(
                  painter = image,
                  contentDescription = null
              )
              GreetingText(
                  message = message,
                  from = from,
                  modifier = Modifier
                      .fillMaxSize()
                      .padding(8.dp)
              )
          }
      }
      ```
      ```kotlin
      @Preview(showBackground = true)
      @Composable
      fun BirthdayCardPreview() {
          HappyBirthdayTheme {
              GreetingImage(
                  message = "Happy Birthday Sam!",
                  from = "From Emma"
              )
          }
      }
      ```
      ```kotlin
      setContent {
          HappyBirthdayTheme {
              // A surface container using the 'background' color from the theme
              Surface(
                  modifier = Modifier.fillMaxSize(),
                  color = MaterialTheme.colorScheme.background
              ) {
                  GreetingImage(
                      message = "Happy Birthday Sam!",
                      from = "From Emma"
                  )
              }
          }
      }
      ```
1. ⑤不透明度を変更し、画像を拡大縮小する
   1. Imageのパラメータを変更する
      * コンテンツのサイズを調整する
        ```diff
        Image(
            painter = image,
            contentDescription = null,
        +    contentScale = ContentScale.Crop
        )
        ```
      * 不透明度の変更
        ```diff
        Image(
            painter = image,
            contentDescription = null,
            contentScale = ContentScale.Crop,
        +    alpha = 0.5F
        )
        ```
   3. レイアウト修飾子：ArrangementとAlignment
      * 概要説明&デモ
        
        ![image](https://github.com/user-attachments/assets/665d1302-0f6a-4484-a6d8-a95b2d88b76d)
1. ⑦適切なコード プラクティスを採用する
   1. Stringリソースの使い方
      * Stringリソース概要説明&app > res > values > strings.xml の strings.xml を見てみる
      * 練習
      * 最後にアプリ実行
1. ⑧課題に挑戦しましょう
   1. minicuestionario:署名テキスト コンポーザブルを画面の中央に揃えて配置

1. リファレンス
   https://developer.android.com/codelabs/basic-android-kotlin-compose-add-images?hl=ja&continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-1-pathway-3%3Fhl%3Dja%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-add-images#0
