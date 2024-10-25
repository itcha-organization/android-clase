# Instalación de Flutter con AndroidStudio

## Instalación del SDK de Flutter
- Consulte Requisitos de hardware para comprobar si lo ha hecho para instalar y ejecutar Flutter.<br>
  El entorno de desarrollo de Windows Flutter debe cumplir los siguientes requisitos mínimos de hardware.<br>
  ![image](https://github.com/user-attachments/assets/03159891-9d85-418c-ae65-b95d21ecf360)
- Abra los siguientes sitios web oficiales.<br>
  https://docs.flutter.dev/get-started/install/windows/mobile#install-the-flutter-sdk
- Abre la pestaña `Descargar e instalar` y pulsa el botón para descargar el archivo zip.
  ![image](https://github.com/user-attachments/assets/f6ea7e92-41c6-40eb-b14c-ce0a5a1432b3)
- Extraiga el archivo zip y colóquelo directamente en la unidad C:.
  <br>Tarda unos 15 minutos, pero espera a que termine.
  ![image](https://github.com/user-attachments/assets/60a6e037-32a7-4926-ba74-cb2f1103f235)
- Busque `variables` y abre `Editar las variables de entorno del sistema`.
  ![image](https://github.com/user-attachments/assets/0fa4ba19-10a5-4ec6-ab0f-7eafa99400c4)
- Haga clic en `variables de entorno`.
  <br>![image](https://github.com/user-attachments/assets/53fdb662-6cb7-4aab-94d4-30f0fa0b1122)
- Seleccione `Path` y haga clic en `Editar`.
  <br>![image](https://github.com/user-attachments/assets/b402cef5-312f-4225-81fe-380f7acac224)
- Haga clic en `Nuevo`.
  <br>![image](https://github.com/user-attachments/assets/c9b95574-d0e6-42ea-b3e0-b7f9984ce5de)
- Introduzca `C:\flutter\bin` y haga clic en `Aceptar`. **Se recomienda copiar y pegar lo para no equivocarse.**
  ![image](https://github.com/user-attachments/assets/9edb2d29-6fce-4a45-88a2-28853c51d8c6)
- Haga clic en `Aceptar`.
  <br>![image](https://github.com/user-attachments/assets/bc80ef5d-34dc-4780-a8dd-bede3154ab3c)

## Configuración inicial en AndroidStudio
- Inicia AndroidStudio. **Si ya se ha iniciado, ciérrelo y vuelva a iniciarlo.**
- Abra el Terminal (Windows PowerShell) haciendo clic en el icono situado en la parte inferior izquierda de la pantalla.
- Ejecute el comando `flutter` y compruebe que no se producen errores.
  ![image](https://github.com/user-attachments/assets/6aaec25f-2f24-476e-8415-9d77cb6c875c)
  > [!NOTE]  
  > Si obtienes un error `Error: Unable to find git in your PATH.`, ejecuta el siguiente comando para excluir `C:\flutter\` de la seguridad de Git.
  > ```
  > git config --global --add safe.directory C:\flutter
  > ```
- Ejecuta el comando `flutter doctor`. Configuraremos los ajustes para que los resultados de esta ejecución sean todos completos✅.
  ![image](https://github.com/user-attachments/assets/c8d8c89e-05c7-4aff-a1cb-a09dd1496f3e)
- Haga clic en el icono de configuración⚙ y abre el `SDK Manager`.
  ![image](https://github.com/user-attachments/assets/566ba031-8fa8-4cae-abf2-81b289382d9b)
- Abre la pestaña `SDK Tools` e instala `Android SDK Command-line Tools(Latest)`.
  ![image](https://github.com/user-attachments/assets/3da6fc65-11cf-4696-afe1-a5e25cc90ebd)

  ![image](https://github.com/user-attachments/assets/3d34bfb1-8607-4bda-a094-b5129f3c749b)
- Ejecute el comando `flutter doctor --android-licenses` en un terminal.**Se le harán varias preguntas, introduzca `y` en todas ellas y pulse `Intro` para continuar.**
  ![image](https://github.com/user-attachments/assets/07c857bb-b754-4abf-95c4-9daec5f41b97)
- Ejecuta el comando `flutter doctor` y asegúrese de que todo está ajustado a completo✅.
  ![image](https://github.com/user-attachments/assets/c9345ef9-8668-4335-b05f-505a8a40e88f)
  > [!NOTE]  
  > Los elementos que no se hayan completado✅ deben seguir instalándose.
  > 
  > **VisualStudio:**
  > <br>Instalador de visual studio: https://learn.microsoft.com/en-us/cpp/build/vscpp-step-0-installation?view=msvc-170#step-2---download-visual-studio
  > <br>Hay que instarar visual studio de opcion `Desktop development with C++`.Esto es para obtener algunos componentes que Flutter necesita para funcionar.
  > ![image](https://github.com/user-attachments/assets/cd0022b4-ce51-42b1-9f71-33a08e4a9a37)

## Instalar plug-in en AndroidStudio
- Haga clic en el icono de configuración⚙ y abre el `Plugins`.
  ![image](https://github.com/user-attachments/assets/d8636b6d-1e63-4323-8b72-d859127427d5)
- Dentro de la pestaña `Marketplace`, busca `flutter` y haz clic en `Install`.
  ![image](https://github.com/user-attachments/assets/ae344477-fcd7-479c-8ee0-40c403bf59b3)
- Reinicie AndroidStudio una vez finalizada la instalación.
  ![image](https://github.com/user-attachments/assets/387130fc-aa95-4b8d-9b8a-ba0acc097692)

## Cree un proyecto Flutter.
- Cierra el proyecto en AndroidStudio y muestra la pantalla `Welcome`.
  <br>![image](https://github.com/user-attachments/assets/005696a8-3154-42ce-b063-4aa964a92b91)
- Haga clic en `New Flutter Project`.
  <br>![image](https://github.com/user-attachments/assets/e98e972d-be51-460f-81a1-7b6dec57331d)
- Seleccione `Flutter` en el menú de la izquierda.Introduzca `C:\flutter` en el campo de Flutter SDK path y haga clic en `Next`.**Se recomienda copiar y pegar lo para no equivocarse.**
  ![image](https://github.com/user-attachments/assets/aa5cf0f2-970f-4c49-8d3d-8546e3e403e8)
- Introduzca `test_drive + INICIALES` (Ejemplo: `test_driveCJZR`) como nombre del proyecto.
- Marque las tres plataformas `Android`, `Web` y `Windows` y haga clic en `Crear`.
  ![image](https://github.com/user-attachments/assets/5fa4623a-229f-4423-bb43-d11703ce2e2a)

## Ejecuta la aplicación en su telefono físico
- Haga clic en el icono de configuración⚙ y abre el `SDK Manager`.
  ![image](https://github.com/user-attachments/assets/5fd40a8a-6d22-40fc-b634-a73b9264ca8d)
- Abre la pestaña `SDK Tools` e instala `Google USB Driver`.
  ![image](https://github.com/user-attachments/assets/9b7c6cd0-b04f-4bfb-9522-89b2e77773f2)

  ![image](https://github.com/user-attachments/assets/e883fd62-1485-47ec-8d78-980520f51397)

- **Conecta el teléfono al PC.** En un terminal, ejecute el comando `flutter devices` y compruebe que aparece el teléfono.
  ![image](https://github.com/user-attachments/assets/d63bf144-a888-4aae-adf2-84f2b6eae1fe)

- Selecciona el teléfono en la selección de dispositivos arriba de la pantalla y pulsa el icono ▶ para ejecutar el código de muestra.
  ![image](https://github.com/user-attachments/assets/1d97f3f4-9d6a-454a-b121-2388be9a204c)
