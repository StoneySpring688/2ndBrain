---
title: "CSS Bases - Fundamentos y Sintaxis"
type: concept
tags: [area/programming, topic/css, topic/web-styling, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, fundamentals]
---

### ¿Qué es CSS?

**CSS** (Cascading Style Sheets — Hojas de Estilo en Cascada) es el lenguaje que usamos para **dar estilo** a las páginas HTML. Permite modificar colores, tamaños, fuentes, márgenes, posiciones, etc. Mientras que HTML estructura, **CSS embellece**.

---

### ¿Cómo se aplica?

CSS puede aplicarse de **tres formas**:

#### 1. En línea (inline)

Usando el atributo `style` directamente en la etiqueta HTML:

```html
<p style="color: blue;">Texto en azul</p>
```

#### 2. Interno (en el `<head>`)

Se escribe dentro de la etiqueta `<style>` en el archivo HTML:

```html
<head>
  <style>
    p {
      color: red;
    }
  </style>
</head>
```

#### 3. Externo (recomendado)

Se escribe en un archivo `.css` aparte y se enlaza así:

```html
<head>
  <link rel="stylesheet" href="estilos.css">
</head>
```

---

### Sintaxis básica

La estructura de una regla CSS es:

```css
selector {
  propiedad: valor;
}
```

Ejemplo:

```css
h1 {
  color: green;
  font-size: 24px;
}
```

---

### Selectores comunes

- `*` → selecciona todos los elementos

- `p` → selecciona todos los `<p>`

- `.clase` → selecciona todos los elementos con `class="clase"`

- `#id` → selecciona el elemento con `id="id"`


```css
#titulo {
  text-align: center;
}

.intro {
  font-style: italic;
}
```

---

### Propiedades útiles

- `color` → color del texto

- `background-color` → color de fondo

- `font-size` → tamaño del texto

- `text-align` → alineación (`left`, `center`, `right`)

- `margin` → margen exterior

- `padding` → relleno interno

- `border` → borde del elemento


Ejemplo:

```css
div {
  background-color: lightgray;
  border: 1px solid black;
  padding: 10px;
  margin: 20px;
}
```

---

### Comentarios en CSS

Se escriben así:

```css
/* Esto es un comentario */
```

---

### Ejemplo completo:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Ejemplo CSS</title>
  <style>
    body {
      font-family: Arial;
    }

    h1 {
      color: darkblue;
    }

    p {
      font-size: 16px;
      line-height: 1.5;
    }

    .destacado {
      background-color: yellow;
    }
  </style>
</head>
<body>
  <h1>Hola CSS</h1>
  <p class="destacado">Este párrafo está resaltado con fondo amarillo.</p>
</body>
</html>
```

---