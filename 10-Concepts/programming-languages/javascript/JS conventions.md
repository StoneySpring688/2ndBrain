---
title: JS conventions
type: convenciones y buenas-practicas
tags:
  - area/programming
  - topic/javascript
  - topic/conventions
  - level/beginner
status: draft
last_reviewed: 2025-09-24
related_concepts: []
difficulty: beginner
domain: programming
language: javascript
concept_type:
  - syntax
  - conventions
  - good practices
---

# Convenciones en JavaScript

Colección de convenciones y buenas practicas en javaScript.

## 🎯 ¿Qué es?

- **Definición:** Serie de normas para facilitar el desarrollo del código en javaScript, así como hacer el código uniforme entre diferentes desarrolladores.
- **Categoría:** Convenciones
- **Lenguaje:** JavaScript
- **Versión introducida:** no existe versión específica
- **Contexto:** Siempre ha de tenerse presente para mejorar la calidad del código y facilitar su posterior revisión.

## 🔍 ¿Por qué es importante?

- **Problema que resuelve:** Desarrollo uniforme entre multiples desarrolladores
- **Ventajas:** Uniformidad y legibilidad
- **Casos de uso comunes:** Nombres de ficheros, nombres de variables, ...
- **Alternativas:** no consta
- **Mejores prácticas:** Tenerlo presente a la hora hacer algo nuevo o revisar algo antigüo

## 📝 Convenciones

### Nombrado de ficheros

Deben nombrarse usando **kebab-case**. En este las palabras son **separadas con guiones y en minúscula**.
```
context-manager.js
```

## 💡 Ejemplos prácticos

### Ejemplo 1: Caso básico
```language-name
// Explicación del contexto del problema
// Solución usando el concepto

// Entrada esperada
input = ejemplo_entrada;

// Aplicación del concepto
resultado = aplicar_concepto(input);

// Salida obtenida
console.log(resultado); // Output esperado
```

### Ejemplo 2: Caso intermedio
```language-name
// Problema más complejo que requiere:
// - Validación de entrada
// - Manejo de errores
// - Optimización

try {
    // Implementación robusta
    resultado = concepto_con_validacion(input);
} catch (error) {
    // Manejo de errores específicos del concepto
    manejar_error(error);
}
```

### Ejemplo 3: Caso avanzado/real
```language-name
// Caso de uso real en aplicación
// Mostrando:
// - Integración con otros conceptos
// - Consideraciones de rendimiento
// - Mejores prácticas de producción

class EjemploReal {
    constructor() {
        this.configuracion = configuracion_optimizada;
    }
    
    metodo_que_usa_concepto(datos) {
        // Implementación completa y optimizada
        return resultado_procesado;
    }
}
```

## ⚖️ Ventajas y desventajas

### ✅ Ventajas
- **Legibilidad:** Hace el código más claro y expresivo
- **Mantenibilidad:** Facilita el mantenimiento del código
- **Performance:** No tiene un impacto directo en el rendimiento
- **Reutilización:** Facilita la reutilización de código
- **Debugging:** Facilita la depuración

### ❌ Desventajas o limitaciones
- **Curva de aprendizaje:** Puede resultar complejo acostumbrarse usarlas.

## 🔄 Puntaje

| Aspecto      | Puntuación |
| ------------ | ---------- |
| Legibilidad  | ⭐⭐⭐⭐⭐      |
| Performance  | ⭐⭐⭐⭐⭐      |
| Simplicidad  | ⭐⭐⭐        |
| Flexibilidad | ⭐⭐         |

## 🔗 Conceptos relacionados

**No Constan.**

## 📖 Referencias y recursos

### Documentación oficial
* [Guía de estilo](https://google.github.io/styleguide/jsguide.html)

---

**Notas de revisión:**
- [ ] Verificar que ejemplos de código compilen y funcionen
- [ ] Actualizar enlaces a documentación cuando cambie
- [ ] Revisar compatibilidad con versiones actuales del lenguaje
- [ ] Validar que las alternativas sean actuales y relevantes
- [ ] Comprobar que los casos de uso reflejen prácticas modernas