[![en](https://img.shields.io/badge/lang-en-blue.svg)](README.md)

# 🎮 ModeX Arcade

![Python](https://img.shields.io/badge/Python-3.11.4-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pygame](https://img.shields.io/badge/Pygame-2.6.1-00B140?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik04IDVsOCA3LTggN1Y1eiIvPjwvc3ZnPg==&logoColor=white)
![Arcade](https://img.shields.io/badge/Arcade-3.3.2-FF6B35?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik04IDVsOCA3LTggN1Y1eiIvPjwvc3ZnPg==&logoColor=white)
![Juegos](https://img.shields.io/badge/Juegos-4_Títulos-FF2DCE?style=for-the-badge&logo=steam&logoColor=white)
![FPS](https://img.shields.io/badge/Rendimiento-60_FPS-00D4FF?style=for-the-badge&logo=speedtest&logoColor=white)
![Sesiones](https://img.shields.io/badge/Playtesting-75_Sesiones-8B5CF6?style=for-the-badge&logo=testcafe&logoColor=white)
![Arquitectura](https://img.shields.io/badge/Arquitectura-Modular-FFD700?style=for-the-badge&logo=blueprint&logoColor=black)
![Versión](https://img.shields.io/badge/Versión-1.6-gold?style=for-the-badge)
![Concursos](https://img.shields.io/badge/Concursos-3-bronze?style=for-the-badge&logo=trophy&logoColor=white)

Un **sistema arcade modular** desarrollado en Python usando las bibliotecas Pygame y Arcade. ModeX integra cuatro juegos 2D con mecánicas distintas en un único ejecutable standalone, validando que Python puede alcanzar 60 FPS estables en hardware convencional sin motores comerciales.

---

## 🎬 Vista Previa

<div align="center">
  <img src="assets/gifs/preview.gif" alt="ModeX Arcade Vista Previa"/>
</div>


---

## 👨‍💻 Información del Equipo

| Rol | Nombre | Correo |
|-----|--------|--------|
| Desarrollador e Investigador | Magallanes López Carlos Gabriel | cgmagallanes23@gmail.com |
| Desarrollador e Investigador | Barrón Pando Kevin Zaid | — |

---

## 🎯 Descripción del Proyecto

ModeX Arcade es un **proyecto de investigación tecnológica** que responde una pregunta central:

> *¿Es técnicamente viable desarrollar videojuegos 2D de calidad profesional en Python con bibliotecas open-source, alcanzando 60 FPS estables en hardware convencional?*

La respuesta, respaldada por datos de 75 sesiones de playtesting, es **sí**.

El sistema integra cuatro juegos de distintos géneros — carreras, plataformas, peleas y shooter cooperativo — todos compartiendo una arquitectura modular común, un sistema de medición automática de rendimiento y un ejecutable standalone que no requiere instalación de Python.

---

## 🕹️ Juegos

| Juego | Género | Biblioteca |
|-------|--------|------------|
| 🏎️ **Neon Rush** | Carreras top-down | Arcade |
| 🌌 **Cosmic Odyssey** | Plataformas 2D | Arcade |
| ⚔️ **The Ghost Tsushima** | Peleas 1v1 | Pygame |
| 🧟 **The Past Z** | Shooter cooperativo de zombies | Pygame |

---

## 📊 Resultados de Rendimiento

Resultados de **75 sesiones de playtesting** (25 por juego) en un Intel Core i5 8.ª gen., 8 GB RAM, Intel UHD 630:

| Juego | FPS Promedio | FPS Mediana | Desv. Estándar | Caídas de Frame |
|-------|-------------|-------------|----------------|-----------------|
| Peleas | **60.41** | 60.45 | 0.75 | 0.00% |
| Plataformas | **58.75** | 58.79 | 1.05 | 0.21% |
| Carreras | **58.10** | 58.10 | 1.20 | 2.90%* |

> \*Las caídas en Carreras son exclusivamente por picos de carga sincrónica en transiciones de nivel (~2,237 ms y ~2,791 ms). La mediana en condiciones normales es 58.10 FPS.

**Memoria:** 50 MB RAM constantes en todos los juegos y sesiones. **0 fugas de memoria detectadas.**

---

## 🔧 Arquitectura y Optimizaciones

```
ModeXArcade/
├── main.py                  ← Punto de entrada
├── utils/
│   ├── singleton.py         ← Metaclase Singleton
│   ├── paths.py             ← Resolución de rutas absolutas
│   └── colors.py            ← Constantes de color
├── games/
│   ├── neon_rush/           ← Juego de carreras (Arcade)
│   ├── cosmic_odyssey/      ← Plataformas (Arcade)
│   ├── ghost_tsushima/      ← Juego de peleas (Pygame)
│   └── the_past_z/          ← Shooter (Pygame)
├── assets/                  ← Assets compartidos
└── state/                   ← Persistencia SQLite
```

### Optimizaciones clave aplicadas
- **Object pooling** — Reutilización de instancias de balas y partículas
- **Sprite batching** — Agrupación de draw calls para reducir viajes a la GPU
- **Spatial culling** — Omitir actualización/renderizado de entidades fuera del viewport
- **Spatial hashing** — Evitar cálculos de colisión redundantes para objetos estáticos
- **`__slots__`** — Almacenamiento de atributos de tamaño fijo eliminando el overhead del dict por instancia
- **`functools.lru_cache`** — Memoización para funciones recursivas costosas

---

## 🏆 Resultados en Concursos

| Concurso | Fecha | Versión | Resultado |
|----------|-------|---------|-----------|
| Concurso Local de Prototipos (DGETI) | 25–26 Nov 2025 | v1.2 | 🥈 2.° Lugar — Software |
| Concurso Estatal 26-AS3414 | 11–13 Mar 2026 | v1.5 | 🥉 3.° Lugar — Software |
| Hackathon TecMilenio | 22 Abr 2026 | v1.6 | 🥉 3.° Lugar — STEAM |

---

## 🧪 Metodología

La investigación sigue una metodología **RAD (Rapid Application Development)** adaptada con ciclos iterativos de 2 semanas. El diseño de recolección de datos es **cuantitativo evaluativo-experimental**.

### Métricas recopiladas por sesión (cada 2 segundos, automáticamente)
- FPS instantáneo / promedio / mínimo histórico
- Percentiles 1 y 99 de FPS
- Desviación estándar de FPS
- Tiempo de frame (ms)
- Consumo de RAM
- Datos del recolector de basura (GC)
- Conteo de entidades activas
- Draw calls estimados
- Frecuencia de caídas de frame consecutivas

---

## 💡 Propuesta de Valor

| Aspecto | ModeX | Unity | Unreal Engine |
|---------|-------|-------|---------------|
| Costo de software | **$0 MXN** | Requiere licencia | Requiere licencia |
| Requisito de RAM | **8 GB** | 8 GB (mín) | 32 GB (recomendado) |
| Tamaño de instalación | **250 MB** | Varios GB | Varios GB |
| Curva de aprendizaje | Baja (Python) | Media–Alta | Alta |
| Replicabilidad | Documentación completa | Limitada | Limitada |

---

## 🛠️ Stack Tecnológico

| Tecnología | Versión | Propósito |
|------------|---------|-----------|
| Python | 3.11.4 | Lenguaje base |
| Pygame | 2.6.1 | Juegos de peleas y shooter |
| Arcade | 3.3.2 | Juegos de carreras y plataformas |
| Tiled Map Editor | — | Diseño de niveles (TMX) |
| SQLite | Integrado | Persistencia de puntajes y estado |
| PyInstaller | — | Empaquetado en .exe standalone |
| Pytest | — | Pruebas unitarias |

---

## ⚙️ Requisitos del Sistema

| Componente | Mínimo |
|------------|--------|
| Procesador | Intel Core i5 (8.ª gen.) o equivalente |
| RAM | 8 GB |
| Gráficos | Intel UHD 620/630 o GPU integrada equivalente |
| Almacenamiento | 250 MB |
| Sistema Operativo | Windows 10 / 11 |

---

## ▶️ Cómo Ejecutar

```bash
# Descarga la última versión en Releases
# Ejecuta directamente — no requiere instalación de Python
ModeX_Arcade_v1.6.exe
```

---

## 📚 Documentación

Todos los documentos están disponibles en el [sitio web del proyecto](https://modex-arcade-26-as3414.netlify.app/).

| Documento | Descripción |
|-----------|-------------|
| 📊 Documento de Investigación | Análisis de rendimiento de 75 sesiones y validación de hipótesis |
| 🔧 Documentación Técnica | Arquitectura del sistema, patrones de diseño, diagramas UML (26 páginas) |
| 📖 Manual de Usuario | Guía completa de juego y controles |
| ⚙️ Manual de Instalación | Configuración, requisitos y solución de problemas |
| 📓 Bitácora | Registro cronológico del desarrollo |

---

## 📈 Cronología de Desarrollo

```
Feb 2025  → Algoritmos, diagramas de flujo y fundamentos de C++
Abr 2025  → Zhyniria: primer juego (C++, proyecto de clase)
Sep 2025  → ModeX v1.0: Singleton, logging, utils, Neon Rush
Oct 2025  → ModeX v1.1: Cosmic Odyssey, The Ghost Tsushima
Nov 2025  → ModeX v1.2: The Past Z, primer ejecutable .bat
Nov 2025  → 🥈 Concurso Local: 2.° Lugar
Dic 2025  → ModeX v1.3: SQLite, vistas rediseñadas, ventana redimensionable
Ene 2026  → ModeX v1.4: Optimizaciones globales de rendimiento
Feb 2026  → ModeX v1.5: 75 sesiones de playtesting, .exe, documentación completa
Mar 2026  → 🥉 Concurso Estatal: 3.° Lugar
Abr 2026  → ModeX v1.6 → 🥉 Hackathon TecMilenio: 3.° Lugar STEAM
```

---

## 🔗 Enlaces

- 🌐 **Sitio Web:** [modex-arcade-26-as3414.netlify.app](https://modex-arcade-26-as3414.netlify.app/)
- 📦 **Releases:** [github.com/TheNarratorVIMMXX/ModeXArcade/releases](https://github.com/TheNarratorVIMMXX/ModeXArcade/releases)
- 📧 **Contacto:** cgmagallanes23@gmail.com

---

⭐ **Un sistema arcade modular en Python que demuestra que los lenguajes interpretados pueden alcanzar rendimiento de calidad profesional en videojuegos 2D sin motores comerciales.**
