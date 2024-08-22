# Configuración

## Instalación de Android Studio

Utiliza un IDE gratuito llamado Android Studio. Con Android Studio, puede hacerlo todo, desde el desarrollo de aplicaciones hasta las pruebas.<br>
Necesitará unos 8 GB de espacio libre. Asegúrese de que dispone de suficiente espacio libre antes de iniciar la instalación.

Abra el sitio web oficial ![https://developer.android.com/studio?hl=es-419
](https://developer.android.com/studio?hl=es-419)
<br>
Haz clic en "Descargar Android Studio Koala".

![image](https://github.com/user-attachments/assets/90a35eaf-04b3-4ed5-92f7-33c46c02bf24)

Después de revisar los términos y condiciones de uso, marque "Leí y acepto los Términos y Condiciones anteriores" y pulse "Descargar".

![image](https://github.com/user-attachments/assets/09da411d-621e-4a1e-8ce2-10ab7c7c8c98)

Ejecute el instalador descargado.

![image](https://github.com/user-attachments/assets/6de74cb7-3e96-41d0-ae2d-d8207d278c21)

Pulse `Next` cuando aparezca la pantalla `Welcome to Android Studio Setup`.

![image](https://github.com/user-attachments/assets/42f567c5-afc4-4aad-9820-a5937ca9670f)

Asegúrate de que la opción `Android Virtual Device` está marcada y pulse `Next`.

![image](https://github.com/user-attachments/assets/5711178e-0e9e-4934-9722-ef6b026695dc)

No es necesario cambiar el lugar de instalación. Pulse `Next`.

![image](https://github.com/user-attachments/assets/610f8697-197d-4afa-8e26-3beeba095112)


Decide el nombre que aparecerá en el menú Inicio. Si no necesita cambiarlo en particular, pulse `Instalar` tal como está.

![image](https://github.com/user-attachments/assets/c55e4999-5efd-489b-a974-f9a213654551)

Pulse `Siguiente` cuando finalice la instalación.

![image](https://github.com/user-attachments/assets/e6f1fce8-5786-4997-988d-36f6a31a6588)

Asegúrate de que la opción `Start Android Studio` está marcada y pulsa `Finish`.

![image](https://github.com/user-attachments/assets/fde2a1f8-c612-48e4-973f-6e9fa7a60461)

Seleccione `No importar configuración` y pulse `OK`. 

![image](https://github.com/user-attachments/assets/2587ab1c-a84b-422c-989d-a8e6100d9050)

Selecciona si quieres permitir que `Android Studio` envíe información de uso a `Google`.<br>
Si no hay ningún motivo, puede seleccionar "No enviar" sin problemas.

![image](https://github.com/user-attachments/assets/5c5f2709-56bd-4453-9758-336a9ca90977)

Pulse `Next`.

![image](https://github.com/user-attachments/assets/658150be-55b0-43fc-a9f4-bb93f63e43e3)

Selección del método de configuración. Seleccione `Estándar` y pulse `Siguiente`.

![image](https://github.com/user-attachments/assets/c98e0cf4-3b61-41c8-9d1b-45789facc530)

Pulse `Next`.

![image](https://github.com/user-attachments/assets/f6b52477-84bc-41c2-a210-20400a2f3778)

Tienes que aceptar la licencia, así que haz clic en `android-sdk-license` a la izquierda y selecciona `Accept` abajo a la derecha.<br>
Se espera que dure aproximadamente 30 minutos.

![image](https://github.com/user-attachments/assets/47a7046a-2a0e-4059-abbb-a51731c05fb9)

Pulse `Finish` para iniciar la instalación.

![image](https://github.com/user-attachments/assets/07124e99-6e68-45b0-ab20-43c8f00b313b)

Pulse `Finish` cuando la instalación haya terminado.

![image](https://github.com/user-attachments/assets/15e12513-333e-42c1-92e2-ab9e8e0ccd40)

Cuando aparezca la pantalla de inicio de Android Studio, habrás terminado.

Android Studio se actualiza con frecuencia, así que comprueba si hay actualizaciones. Haz clic en el símbolo de configuración situado en la parte inferior izquierda de la pantalla de bienvenida y selecciona `Check for Updates` en el menú que aparece.

![image](https://github.com/user-attachments/assets/a67efc4f-2ef0-4a10-8278-942520cb1b59)

Si aparece en la esquina inferior derecha de la pantalla, hay una actualización disponible. Haga clic en `Update` para obtenerla.

![image](https://github.com/user-attachments/assets/2d50ba92-92dd-49c3-bc37-c0888f3e6542)

![image](https://github.com/user-attachments/assets/8c6fbcd8-0243-43c2-ab74-3f279db8cb6b)

Si aparece la palabra `Restart`, haga clic para reiniciar.

![image](https://github.com/user-attachments/assets/cc1b7476-8991-4c63-8e02-c36d8ba6582c)

## Crear un proyecto

Haga clic en `New Project`.

![image](https://github.com/user-attachments/assets/98bae122-05f2-465d-8d9a-65d3adac409a)

Seleccione `Empty Views Activity` y pulse `Next`.
<br>Empty significa 'vacío' y Empty Views Activity es un diseño para construir una pantalla de aplicación desde cero.

![image](https://github.com/user-attachments/assets/731937ad-f286-45d3-893a-b75d27c9787f)

A continuación, introduzca la información del proyecto.

![image](https://github.com/user-attachments/assets/313e606d-db00-44ac-a7b4-285e09892907)

* ①Nombre de la aplicación:<br>
  Introduzca un nombre para su aplicación. En este caso, hemos elegido `Sample`.

* ②Nombre del paquete:<br>
  El nombre del paquete especificado aquí también se utiliza para el applicationId (ID de aplicación) utilizado cuando la aplicación se publica en Play Store.<br>
  `https://play.google.com/store/apps/details?id=Nombre del paquete`

  Las aplicaciones con el mismo ID no pueden publicarse en Play Store, por lo que el nombre del paquete debe ser uno que no duplique otros.Es habitual adquirir un dominio y utilizarlo como nombre del paquete.

  En este caso, dado que la aplicación no se publicará, no hay ningún problema si se establece en com.example.sample.

* ③Guardar ubicación:<br>
  Especifique dónde desea guardar este proyecto - no importa si lo guarda en la carpeta AndroidStudioProjects.

* ④Lenguaje:<br>
  Seleccione si desea utilizar el lenguaje Java o Kotlin. JetpackCompose sólo soporta el lenguaje kotlin, por lo que seleccione kotlin aquí.

* ⑤SDK mínimo:<br>
  Dependiendo del SDK que se haya configurado, se determina hasta qué fecha se admiten modelos más antiguos.<br>
  Para este proyecto, seleccione API 21.En el desarrollo real, tiene que pensar qué APIs permitirán las funciones que quieres implementar en tu aplicación.

![image](https://github.com/user-attachments/assets/b7dbf098-73cb-4481-9226-64d6c44f4155)

  Pulsa `Help me choose` para ver el porcentaje de modelos compatibles con cada SDK.

![image](https://github.com/user-attachments/assets/c5ef65ef-5b6c-4792-a0db-2b84cb23683e)

* ⑥Configuración de la construcción:<br>
  Seleccione el idioma que se utilizará para el archivo de configuración de la aplicación. Continúe sin realizar ningún cambio aquí.

Una vez introducido todo, pulse `Finish` en la esquina inferior derecha. Se inicia la creación del proyecto.

![image](https://github.com/user-attachments/assets/c7f0c233-1201-4725-97ff-421fdd29eb8e)

Una vez finalizada la instalación del SDK, pulse `Finish`.

![image](https://github.com/user-attachments/assets/80af867b-e5a1-43ba-bcfc-f8a2e6077dbf)


Cuando se crea el proyecto, aparece la siguiente pantalla.

En la parte derecha de la pantalla verás una introducción a las nuevas características del Android Studio descargado.<br>
Haga clic en el botón Asistente situado en el extremo derecho para cerrarlo.

![image](https://github.com/user-attachments/assets/b214319c-7ec6-4424-b4b8-9b24fd295f54)

## Configurar funciones útiles

### Importación automática

Active la configuración para añadir automáticamente las importaciones necesarias y eliminar automáticamente las importaciones no utilizadas.

Pulse en Icono Ajustes⚙→ `Setting` o teclee las teclas Ctrl, Alt y S para abrir la configuración.

![image](https://github.com/user-attachments/assets/11ed7c05-839e-41b5-80fc-bba9ad04ac71)

Abra `Editor` → `General` → `Auto Import` en el menú de la izquierda.<br>
A continuación, active las siguientes opciones tanto en Java como en Kotlin 
* Add unambiguous imports on the fly
* Optimize imports on the fly

Por último, pulse `Apply` para aplicar los ajustes y pulse `OK` para finalizar.

![image](https://github.com/user-attachments/assets/a56818b3-95f9-4254-80a8-0ba32050bacf)


> [!NOTE]
> `Optimize imports on the fly`, que elimina automáticamente las importaciones, sólo se aplica al proyecto actual. Si creas un proyecto nuevo, tienes que volver a activarla.
