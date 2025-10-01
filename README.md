# Calculadora de Gastos Personales

Aplicación para registrar y controlar **gastos diarios**.

## Entrega 2 (UI terminada)
- Estructura del repositorio alineada a clase.
- Mockups (imágenes o Figma) en `docs/mockups/`.
- Prototipo web en `prototype/`.
- Proyecto Android (UI con Jetpack Compose) en `android-app/` (sin lógica todavía).
- Persistencia **Room** planificada (ver `docs/modelo_datos.md`).

## Estructura del repo
```
docs/               Documentación del proyecto
  ├─ ideas.md
  ├─ funcionalidades.md
  ├─ diseno_ui.md
  ├─ modelo_datos.md       ← Modelo de datos para Room
  └─ mockups/              ← Imágenes exportadas / enlaces Figma
prototype/
  └─ index.html            ← Prototipo interactivo (HTML/JS)
android-app/               ← Proyecto Android Studio (Jetpack Compose)
```

## Cómo ver el prototipo
- Abre `prototype/index.html` en el navegador (doble clic).

## Próximos pasos (Android Studio)
- Replicar vistas con **Jetpack Compose** (`Column`, `LazyColumn`, `FloatingActionButton`).
- Navegación con `NavHost`.
- Estado con `ViewModel`.
- Persistencia con **Room** (ver `docs/modelo_datos.md`).
