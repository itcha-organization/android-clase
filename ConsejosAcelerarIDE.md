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
