# 🗃️ Archive

Material congelado, obsoleto o que ya no es relevante. Contenido que se mantiene por valor histórico pero no se actualiza activamente.

## 🎯 Propósito

- Preservar contenido que ya no es relevante pero tiene valor histórico
- Evitar eliminar conocimiento que podría ser útil en el futuro
- Mantener el registro de evolución del conocimiento personal
- Liberar espacio en las secciones activas

## 📦 Qué archivar

### ✅ Candidatos para archivo

- **Tecnologías obsoletas**: Frameworks, herramientas o versiones descontinuadas
- **Proyectos completados**: Documentación de proyectos finalizados sin mantenimiento
- **Notas temporales**: Información que perdió relevancia temporal
- **Enfoques superados**: Métodos o técnicas reemplazadas por mejores alternativas
- **Contenido duplicado**: Cuando se consolida información en otras secciones

### ❌ No archivar

- **Conceptos fundamentales**: Principios atemporales que siguen siendo válidos
- **Documentación activa**: Material que se consulta o actualiza regularmente
- **Referencias vigentes**: Enlaces y recursos que siguen siendo útiles

## 📝 Proceso de archivado

1. **Marcar como obsoleto**: Añadir nota de deprecación en el archivo original
2. **Mover a archivo**: Preservar estructura original dentro de `99-Archive/`
3. **Actualizar índices**: Remover referencias en INDEX.md de secciones activas
4. **Documentar motivo**: Explicar por qué se archiva y cuándo

## 🏷️ Estructura de archivo

Preservar la estructura original para facilitar navegación histórica:

```
99-Archive/
├── archived-2025/
│   ├── old-concepts/
│   │   └── jquery-patterns.md  # [ARCHIVED 2025-01] jQuery obsoleto
│   ├── deprecated-tools/
│   │   └── gulp-config.md      # [ARCHIVED 2025-01] Migrado a Vite
│   └── completed-projects/
│       └── blog-v1/            # [ARCHIVED 2025-01] Reemplazado por v2
├── archived-2024/
└── README.md                   # Índice del archivo con fechas y motivos
```

## 📝 Convenciones de archivado

- **Prefijo de fecha**: `[ARCHIVED YYYY-MM]` en el título o metadatos YAML
- **Motivo del archivo**: Explicar brevemente por qué se archiva
- **Referencias**: Enlazar a contenido de reemplazo cuando exista
- **Preservar formato**: Mantener el contenido original sin modificaciones importantes

## 🔍 Ejemplo de nota archivada

```markdown
---
title: "[ARCHIVED 2025-01] Configuración de Webpack 4"
type: archived
original_type: howto
archived_date: 2025-01-15
archived_reason: "Webpack 4 obsoleto, migrado a Vite"
replacement: "../20-HowTos/dev-environments/vite-setup.md"
tags: [archived, webpack, build-tools]
---

# [ARCHIVADO] Configuración de Webpack 4

**⚠️ NOTA DE ARCHIVO**: Este contenido se archivó el 2025-01-15. 
Webpack 4 ya no se usa en proyectos nuevos. Ver [configuración de Vite](../20-HowTos/dev-environments/vite-setup.md) como alternativa moderna.

[Contenido original preservado...]
```

## 🔗 Enlaces útiles

- [Guía de estructura](../docs/STRUCTURE.md)
- [Proceso de mantenimiento](../docs/STRUCTURE.md#mantenimiento)