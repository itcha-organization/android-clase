# Creación de proyectos y configuración inicial

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

## Conexión de un dispositivo Android a Android Studio

### Activar la depuración USB en un dispositivo Android

Para permitir que Android Studio se comunique con el dispositivo Android, debes habilitar la depuración por USB en la configuración Opciones para desarrolladores del dispositivo.

En el dispositivo Android, pulsa `Ajustes` > `Acerca del teléfono`.

![image](https://github.com/user-attachments/assets/9758619e-2e06-420c-bc5f-176e8236c095)

Pulse `Información de estado`.

![image](https://github.com/user-attachments/assets/d5412f99-3a43-4009-b268-f2b438f59d5a)

Toque `Número de compilación`（`Número de serie`）7 veces.<br>
Si se te solicita, ingresa la contraseña o el PIN del dispositivo. Sabrás que tuviste éxito cuando veas el mensaje ¡Ya eres desarrollador! (You are now a developer!)

![image](https://github.com/user-attachments/assets/a7f8c6f1-5616-4184-99f6-39c19840b83c)

Regresa a `Ajustes` y presiona `Opciones para desarrolladores`.Si no se encuentra, busque `Opciones para desarrolladores`.

![image](https://github.com/user-attachments/assets/24a444bf-35c5-41ec-8ab9-5308ed5e8637)

Presiona el botón de Depuración por USB (USB Debugging) a fin de activarlo.

![image](https://github.com/user-attachments/assets/14d0cc74-0600-4c1c-9b17-82c310301de3)

### Activar la duplicación y ejecutar la aplicación en el dispositivo Android

Pulse en Icono Ajustes⚙→ `Setting` o teclee las teclas Ctrl, Alt y S para abrir la configuración.

Busca `mirror` en la pantalla de configuración.<br>
Haga clic en `Device Mirroring` para abrirlo.<br>
Marque `Activate mirroring when a new physical device is connected`. Si aparece una advertencia, seleccione `Acknowledge`.<br>
Por último, pulse `Apply` para aplicar los ajustes y pulse `OK` para finalizar.

![image](https://github.com/user-attachments/assets/920a66e1-7656-434e-9da1-ef926744196d)

Conecta el dispositivo Android al ordenador mediante un cable USB.

Al continuar con el procedimiento, el dispositivo muestra un diálogo solicitando permiso para la depuración USB.<br>
En este caso, marque la casilla y pulse `Permitir`.

![image](https://github.com/user-attachments/assets/dce74bbd-aa38-4adb-9733-3e41476b14b6)

En Android Studio, pulse el icono situado en la parte derecha de la pantalla para mostrar la pestaña `Running Devices`.

![image](https://github.com/user-attachments/assets/45ad5012-8402-4b6c-a4af-31d581abed08)

Haga clic en el icono + para ver los dispositivos disponibles y seleccione el dispositivo conectado.

![image](https://github.com/user-attachments/assets/fce571d8-4eed-47f1-8dad-7361414be7f5)

Si aparece una advertencia, haga clic en `Permitir acceso`.

![image](https://github.com/user-attachments/assets/e884dca8-874c-4dc6-b144-3b73684e58f3)

Pulse en Icono ▶ o teclee las teclas Mayús y F10 para ejecutar la aplicacion.

![image](https://github.com/user-attachments/assets/f279b2e3-27f0-40cf-8d98-7bc45ac9a951)
