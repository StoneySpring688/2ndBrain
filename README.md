# 🧠 2nd Brain

Un **Second Brain** personal organizado por tipo de nota, diseñado para capturar, organizar y conectar conocimiento técnico de manera eficiente.

## 🏗️ Estructura

Este repositorio está organizado por **propósito** en lugar de por tecnología, facilitando encontrar información según tu necesidad:

### 📁 Directorios principales

- **[📥 00-Inbox](./00-Inbox/)** - Captura rápida de información sin clasificar
- **[💡 10-Concepts](./10-Concepts/)** - Conocimiento atemporal: qué es y por qué importa
- **[🛠️ 20-HowTos](./20-HowTos/)** - Guías paso a paso y procedimientos
- **[⚡ 30-Snippets](./30-Snippets/)** - Código reutilizable organizado por lenguaje
- **[🚀 40-Projects](./40-Projects/)** - Documentación de proyectos activos
- **[🔬 50-Research](./50-Research/)** - Papers, experimentos y análisis
- **[🛠️ 60-Tools](./60-Tools/)** - Configuración y notas de herramientas
- **[📚 70-References](./70-References/)** - Enlaces curados y material de referencia
- **[📝 80-Journal](./80-Journal/)** - TILs, notas diarias y reflexiones
- **[🗃️ 99-Archive](./99-Archive/)** - Contenido obsoleto pero conservado

### 🎯 ¿Cómo encontrar lo que necesitas?

- **"¿Qué es X?"** → `10-Concepts/`
- **"¿Cómo hago Y?"** → `20-HowTos/`
- **"¿Tengo código para Z?"** → `30-Snippets/`
- **"¿Cómo documenté el proyecto W?"** → `40-Projects/`
- **"¿Qué dice la investigación sobre V?"** → `50-Research/`

## 📝 Convenciones

### YAML Frontmatter
Todas las notas incluyen metadatos estructurados:

```yaml
---
title: "Título descriptivo"
type: concept | howto | snippet | project | research | journal
tags: [area/domain, topic/specific, level/difficulty]
status: draft | active | final
last_reviewed: YYYY-MM-DD
---
```

### Sistema de etiquetas
Etiquetas jerárquicas para facilitar búsquedas:
- `area/frontend` - Área principal
- `topic/react-hooks` - Tema específico  
- `level/intermediate` - Nivel de dificultad
- `tool/docker` - Herramienta específica

## 🚀 Empezar

1. **Explorar estructura**: Revisa los directorios principales arriba
2. **Leer la guía**: Consulta [docs/STRUCTURE.md](./docs/STRUCTURE.md) para convenciones detalladas
3. **Usar plantillas**: Copia de [templates/](./templates/) para crear nuevas notas
4. **Contribuir**: Sigue el flujo de trabajo documentado

## 📚 Documentación

- **[📖 Guía completa de estructura](./docs/STRUCTURE.md)** - Convenciones, flujo de trabajo y mejores prácticas
- **[📄 Plantillas](./templates/)** - Templates para diferentes tipos de notas
- **[🗺️ Índices (MOCs)](./10-Concepts/INDEX.md)** - Maps of Content para navegación

## 🔄 Flujo de trabajo

1. **Captura** → Añadir información rápida a `00-Inbox/`
2. **Procesa** → Clasificar y mover a la sección apropiada
3. **Conecta** → Crear enlaces entre notas relacionadas
4. **Mantén** → Revisar y actualizar contenido regularmente

## 🎯 Contenido actual

### AI y Machine Learning
- Fundamentos de Deep Learning y Redes Neuronales
- Regresión logística y conceptos fundamentales

### Desarrollo Web
- HTML: Elementos, estructura y mejores prácticas
- CSS: Estilado, layout, responsive design y animaciones
- JavaScript: Conceptos core y patrones

## 🛠️ Herramientas recomendadas

- **[Obsidian](https://obsidian.md)** - Para navegación visual y enlaces
- **[VS Code](https://code.visualstudio.com)** - Con extensiones de Markdown
- **[Logseq](https://logseq.com)** - Para workflows basados en bloques

## 🔗 Links útiles

[W3School](https://www.w3schools.com/)

## 📜 Licencia

Este repositorio se distribuye bajo la licencia **Creative Commons Attribution 4.0 International (CC BY 4.0)**. 

📄 [Ver licencia completa](./LICENSE) | 🌐 [Más información](https://creativecommons.org/licenses/by/4.0/)

---

**🔗 Enlaces rápidos**: [Estructura completa](./docs/STRUCTURE.md) | [Plantillas](./templates/) | [Conceptos](./10-Concepts/) | [HowTos](./20-HowTos/) | [Snippets](./30-Snippets/)
