# Templates para 2nd Brain

Esta carpeta contiene plantillas (templates) especializadas para diferentes tipos de contenido y dominios específicos.

## 📋 Templates disponibles

### Templates generales
- **`Concept.md`** - Template general para conceptos (mantiene compatibilidad)
- **`HowTo.md`** - Guías paso a paso y procedimientos generales
- **`Snippet.md`** - Fragmentos de código reutilizables
- **`Project.md`** - Documentación de proyectos generales
- **`Research.md`** - Papers, estudios y investigación

### Templates especializados para Conceptos

#### `Concept-Programming-Language.md`
**Para:** Lenguajes de programación (Python, JavaScript, Rust, etc.)
- Sintaxis fundamental y características distintivas
- Ecosistema de herramientas y frameworks
- Comparaciones con otros lenguajes
- Ejemplos prácticos de uso

#### `Concept-Software-Engineering.md`  
**Para:** Arquitectura, patrones de diseño, metodologías, principios
- Principios fundamentales y casos de uso
- Implementaciones y anti-patrones
- Trade-offs y consideraciones
- Casos de estudio reales

#### `Concept-Algorithm.md`
**Para:** Algoritmos y estructuras de datos
- Análisis de complejidad temporal y espacial
- Implementaciones paso a paso
- Comparaciones de rendimiento
- Testing y validación empírica

#### `Concept-Deep-Learning.md`
**Para:** Arquitecturas, técnicas y métodos de DL
- Fundamentos teóricos y matemáticos
- Implementaciones en PyTorch/TensorFlow
- Análisis experimental y hiperparámetros
- Referencias a papers y datasets

#### `Concept-Machine-Learning.md`
**Para:** Algoritmos y técnicas de ML tradicional
- Formulación matemática y supuestos
- Implementaciones con Scikit-learn
- Evaluación y validación cruzada
- Tuning de hiperparámetros

#### `Concept-Mathematics.md`
**Para:** Conceptos matemáticos puros y aplicados
- Definiciones formales y demostraciones
- Ejemplos ilustrativos y contra-ejemplos
- Implementaciones computacionales
- Conexiones interdisciplinarias

### Templates especializados para otros tipos

#### `HowTo-Development.md`
**Para:** Guías de desarrollo, setup, deployment
- Configuración de entornos de desarrollo
- Workflows de desarrollo completos
- Testing y validación técnica
- Troubleshooting y debugging

#### `Project-Data-Science.md`
**Para:** Proyectos de ML/DS con lifecycle específico
- Análisis exploratorio y feature engineering
- Experimentación y evaluación de modelos
- Deployment y monitoreo de modelos
- Business impact y ROI

## 🎯 Cuándo usar cada template

### Usa `Concept-Programming-Language.md` para:
- Python, JavaScript, Rust, Go, C++, etc.
- Características específicas de lenguajes
- Comparaciones entre lenguajes
- Ecosistemas y herramientas

### Usa `Concept-Software-Engineering.md` para:
- Patrones de diseño (Strategy, Observer, Factory)
- Principios (SOLID, DRY, KISS)
- Arquitecturas (MVC, Clean Architecture, Microservicios)
- Metodologías (Agile, TDD, DevOps)

### Usa `Concept-Algorithm.md` para:
- Algoritmos de ordenamiento (QuickSort, MergeSort)
- Algoritmos de búsqueda (BFS, DFS, A*)
- Estructuras de datos (Binary Tree, Hash Table)
- Algoritmos de optimización

### Usa `Concept-Deep-Learning.md` para:
- Arquitecturas (CNN, RNN, Transformer, GAN)
- Técnicas (Attention, Batch Normalization, Dropout)
- Funciones de pérdida y optimizadores
- Regularización y técnicas de entrenamiento

### Usa `Concept-Machine-Learning.md` para:
- Algoritmos supervisados (SVM, Random Forest, Logistic Regression)
- Algoritmos no supervisados (K-means, PCA, DBSCAN)
- Técnicas de evaluación y validación
- Métodos de preprocessing

### Usa `Concept-Mathematics.md` para:
- Teoremas y lemas matemáticos
- Conceptos de cálculo, álgebra, geometría
- Estadística y probabilidad
- Matemáticas aplicadas en CS/ML

### Usa `HowTo-Development.md` para:
- Configurar entornos de desarrollo (local, Docker, CI/CD)
- Implementar features específicas con testing
- Procesos de deployment y debugging
- Workflows de desarrollo completos

### Usa `Project-Data-Science.md` para:
- Proyectos de machine learning y data science
- Análisis exploratorio y feature engineering
- Experimentación con modelos y evaluación
- Deployment de modelos y monitoreo en producción

## 🚀 Cómo usar los templates

1. **Copia el template apropiado** según el dominio de tu concepto
2. **Renombra el archivo** con un nombre descriptivo
3. **Actualiza el frontmatter YAML** con información específica
4. **Completa las secciones** siguiendo la estructura guía
5. **Adapta el contenido** a las necesidades específicas de tu concepto

## 📝 Estructura común

Todos los templates especializados mantienen elementos comunes:

### Frontmatter YAML
```yaml
---
title: "Título descriptivo"
type: concept
tags: [area/domain, topic/specific, level/difficulty]
status: draft | active | final  
last_reviewed: YYYY-MM-DD
related_concepts: []
difficulty: beginner | intermediate | advanced
domain: specific-domain
---
```

### Secciones principales
- **🎯 ¿Qué es?** - Definición y contexto
- **🔍 ¿Por qué es importante?** - Relevancia y aplicaciones
- **💡 Ejemplos prácticos** - Implementaciones y uso
- **⚖️ Ventajas y limitaciones** - Trade-offs
- **🔗 Conceptos relacionados** - Enlaces a otros conceptos
- **📖 Referencias y recursos** - Fuentes y lectura adicional

## 🔄 Evolución de templates

Los templates evolucionarán basado en:
- **Feedback de uso** - Mejoras basadas en experiencia práctica
- **Nuevos dominios** - Templates adicionales según necesidades
- **Mejores prácticas** - Actualizaciones de estructura y contenido
- **Herramientas** - Integración con nuevas herramientas de PKM

## 🤝 Contribuciones

Para proponer mejoras a los templates:
1. Identifica qué template necesita mejoras
2. Proporciona ejemplos específicos de uso
3. Sugiere modificaciones concretas
4. Considera compatibilidad con herramientas existentes

---

*Última actualización: 2024 - Los templates están diseñados para ser tool-agnostic y funcionar con Obsidian, Logseq, VS Code, y otros editores de Markdown.*