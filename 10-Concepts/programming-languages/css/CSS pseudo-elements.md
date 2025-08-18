---
title: "CSS pseudo-elements"
type: concept
tags: [area/programming, topic/css, topic/css-pseudo-elements, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, property]
---

Los **pseudo-elementos** permiten aplicar estilos a **partes específicas de un elemento HTML**, incluso si esas partes **no existen como nodos reales** en el DOM (Document Object Model).

Se escriben con **dos puntos dobles `::`** (aunque algunos navegadores todavía aceptan `:` simple por compatibilidad).

---

## 🧩 Sintaxis general

```css
selector::pseudo-element {
  propiedad: valor;
}
```

---

## 🎯 Pseudo-elementos principales

### 1. `::before`

Inserta contenido **antes** del contenido real del elemento.

```css
p::before {
  content: "→ ";
  color: gray;
}
```

🔹 Requiere obligatoriamente `content`, incluso si es una cadena vacía (`""`).

---

### 2. `::after`

Inserta contenido **después** del contenido real.

```css
p::after {
  content: " ✔";
  color: green;
}
```

🟠 Muy útil para agregar decoraciones, íconos, símbolos, o efectos visuales.

---

### 3. `::first-line`

Aplica estilos solo a la **primera línea** visible del texto (según el ancho del contenedor).

```css
p::first-line {
  font-weight: bold;
  color: navy;
}
```

🧠 Solo funciona con propiedades relacionadas con texto: `font`, `color`, `text-decoration`, etc.

---

### 4. `::first-letter`

Aplica estilos solo a la **primera letra** de un bloque de texto.

```css
p::first-letter {
  font-size: 2em;
  color: darkred;
}
```

🔸 Ideal para efectos tipográficos como en los libros antiguos (capitulares).

---

### 5. `::selection`

Estiliza la parte del texto que el usuario **selecciona** con el cursor.

```css
p::selection {
  background: yellow;
  color: black;
}
```

🎨 Soporta `color`, `background`, `text-shadow` y `outline`.

---

## 🧪 Ejemplo combinado

```html
<p class="destacado">Este párrafo tiene pseudo-elementos antes, después y más.</p>
```

```css
.destacado::before {
  content: "★ ";
  color: gold;
}

.destacado::after {
  content: " [fin]";
  color: gray;
}

.destacado::first-letter {
  font-size: 2rem;
  color: crimson;
}

.destacado::selection {
  background-color: lime;
  color: black;
}
```

---

## 🧠 Notas importantes

- **`content` es obligatorio** en `::before` y `::after`, incluso si no se muestra nada.

- Se puede usar `content: attr(data-atributo)` para insertar atributos personalizados.

- Los pseudo-elementos no afectan al DOM real, por lo que no se pueden seleccionar con JavaScript directamente.

- Solo se puede usar **uno de cada tipo por selector** (no puedes tener dos `::before` en el mismo elemento).


---

## ✅ Buenas prácticas

- Usa `::before` y `::after` para decoraciones **ligeras y no estructurales**.

- Úsalos con clases o selectores específicos para evitar efectos no deseados.

- Ideal para separar lógica de HTML y presentación visual en CSS.


---
