# Crea aplicaciones con IA con Flutter y Gemini
Vamos a probar una aplicación de chat simple en Flutter que se conecte a la API de Gemini para generar respuestas de IA a los mensajes del usuario.

### Paso 1: Crear un Proyecto de Flutter

1. Crea un proyecto en Flutter con nombre `gemini_chat` en AndroidStudio.
   ![image](https://github.com/user-attachments/assets/ba122b0c-a97e-49d2-860b-9c8dd33684f4)

### Paso 2: Instalar los dependencias

Esta aplicación requiere los siguientes dependencias. Agrégalos en el archivo `pubspec.yaml` y luego actualiza las dependencias con `Pub get`.

```yaml
dependencies:
  flutter:
    sdk: flutter
  flutter_markdown: ^0.7.4
  google_generative_ai: ^0.4.6
  url_launcher: ^6.3.1
```

### Paso 3: Configurar la funcion `main` y código principale `MyApp`

1. Abre `lib/main.dart` y reemplázalo con el siguiente código:

```dart
import 'package:flutter/material.dart';
import 'package:google_generative_ai/google_generative_ai.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Gemini AI Chat',
        theme: ThemeData(
          colorScheme: ColorScheme.fromSeed(
            brightness: Brightness.dark,
            seedColor: Colors.blueAccent,
          ),
          useMaterial3: true,
        ),
        home: Scaffold(
          appBar: AppBar(title: Text('AI Chat con Gemini API')),
          body: Text('TODO: Falta la implementación de ChatScreen.'),
        ));
  }
}
```

### Paso 4: Crear la Pantalla de Chat

1. Añade `ChatScreen` y define la interfaz y lógica de la pantalla de chat.

```dart
class ChatScreen extends StatefulWidget {
  const ChatScreen({super.key});

  @override
  State<ChatScreen> createState() => _ChatScreenState();
}

class _ChatScreenState extends State<ChatScreen> {
  String? apiKey; // TODO: Falta el clave
  late final GenerativeModel _model;
  late final ChatSession _chatSession;
  final TextEditingController _textController = TextEditingController();
  final List<String> _chatHistory = [];

  @override
  void initState() {
    // TODO: Falta la implementación
  }

// TODO: Falta la implementación
//   Future<void> _sendMessage(String message) async {
//   }

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Expanded(
          child: ListView.builder(
            itemCount: _chatHistory.length,
            itemBuilder: (context, index) {
              return ListTile(
                title: Text(_chatHistory[index]),
              );
            },
          ),
        ),
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: Row(
            children: [
              Expanded(
                child: TextField(
                  controller: _textController,
                  decoration: InputDecoration(
                    hintText: 'Enter a message...',
                    border: OutlineInputBorder(),
                  ),
                ),
              ),
              IconButton(
                icon: Icon(Icons.send),
                onPressed: () {
                  // TODO: Falta la implementación
                },
              ),
            ],
          ),
        ),
      ],
    );
  }
}
```

### Paso 5: Implementa el método `_sendMessage`.

```dart
Future<void> _sendMessage(String message) async {
  setState(() {
    _chatHistory.add("You: $message");
  });
  try {
    final response = await _chatSession.sendMessage(Content.text(message));
    setState(() {
      _chatHistory.add("AI: ${response.text}");
    });
  } catch (e) {
    setState(() {
      _chatHistory.add("Error: $e");
    });
  }
}
```
```diff
IconButton(
  icon: Icon(Icons.send),
  onPressed: () {
    _sendMessage(_textController.text); // Añade este código.
    _textController.clear(); // Añade este código.
  },
),
```

### Paso 6: Configurar `GenerativeModel` y `_chatSession`.

Implementa `initState` e inicializa `GenerativeModel` y `_chatSession`.El programa para utilizar la `GeminiAPI` ya está listo.

```dart
@override
void initState() {
  super.initState();
  if (apiKey != null) {
    _model = GenerativeModel(model: 'gemini-pro', apiKey: apiKey!);
    _chatSession = _model.startChat();
  }
}
```

### Paso 7: Establezca la clave API.
Establecer clave API.

```dart
String? apiKey = 'Su propia clave API';
```

> [!CAUTION]
> Básicamente, las claves API no deben codificarse directamente en el código fuente.
> En este caso, el procedimiento se codificó para simplificar el proceso, pero esto es problemático desde el punto de vista de la seguridad.
