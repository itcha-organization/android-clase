# Consejos para acelerar el IDE

## Obtenga información sobre sus construcciones
https://punchthrough.com/android-studio/

Una forma eficaz de inspeccionar una compilación e identificar cuellos de botella en el rendimiento es generar un análisis de compilación. Los escaneos de compilación proporcionan información muy detallada sobre lo que ha ocurrido durante el proceso de compilación y permiten ver cuánto tiempo han tardado las distintas tareas de compilación. 
El siguiente comando se pueden utilizar para instalar una aplicación en un dispo
```
./gradlew installDebug --scan
```

<details>

<summary>En caso de `ERROR: JAVA_HOME is not set`
</summary>

## Android Studioに割り当てるヒープ領域を増やす

![image](https://github.com/user-attachments/assets/a34c5f8c-ffdc-4a08-bdf5-b61144324d65)

![image](https://github.com/user-attachments/assets/c489880c-443a-4e71-a46d-a9f59d519724)
- Añade `JAVA_HOME` a la variable de entorno del usuario. Establece el valor en `C:\Program Files\Android\Android Studio\jbr`.
  ![image](https://github.com/user-attachments/assets/ef9d2dd9-6b64-4ea5-9b0c-7f17b6ca5955)
- Añada `%JAVA_HOME%\bin` a `Path`.
  ![image](https://github.com/user-attachments/assets/03adc211-0d05-4bfd-b529-e1e614a09fca)
- Reinicie el terminal y vuelva a ejecutar el comando.

## Android Studioに割り当てるヒープ領域を増やす
Gradle Android Compiler
![image](https://github.com/user-attachments/assets/87c2dc8d-b2b0-4325-97ac-f632fd85c903)


</details>


ベースライン
https://scans.gradle.com/s/bvj5rd2qirzye
https://scans.gradle.com/s/yhpe55iggjuk6




https://androidguru.one/760/
Compiler（JVMのオプション＝Command-line Options？）
「Build, Execution, Deployment」→「Compiler」→「Command-line Options」
ここで、「-Xmx」オプションを使用してHeap Sizeを指定することができます。たとえば、「-Xmx2048m」と入力すると、Heap Sizeを2048MBに設定することができます。

※マルチモジュールのプロジェクトのみで有効(デフォルトではモジュールはappのみ)
Build, Execution, Deployment > Compiler > Compile independent modules in parallelのチェックボックスにチェックを入れる必要があります。この設定を有効にすることで、コンパイルプロセスが並列化され、コンパイル速度が向上します。


Gradle（ビルドツール）
Gradleの設定方法として、Gradle VM optionsを確認することが挙げられます。Gradle VM optionsは、Gradleが使用するメモリーの量を調整することができます。デフォルトでは、Gradleは512MBのメモリーを使用しますが、この量を増やすことでビルド速度を向上させることができます。たとえば、1024MBや2048MBに設定することで、ビルド速度を向上させることができます。

 Android Studioの起動に使用されるJVM/Android Studio自体がどれだけのメモリを消費するかを決定
studio.vmoptions/studio64.exe.vmoptions
2. Increase IDE heap size to Max ( IDE performance enhancement)
As an Android developer, you already know that Android Studio requires a lot of RAM to run; if you haven't, the whole Android Studio/editor will lag. But if you already have enough RAM and are still facing a laggy editor issue, you can reduce the default heap size to max.
Go to: Settings → Appearance & Behavior → System Settings → Memory Settings → Select IDE max heap size.
I recommend choosing max heap size according to your RAM range from 2048MB to 4096MB.

gradle.properties
gradleのJVMオプション、gradleのビルドコマンドのパラメータを設定できる


プラグイン管理
Wajahat Karim Feb 20, 2019
https://medium.com/android-news/is-your-android-studio-always-slow-heres-how-to-speed-up-immediately-326ef9238024
最終更新日 2018年09月26日
https://qiita.com/ikemura23/items/0b370d638c20e081bc96

ビルド最適化
AndroidStudioでビルドを高速化するTIPSを試してみる（公式の検証）
https://qiita.com/etet-etet/items/29d58bd34f95763fd171
スキャンの見方など
https://www.freecodecamp.org/news/how-to-improve-the-build-speed-of-your-android-projects-bd49029d8602/
android.enableBuildCache=true and org.gradle.caching=true
https://punchthrough.com/android-studio/

トラブルシューティング
ファイル > キャッシュを無効化/再起動
https://stackoverflow.com/questions/42679475/android-studio-slow-performance

未読
https://tekidroid.tokyo/android-studio%E3%81%AE%E9%87%8D%E3%81%95%E3%82%92%E8%A7%A3%E6%B6%88%EF%BC%81/
https://www.droidcon.com/2025/05/06/how-to-reduce-android-studio-memory-usage/
https://www.blog.finotes.com/post/tips-to-speed-up-android-studio-boost-your-development-workflow-today
