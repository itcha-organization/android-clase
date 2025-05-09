# Consejos para acelerar el IDE

## Optimizar las compilaciones de Gradle.
https://qiita.com/etet-etet/items/29d58bd34f95763fd171

https://www.freecodecamp.org/news/how-to-improve-the-build-speed-of-your-android-projects-bd49029d8602/

### Obtenga información sobre sus construcciones
https://www.freecodecamp.org/news/how-to-improve-the-build-speed-of-your-android-projects-bd49029d8602/

Una forma eficaz de inspeccionar una compilación e identificar cuellos de botella en el rendimiento es generar un análisis de compilación. Los escaneos de compilación proporcionan información muy detallada sobre lo que ha ocurrido durante el proceso de compilación y permiten ver cuánto tiempo han tardado las distintas tareas de compilación. 
El siguiente comando tienen como objetivo un tiempo de compilación de referencia.
```
./gradlew clean assembleDebug --scan
```

<details>

<summary>En caso de `ERROR: JAVA_HOME is not set`
</summary>

![image](https://github.com/user-attachments/assets/c489880c-443a-4e71-a46d-a9f59d519724)
- Añade `JAVA_HOME` a la variable de entorno del usuario. Establece el valor en `C:\Program Files\Android\Android Studio\jbr`.
  ![image](https://github.com/user-attachments/assets/ef9d2dd9-6b64-4ea5-9b0c-7f17b6ca5955)
- Añada `%JAVA_HOME%\bin` a `Path`.
  <br>![image](https://github.com/user-attachments/assets/03adc211-0d05-4bfd-b529-e1e614a09fca)
- Reinicie el terminal y vuelva a ejecutar el comando.



</details>

### Optimizar las opciones JVM de Gradle.
- [Aumentar el tamaño del montón de JVM](https://developer.android.com/build/optimize-your-build?hl=ja#increase-the-jvm-heap-size)
- [Experimentar con el recolector de elementos no utilizados paralelo de JVM](https://developer.android.com/build/optimize-your-build?hl=ja#experiment-with-the-jvm-parallel-garbage-collector)

### Optimizar las opciones de Gradle
- [Usar la caché de compilación](https://medium.com/glovo-engineering/accelerate-your-android-development-top-techniques-to-reduce-gradle-build-time-part-i-of-ii-4f35aa4a1a17)
  <br>
  Agregue el código al archivo `gradle.properties`.
  ```
  org.gradle.caching=true
  ```
- [Usar la caché de configuración](https://developer.android.com/build/optimize-your-build?hl=es-419#use-the-configuration-cache)

Existen otras instrucciones oficiales de Android sobre cómo optimizar las compilaciones.<br>
https://developer.android.com/build/optimize-your-build

> [!NOTE]
>  El `Settings > Build, Execution, Deployment > Gradle Android Compiler` no necesita ser cambiado, porque puede ser configurado en `gradle.properties`.

## Aumentar el tamaño del montón del propio Android Studio
Vaya a:  `Settings > Appearance & Behavior > System Settings > Memory Settings > Select IDE max heap size`.
Recomiendo elegir el tamaño máximo del montón de acuerdo a su rango de RAM de 2048MB a 4096MB.

![image](https://github.com/user-attachments/assets/3bea8ec1-c394-49b4-a5a8-23aa5686fc76)
> Android Studio se ejecuta en la JVM. Añadiendo opciones JVM al archivo `studio.vmoptions`/`studio64.exe.vmoptions` también se obtienen los mismos resultados que en la imagen.

## Desactiva los plug-ins de Android Studio que no utilices.
https://medium.com/android-news/is-your-android-studio-always-slow-heres-how-to-speed-up-immediately-326ef9238024

https://qiita.com/ikemura23/items/0b370d638c20e081bc96

Resumen de otros métodos de aceleración

https://www.droidcon.com/2025/05/06/how-to-reduce-android-studio-memory-usage/

https://www.blog.finotes.com/post/tips-to-speed-up-android-studio-boost-your-development-workflow-today

Cómo borrar la caché y reiniciar AndroidStudio.

https://stackoverflow.com/questions/42679475/android-studio-slow-performance

未読
https://tekidroid.tokyo/android-studio%E3%81%AE%E9%87%8D%E3%81%95%E3%82%92%E8%A7%A3%E6%B6%88%EF%BC%81/


ベースライン
https://scans.gradle.com/s/bvj5rd2qirzye
https://scans.gradle.com/s/yhpe55iggjuk6

JVM 並列ガベージ コレクタを試す
https://developer.android.com/build/optimize-your-build?hl=ja#experiment-with-the-jvm-parallel-garbage-collector
https://gradle.com/s/zdd4m5ishfgny
https://gradle.com/s/uvulj5q7hdvbm

ビルドキャッシュ
https://medium.com/glovo-engineering/accelerate-your-android-development-top-techniques-to-reduce-gradle-build-time-part-i-of-ii-4f35aa4a1a17
https://gradle.com/s/blsoqzegegmn4
https://gradle.com/s/xm7p5k3iu7lz4

構成キャッシュ
org.gradle.configuration-cache=true 
https://gradle.com/s/awqrllqc22eok
https://gradle.com/s/ek3scfufx4xwi
