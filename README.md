# 📱 Animedex

**Animedex** es una aplicación Android desarrollada en Kotlin que permite a los usuarios explorar y gestionar información de animes mediante una interfaz moderna e intuitiva. La aplicación se complementa con una API REST propia construida con FastAPI y una base de datos PostgreSQL. El objetivo principal es permitir al usuario visualizar animes, agregarlos a favoritos, clasificarlos por estado y consultar estadísticas personalizadas de uso.

---

## 📦 Estructura del proyecto

```
dcmerida-animedex/
├── Animedex-App/               # Aplicación Android
│   ├── app/
│   │   ├── src/
│   │   │   ├── main/
│   │   │   │   ├── java/com/example/animedex/
│   │   │   │   │   ├── activities/              # Actividades principales (Main, Splash)
│   │   │   │   │   ├── fragments/               # Fragments de la app (Home, Search, Lists, Detail, Analytics)
│   │   │   │   │   ├── adapters/                # Adaptadores para RecyclerViews
│   │   │   │   │   ├── models/                  # Modelos de datos para animes y favoritos
│   │   │   │   │   ├── network/                 # Cliente Retrofit y servicio API
│   │   │   │   │   ├── datastore/               # Gestión de preferencias y estadísticas con DataStore
│   │   │   │   │   └── utils/                   # Utilidades generales
│   │   │   │   └── res/                         # Recursos gráficos y layouts XML
│   │   │   └── AndroidManifest.xml              # Declaración de componentes Android
│   └── build.gradle                             # Configuración del módulo
│
└── api+bbdd/                  # Backend con FastAPI y base de datos
    ├── API/
    │   ├── main.py            # Entrypoint de FastAPI
    │   ├── db.py              # Conexión y gestión de la base de datos PostgreSQL
    │   ├── models.py          # Definición de tablas SQLAlchemy
    │   ├── schemas.py         # Esquemas de entrada/salida con Pydantic
    │   ├── anime_db_backup.sql# Dump SQL de respaldo de la BBDD
    │   └── docker-compose.yaml# Orquestación de API y BBDD con Docker
```

---

## 🎯 Funcionalidades destacadas

- 🔍 Búsqueda de animes por título mediante API externa.
- 🏆 Visualización de animes populares y actualmente en emisión.
- ❤️ Añadir animes a favoritos con seguimiento del número de visitas.
- 📋 Clasificación de favoritos por estado: Planned / Watching / Watched.
- 📊 Visualización de estadísticas personalizadas (animes más vistos, favoritos).
- 💾 Persistencia local de configuraciones y contadores con Jetpack DataStore.
- 🔗 Consumo combinado de APIs externas públicas y una API propia privada.

---

## 🧩 Tecnologías utilizadas

### Android App

- Kotlin
- Android Jetpack: Fragments, ViewModel, Navigation, Lifecycle
- Retrofit + Gson (para llamadas HTTP REST)
- Glide (para carga de imágenes)
- MPAndroidChart (para visualización de gráficos)
- Jetpack DataStore (persistencia de preferencias)
- RecyclerView + ViewBinding

### Backend API

- Python 3.10
- FastAPI
- PostgreSQL
- SQLAlchemy
- Pydantic
- Docker y Docker Compose

---

## 🛠 Componentes principales

### App Android

- `MainActivity.kt`: Actividad principal que controla la navegación entre fragments.
- `SplashActivity.kt`: Pantalla de inicio de carga.
- `HomeFragment.kt`: Consulta y muestra animes populares y en emisión.
- `SearchFragment.kt`: Permite al usuario buscar animes por título.
- `ListsFragment.kt`: Muestra los animes favoritos, filtrados por estado (Planned, Watching, Watched).
- `AnimeDetailFragment.kt`: Muestra detalles completos del anime seleccionado, incluyendo botones para marcar como favorito y cambiar estado.
- `AnalyticsFragment.kt`: Carga y muestra gráficas personalizadas generadas localmente.
- `UserPreferences.kt`: Gestión de contadores y preferencias usando Jetpack DataStore.
- `AnimeService.kt`: Interfaz Retrofit para la comunicación con la API REST personalizada.

### API Backend

- `main.py`: Inicializa y expone los endpoints de la API FastAPI.
- `models.py`: Define la estructura de las tablas `Anime`, `Fav`, etc.
- `schemas.py`: Define los modelos de entrada/salida para validación de datos.
- `db.py`: Establece la conexión con PostgreSQL y operaciones básicas.
- `docker-compose.yaml`: Lanza los servicios de API y base de datos de forma conjunta.
- `anime_db_backup.sql`: Backup para restaurar los datos iniciales.

---

## 📊 Estadísticas y visualización

- Se registran automáticamente las visitas a cada anime cuando se consultan.
- La app muestra:
  - Una gráfica de barras con los 5 animes más consultados.
  - Una gráfica circular comparando animes favoritos vs no favoritos.
- Las estadísticas se renderizan con MPAndroidChart en `AnalyticsFragment.kt`.

---

## 📝 Licencia

MIT License  
© 2025 Daniel Mérida Cordero
