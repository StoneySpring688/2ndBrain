# 🧠 2nd Brain - Guía de Estructura

Esta guía explica la organización, convenciones y mejores prácticas para mantener este Second Brain técnico.

## 🏗️ Filosofía de organización

El repositorio está estructurado por **tipo de nota** en lugar de por tecnología, permitiendo encontrar información según el **propósito** de uso:

- **¿Qué es esto?** → `10-Concepts/`
- **¿Cómo hago esto?** → `20-HowTos/`
- **¿Tengo código para esto?** → `30-Snippets/`
- **¿Cómo documenté este proyecto?** → `40-Projects/`
- **¿Qué dice la investigación sobre esto?** → `50-Research/`
- **¿Cómo configuro esta herramienta?** → `60-Tools/`
- **¿Dónde están las referencias?** → `70-References/`
- **¿Qué aprendí recientemente?** → `80-Journal/`

## 📁 Estructura de directorios

```
/
├── 00-Inbox/                  # Capturas rápidas sin clasificar
├── 10-Concepts/               # Conocimiento atemporal (qué/por qué)
│   ├── programming-languages/ # Lenguajes de programación
│   ├── software-engineering/  # Ingeniería de software
│   ├── systems/              # Sistemas y arquitecturas
│   ├── data/                 # Datos y bases de datos
│   ├── ai-ml/                # Inteligencia artificial y ML
│   ├── cloud-devops/         # Cloud computing y DevOps
│   └── INDEX.md
├── 20-HowTos/                # Procedimientos paso a paso
│   ├── dev-environments/     # Setup de entornos de desarrollo
│   ├── automation/           # Scripts y automatización
│   ├── troubleshooting/      # Resolución de problemas
│   └── INDEX.md
├── 30-Snippets/              # Código reutilizable
│   ├── js/                   # JavaScript/TypeScript
│   ├── python/               # Python
│   ├── bash/                 # Shell scripts
│   ├── sql/                  # SQL
│   └── INDEX.md
├── 40-Projects/              # Documentación de proyectos
├── 50-Research/              # Investigación y análisis
│   ├── papers/               # Resúmenes de papers
│   ├── experiments/          # Experimentos técnicos
│   ├── benchmarks/           # Comparativas y benchmarks
│   └── INDEX.md
├── 60-Tools/                 # Configuración de herramientas
│   ├── editors/              # Editores de código
│   ├── terminals/            # Terminal y shell
│   ├── git/                  # Git y control de versiones
│   ├── observability/        # Monitoreo y debugging
│   └── INDEX.md
├── 70-References/            # Referencias y enlaces curados
├── 80-Journal/               # TILs, notas diarias, reflexiones
├── 99-Archive/               # Contenido obsoleto o histórico
├── docs/                     # Documentación del repositorio
│   └── STRUCTURE.md          # Esta guía
├── templates/                # Plantillas de notas especializadas
│   ├── Concept-Programming.md   # Conceptos específicos de programación
│   ├── Concept-Software-Engineering.md  # Arquitectura, patrones, metodologías
│   ├── Concept-Algorithm.md     # Algoritmos y estructuras de datos
│   ├── Concept-AI-ML.md        # Conceptos de IA/ML unificados
│   ├── Concept-Mathematics.md   # Conceptos matemáticos formales
│   ├── HowTo-Development.md     # Guías de desarrollo y workflows
│   ├── Project-Data-Science.md  # Proyectos de ML/DS
│   ├── Snippet.md              # Fragmentos de código
│   ├── Project.md              # Proyectos generales
│   └── Research.md             # Papers y estudios
└── README.md
```

## 📝 YAML Frontmatter

### ¿Qué es el frontmatter?

El YAML frontmatter es un bloque de metadatos al inicio de los archivos Markdown, delimitado por líneas `---`. Facilita la búsqueda, filtrado y organización automática del contenido.

### Campos estándar

Todos los archivos deben incluir estos campos básicos:

```yaml
---
title: "Título descriptivo y único"
type: concept | howto | snippet | project | research | journal
tags: [area/domain, topic/specific, level/difficulty]
status: draft | active | final
last_reviewed: YYYY-MM-DD
---
```

### Descripción de campos

- **`title`**: Título humano-legible de la nota (único dentro de su tipo)
- **`type`**: Tipo de nota según la estructura de directorios
- **`tags`**: Lista de etiquetas jerárquicas para facilitar búsquedas
- **`status`**: Estado de la nota
  - `draft`: Contenido en desarrollo, puede estar incompleto
  - `active`: Contenido completo y actualizado
  - `final`: Contenido completado que no requiere actualizaciones frecuentes
- **`last_reviewed`**: Última fecha de revisión (formato ISO: YYYY-MM-DD)

