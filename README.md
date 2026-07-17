# Registro de Peliculas - TP1

Aplicacion Android para gestionar el registro de peliculas de una coleccion
personal. Desarrollada con Kotlin y Jetpack Compose.

## Funcionalidades

- Registro de peliculas con titulo, director, año, genero y duracion
- Lista vertical de peliculas registradas (LazyColumn)
- Cada item muestra sus datos en una fila horizontal deslizable (LazyRow)
- Eliminacion de peliculas con dialogo de confirmacion y animacion de salida
- Persistencia de datos ante cambios de configuracion (rotacion de pantalla)
  mediante ViewModel y rememberSaveable
- Banner con imagen personalizada
- Icono de app personalizado
- Tema personalizado con soporte para modo claro y oscuro

## Estructura del proyecto
app/src/main/java/com/example/registropeliculas/
├── MainActivity.kt          # Actividad principal, contiene:
│   ├── Pelicula               # data class con los datos de una pelicula
│   ├── PantallaPrincipal      # LazyColumn que agrupa banner, formulario y lista
│   ├── FormularioPancracio    # formulario de ingreso de datos
│   └── ItemPelicula           # cada item de la lista, con LazyRow, dialogo de
│                                confirmacion y animacion al eliminar
├── PeliculasViewModel.kt     # ViewModel que guarda la lista de peliculas en un
│                                StateFlow, sobrevive a cambios de configuracion
└── ui/theme/
├── Color.kt               # paleta de colores del tema
├── Theme.kt                # definicion de RegistroPeliculasTheme (claro/oscuro)
└── Type.kt                 # tipografia de la app

## Arquitectura

Los datos de la app (lista de peliculas) se manejan en un `PeliculasViewModel`,
separado de la interfaz. Esto sigue las practicas recomendadas de arquitectura
de apps para Android: la UI (Composables) solo muestra el estado y notifica
eventos, mientras que el ViewModel mantiene los datos vivos durante toda la
vida de la Activity, incluso si esta se destruye y recrea (por ejemplo, al
rotar la pantalla).

Los campos del formulario usan `rememberSaveable` para que el texto que se
esta escribiendo tambien sobreviva a un cambio de configuracion antes de
tocar "Agregar".

## Tema personalizado

El tema fue generado con Material Design Theme Builder
(m3.material.io/theme-builder), exportado en formato Jetpack Compose y
aplicado en la carpeta `ui/theme/`. Se adapta automaticamente al modo
claro u oscuro segun la configuracion del sistema operativo.

## Tecnologias utilizadas

- Lenguaje: Kotlin
- UI: Jetpack Compose
- Arquitectura: ViewModel + StateFlow
- Sistema de diseño: Material Design 3

## Como ejecutar la aplicacion

1. Clonar el repositorio:
   git clone https://github.com/seitan-moon/intro-prog-disp-mov-oto2026-grupo4-tp-1-final.git
2. Abrir la carpeta del proyecto con Android Studio
3. Esperar a que finalice la sincronizacion de Gradle
4. Conectar un dispositivo o emulador y ejecutar la app (boton Run)