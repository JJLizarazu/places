📍 Places - Ecosistema Multiplataforma

Cliente Frontend interactivo con autenticación dinámica y consumo de API REST

Desarrollado por: Juan Jose Lizarazu Quiroga

Docente: Ing. Martin Albino Ascui

Materia: Tecnología Web I

Fecha de entrega: 08/06/2026

Tipo de proyecto: Frontend Multiplataforma (Compilación Web/Móvil)

Resumen del Sistema

Esta aplicación conforma la interfaz de usuario (UI) del ecosistema "Places". Desarrollada con el SDK de Flutter, su código base único permite compilarse y ejecutarse de manera nativa en navegadores web (HTML5/CanvasKit), así como en dispositivos Android e iOS.

El cliente está diseñado para comunicarse bidireccionalmente con el servidor de Django (places-backend). Incluye un flujo completo de autenticación y manejo de sesión local.

Flujos funcionales implementados:

Onboarding (Login/Signup): Interfaz fluida con animaciones nativas (PageController).

Control de Acceso: Validaciones frontend (campos requeridos, longitud de clave, formato de email) previas al envío HTTP.

Recuperación de Credenciales: Ventana modal (PopUp) interactiva.

Gestión de Estado: Singleton en memoria (UserSession) para persistencia de datos del usuario activo a través del árbol de widgets.

Navegación Segura: Limpieza absoluta del árbol de navegación (rootNavigator) al ejecutar el Logout.

Características técnicas

Característica

Detalle

Framework Base

Flutter SDK (Dart)

Patrón de Navegación

Scaffolding mixto (Material Scaffold + CupertinoTabScaffold)

Consumo de Servicios

Paquete http (Serialización JSON nativa)

Estado Local

Patrón Singleton (user_session.dart) para almacenamiento en caché

Tipografía / Assets

Lato, WorkSans / FontAwesomeIcons para iconografía escalable

Guía de Despliegue (Modo Web Local)

Dado que las configuraciones de los Endpoints apuntan a 127.0.0.1 (localhost), la prueba de desarrollo debe ejecutarse en el navegador Chrome.

1. Dependencia Absoluta

Verifica que el proyecto places-backend esté en ejecución activa (python manage.py runserver). Si el backend está apagado, la aplicación arrojará excepciones de conexión de red.

2. Inicialización

Abre una consola en la ruta donde desees alojar el código cliente:

# Clonar repositorio
git clone <URL_DEL_REPOSITORIO_FLUTTER>
cd places

# Descargar dependencias del pubspec.yaml
flutter pub get


3. Despliegue en Navegador

Inicia el motor de compilación web de Flutter. Este proceso puede tomar unos segundos la primera vez:

flutter run -d chrome


Pruebas sugeridas:

Navega a NUEVO y registra un usuario (verifica validaciones de clave).

Ve a EXISTE y realiza el Login (si la clave es incorrecta, observa el SnackBar rojo).

Utiliza la opción "¿Olvidaste tu contraseña?" para actualizar datos.

Navega hasta el 3er ícono (Perfil) y verifica que tus datos se extraigan correctamente. Cierra sesión para volver al login.

Estructura de Directorios (Source)

places/
├── pubspec.yaml             # Gestor de dependencias e inyección de assets
├── assets/                  # Recursos gráficos estáticos
│   ├── fonts/               # Archivos TTF/OTF locales
│   └── images/              # Gráficos Rasterizados (JPG/PNG)
└── lib/                     # 🧠 NÚCLEO DE LA APLICACIÓN DART
├── login/               # Módulo Completo de Identidad
│   ├── pages/
│   │   └── widgets/
│   │       ├── sign_in.dart   # Auth, Modal de Recuperación y Networking
│   │       └── sign_up.dart   # Formulario de Registro (POST a DB)
│   ├── widgets/
│   │   └── snackbar.dart      # Notificador UI global
│   └── user_session.dart      # Caché de estado activo (Memoria volátil)
├── main.dart            # Entrada (Llamada al Login) y forzado de orientación vertical
├── places_cupertino.dart# Estructura de enrutamiento principal (Bottom NavBar iOS)
├── home.dart            # Módulo Principal y consumo de Widgets (Cards)
└── profile_places.dart  # UI del Perfil (Consumo de caché) y Lógica de LogOut


Desarrollado con compromiso y estándares de ingeniería para la materia de Tecnología Web I.