### Campos opcionales por tipo

#### Concepts
```yaml
related_concepts: [concept1, concept2]  # Enlaces a conceptos relacionados
difficulty: beginner | intermediate | advanced
domain: programming | systems | data    # Dominio principal
```

#### HowTos
```yaml
prerequisites: [tool1, tool2]           # Herramientas o conocimiento necesario
estimated_time: "30 minutes"           # Tiempo estimado de ejecución
platforms: [macos, linux, windows]     # Plataformas compatibles
last_tested: YYYY-MM-DD                # Última vez que se probó el procedimiento
```

#### Snippets
```yaml
language: javascript | python | bash | sql
dependencies: [library1, library2]      # Dependencias externas
use_cases: [case1, case2]              # Casos de uso típicos
```

#### Projects
```yaml
status: planning | active | completed | archived
tech_stack: [tech1, tech2]            # Tecnologías utilizadas
repository: "https://github.com/..."   # Enlace al código
```

#### Research
```yaml
source: "https://paper-url"            # Fuente original
authors: [author1, author2]            # Autores del material original
publication_date: YYYY-MM-DD           # Fecha de publicación original
research_type: paper | experiment | benchmark
```

## 🏷️ Sistema de etiquetas

### Estructura jerárquica

Las etiquetas siguen un patrón jerárquico para facilitar la organización:

```
area/domain          # Área principal
topic/specific       # Tema específico
level/difficulty     # Nivel de dificultad
tool/technology      # Herramienta o tecnología
platform/os          # Plataforma o sistema operativo
```

### Ejemplos de etiquetas

```yaml
# Para un concepto sobre React Hooks
tags: [area/frontend, topic/react, topic/hooks, level/intermediate]

# Para un HowTo de configuración de Docker en macOS
tags: [tool/docker, platform/macos, topic/containerization, level/beginner]

# Para un snippet de Python para APIs
tags: [lang/python, topic/api, topic/requests, level/intermediate]
```

### Convenciones de etiquetado

- **Usar kebab-case**: `machine-learning` en lugar de `Machine Learning`
- **Ser específico**: `topic/react-hooks` es mejor que `topic/react`
- **Jerarquía consistente**: Mantener el orden área > tema > nivel > herramienta
- **Evitar duplicados**: Una etiqueta por concepto, no usar `js` y `javascript`

## 📚 Maps of Content (MOCs)

### ¿Qué son los MOCs?

Los Maps of Content son archivos INDEX.md que actúan como índices temáticos, proporcionando navegación estructurada y resúmenes de contenido disponible.

### Estructura de un INDEX.md

```markdown
# 📁 Título de la sección

Breve descripción del propósito y alcance de esta sección.

## 🎯 Propósito

- Punto clave 1
- Punto clave 2

## 📝 Contenido disponible

### Subcategoría 1
- [Nota importante 1](./nota1.md) - Descripción breve
- [Nota importante 2](./nota2.md) - Descripción breve

### Subcategoría 2
- [Otra nota](./nota3.md) - Descripción breve

## 🔗 Enlaces relacionados

- [Sección relacionada](../otra-seccion/)
- [Herramientas útiles](../60-Tools/categoria/)
```

### Mantenimiento de MOCs

- **Actualizar al añadir contenido**: Cada nueva nota debe referenciarse en su INDEX.md
- **Organizar por importancia**: Listar primero el contenido más útil o fundamental
- **Describir brevemente**: Una línea explicando qué contiene cada nota
- **Enlaces cruzados**: Conectar con contenido relacionado en otras secciones

## 🔄 Flujo de trabajo

### 1. Captura inicial (Inbox)

```
Idea/Información nueva → 00-Inbox/ → Procesamiento → Ubicación final
```

### 2. Procesamiento del Inbox

**Frecuencia**: Semanal o cuando se acumule contenido

**Proceso**:
1. Revisar cada item en `00-Inbox/`
2. Determinar tipo de nota según su naturaleza
3. Completar con YAML frontmatter apropiado
4. Mover a la sección correspondiente
5. Actualizar INDEX.md de la sección de destino
6. Crear enlaces cruzados si es relevante

### 3. Creación de nuevas notas

1. **Elegir ubicación**: Según el tipo de contenido
2. **Usar plantilla**: Copiar de `templates/` la plantilla apropiada
3. **Completar frontmatter**: Todos los campos obligatorios
4. **Escribir contenido**: Seguir convenciones de la sección
5. **Actualizar INDEX.md**: Añadir referencia a la nueva nota
6. **Enlaces cruzados**: Conectar con contenido relacionado

### 4. Mantenimiento y revisión

**Mensual**:
- Revisar notas con `status: draft` y actualizar
- Verificar enlaces rotos
- Actualizar fechas `last_reviewed` de contenido revisado

