# Brick

Un proyecto Flutter que implementa una arquitectura limpia (Clean Architecture) con enrutamiento básico sin dependencias externas.

## 🏗️ Arquitectura

Este proyecto sigue los principios de Clean Architecture organizando el código en capas bien definidas:

```
lib/
├── src/
│   ├── config/           # Configuración de la app
│   │   ├── route/        # Enrutamiento básico
│   │   └── theme/        # Temas claro y oscuro
│   ├── core/             # Elementos centrales
│   │   ├── interfaces/   # Contratos/abstracciones
│   │   └── util/         # Utilidades (DataState, Enums)
│   ├── data/             # Capa de datos
│   │   ├── datasource/   # Fuentes de datos
│   │   ├── models/       # Modelos de datos
│   │   └── repository/   # Implementaciones de repositorios
│   ├── domain/           # Capa de dominio
│   │   ├── contracts/    # Interfaces de repositorios
│   │   ├── entity/       # Entidades de negocio
│   │   └── usecase/      # Casos de uso
│   └── presentation/     # Capa de presentación
│       ├── pages/        # Pantallas
│       └── widgets/      # Widgets reutilizables
```

## 🚀 Características

- **Enrutamiento básico**: Sistema de navegación implementado con `onGenerateRoute` sin paquetes externos
- **Arquitectura limpia**: Separación clara de responsabilidades entre capas
- **Estado de datos tipado**: `DataState<T>` con variantes `DataSuccess` y `DataFailure`
- **Casos de uso**: Interfaces `IUseCaseQuery` e `IUseCaseCommand` para lógica de negocio
- **Temas**: Soporte para tema claro y oscuro
- **Sin dependencias externas**: Solo Flutter SDK y herramientas de desarrollo

## 📱 Pantallas

- **Home Screen**: Pantalla principal con navegación a Details
- **Details Screen**: Pantalla de ejemplo con navegación de regreso

## 🛠️ Tecnologías

- **Flutter**: SDK 3.9.2+
- **Dart**: Lenguaje de programación
- **Material Design**: Componentes de UI

## 🚦 Navegación

El proyecto implementa un sistema de enrutamiento básico:

```dart
// Rutas disponibles
'/' → HomeScreen
'/details' → DetailsScreen
// Cualquier otra ruta → Pantalla 404
```

## 📦 Estructura de Estado

```dart
sealed class DataState<T> {
  const DataState();
}

class DataSuccess<T> extends DataState<T> {
  final T data;
  const DataSuccess(this.data);
}

class DataFailure<T> extends DataState<T> {
  final Exception error;
  const DataFailure(this.error);
}
```

## 🎯 Casos de Uso

```dart
abstract class IUseCaseQuery<T, P> {
  Future<T> call(P params);
}

abstract class IUseCaseCommand<T> {
  Future<T> call();
}
```

## 🎨 Temas

Soporte para tema claro y oscuro configurado en `AppTheme`:

```dart
ThemeData lightTheme = AppTheme.lightTheme;
ThemeData darkTheme = AppTheme.darkTheme;
```

## 🚀 Cómo ejecutar

1. Clona el repositorio
2. Ejecuta `flutter pub get`
3. Ejecuta `flutter run`

## 📝 Notas

- Este proyecto está diseñado como una plantilla base para aplicaciones Flutter con arquitectura limpia
- No utiliza paquetes externos para el enrutamiento, manteniendo la simplicidad
- La estructura está preparada para escalar con nuevas funcionalidades siguiendo los principios de Clean Architecture
