# 📝 Journal

TILs (Today I Learned), diarios de desarrollo, notas de reuniones y material volátil que puede evolucionar hacia contenido estructurado.

## 🎯 Propósito

- Captura de aprendizajes diarios y descubrimientos
- Notas de reuniones y conversaciones técnicas
- Reflexiones sobre el progreso en proyectos
- Material "en bruto" que puede refinarse posteriormente

## 📅 Organización temporal

El contenido del journal puede organizarse de varias formas:

### Por fecha
- `2025-01-15-docker-networking-til.md`
- `2025-01-16-meeting-architecture-review.md`

### Por tipo
- `tils/` - Today I Learned entries
- `meetings/` - Notas de reuniones
- `reflections/` - Reflexiones y análisis

### Por proyecto
- `project-alpha/daily-notes/`
- `project-beta/standups/`

## 📝 Convenciones

- **Formato fecha**: YYYY-MM-DD para ordenación cronológica
- **Títulos descriptivos**: Que permitan identificar el contenido rápidamente
- **Etiquetas útiles**: Usar YAML frontmatter para facilitar búsquedas
- **Contenido honesto**: No pulir demasiado, mantener autenticidad
- **Enlaces a futuro**: Conectar con material más estructurado cuando aplique

## 🔄 Evolución del contenido

El journal actúa como "semillero" de contenido más estructurado:

- **TIL importante** → Puede convertirse en **Concept** o **HowTo**
- **Notas de reunión** → Pueden generar **Project documentation**
- **Experimento personal** → Puede documentarse como **Research**
- **Problema resuelto** → Puede convertirse en **Snippet** o **HowTo**

## 🎯 Ejemplos de contenido

- TIL: Descubrí que Docker tiene un flag `--init` para manejar procesos zombie
- Meeting: Revisión de arquitectura - decisiones sobre base de datos
- Reflection: Lo que aprendí implementando autenticación OAuth
- Debug session: Rastreando un memory leak en producción

## 🏷️ Estructura sugerida

```
80-Journal/
├── 2025/
│   ├── 01-january/
│   │   ├── 2025-01-15-docker-networking-til.md
│   │   ├── 2025-01-16-oauth-implementation-notes.md
│   │   └── 2025-01-17-team-meeting-Q1-planning.md
│   └── 02-february/
├── tils/
├── meetings/
└── reflections/
```

## 🔗 Enlaces útiles

- [Guía de estructura](../docs/STRUCTURE.md)
- [Template básico](../templates/Journal.md)