**Trimestral**:
- Evaluar contenido para posible archivo en `99-Archive/`
- Consolidar información duplicada
- Optimizar estructura de etiquetas

**Anual**:
- Revisión completa de estructura
- Actualización de plantillas y guías
- Reorganización si es necesario

## 📖 Convenciones de escritura

### Nombres de archivos

- **Formato**: `kebab-case` con extensión `.md`
- **Descriptivos**: El nombre debe indicar claramente el contenido
- **Únicos**: Evitar nombres duplicados dentro de la misma sección
- **Sin números**: Evitar prefijos numéricos a menos que indiquen secuencia

**Ejemplos**:
```
✅ javascript-promises-guide.md
✅ docker-setup-macos.md
✅ sql-query-optimization.md

❌ 1-intro.md
❌ notes.md
❌ temp_file.md
```

### Títulos y estructura

- **Título principal**: Una sola línea clara y descriptiva
- **Subtítulos**: Estructura jerárquica lógica (H2, H3, H4)
- **Consistencia**: Mismo estilo de títulos en toda la sección
- **Emojis opcionales**: Para mayor claridad visual en títulos

### Enlaces

- **Internos**: Usar rutas relativas `../section/file.md`
- **Externos**: Enlaces completos con descripción clara
- **Wikilinks**: Opcional, pero ser consistente en su uso
- **Actualizables**: Revisar periodicamente la validez

### Formato de código

```markdown
# Código inline
Usar `backticks` para código inline

# Bloques de código
```javascript
// Especificar el lenguaje para syntax highlighting
function example() {
  return "hello world";
}
```

# Comandos de terminal
```bash
# Incluir comentarios explicativos
npm install --save-dev typescript
```
```

## 🔧 Herramientas recomendadas

### Editores compatibles

- **Obsidian**: Excelente soporte para wikilinks y gráfico de relaciones
- **Logseq**: Enfoque en bloques con buen soporte para YAML
- **VS Code**: Con extensiones para Markdown y YAML
- **Notion**: Para usuarios que prefieren interfaces visuales

### Extensiones útiles

**VS Code**:
- Markdown All in One
- YAML Language Support
- Foam (para Second Brain workflows)

**Obsidian**:
- Templater (para plantillas avanzadas)
- Dataview (para consultas automáticas)
- Tag Wrangler (gestión de etiquetas)

### Scripts de automatización

**Validación de frontmatter**:
```bash
# Script para verificar que todos los .md tienen frontmatter válido
find . -name "*.md" -exec grep -L "^---" {} \;
```

**Generación de índices**:
```bash
# Script para generar automáticamente listas de archivos por sección
ls 10-Concepts/**/*.md | sed 's/.md$//' | sort
```

## ❓ FAQ

### ¿Dónde pongo una nota que podría ir en varias secciones?

Elige la sección según el **uso principal**:
- Si la consultas para entender un concepto → `10-Concepts/`
- Si la usas como guía de acción → `20-HowTos/`
- Si contiene código reutilizable → `30-Snippets/`

Luego crea **enlaces cruzados** desde las otras secciones.

### ¿Cómo manejo contenido que evoluciona rápidamente?

1. **Captura inicial**: `80-Journal/` para apuntes rápidos
2. **Desarrollo**: Mover a sección apropiada cuando se estabilice
3. **Mantenimiento**: Actualizar `last_reviewed` regularmente
4. **Archivo**: Mover a `99-Archive/` cuando quede obsoleto

### ¿Es obligatorio usar todas las etiquetas?

No, pero **sí es obligatorio**:
- `title`, `type`, `status`, `last_reviewed` en frontmatter
- Al menos una etiqueta de área/dominio
- Enlace en el INDEX.md correspondiente

### ¿Puedo cambiar la estructura?

Sí, pero **con cuidado**:
- Actualizar todos los enlaces afectados
- Modificar plantillas si es necesario
- Documentar cambios en commits
- Avisar si trabajas en equipo

### ¿Qué hago con contenido duplicado?

1. **Identificar el mejor contenido** (más completo, actualizado)
2. **Consolidar información** única del duplicado
3. **Crear enlaces** desde ubicaciones lógicas
4. **Archivar o eliminar** duplicados
5. **Actualizar índices** correspondientes

## 🔄 Evolución de esta guía

Esta guía está viva y debe evolucionar con el uso:

- **Feedback**: Documentar problemas o mejoras necesarias
- **Actualizaciones**: Reflejar cambios en la estructura
- **Ejemplos**: Añadir casos de uso reales conforme surjan
- **Automatización**: Mejorar herramientas y scripts de apoyo

---

**Última actualización**: 2025-01-18  
**Próxima revisión programada**: 2025-04-18