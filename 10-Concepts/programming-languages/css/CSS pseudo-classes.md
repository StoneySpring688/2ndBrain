---
title: "CSS pseudo-classes"
type: concept
tags: [area/programming, topic/css, topic/css-pseudo-classes, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, property]
---

Las **pseudo-clases** permiten aplicar estilos a elementos HTML **en función de su estado**, posición o interacción con el usuario, **sin necesidad de agregar clases adicionales** en el HTML.

Se escriben con el símbolo `:` seguido del nombre de la pseudo-clase:

```css
selector:pseudoclase {
  /* estilos */
}
```

---

## 🎯 Tipos comunes de pseudo-clases

### ✅ 1. **Interacción del usuario**

Estas cambian el estilo según la interacción con el mouse o el foco.

|Pseudo-clase|Descripción|
|---|---|
|`:hover`|Cuando el usuario pasa el cursor sobre el elemento|
|`:active`|Mientras el usuario está haciendo clic|
|`:focus`|Cuando el elemento (input, botón…) recibe foco|
|`:visited`|Enlaces que ya fueron visitados|
|`:link`|Enlaces que no han sido visitados|
|`:focus-visible`|Cuando el foco es visible (mejor para accesibilidad)|

```css
a:hover {
  color: red;
}

button:focus {
  outline: 2px solid blue;
}
```

---

### 🧭 2. **Posición dentro del documento**

Estas seleccionan elementos según su orden en el HTML.

|Pseudo-clase|Descripción|
|---|---|
|`:first-child`|El primer hijo dentro de su padre|
|`:last-child`|El último hijo|
|`:nth-child(n)`|El enésimo hijo (empieza en 1)|
|`:nth-last-child(n)`|Como `nth-child`, pero contado desde el final|
|`:only-child`|Si es el único hijo|

```css
li:first-child {
  font-weight: bold;
}

tr:nth-child(odd) {
  background-color: #f9f9f9;
}
```

🔹 Puedes usar fórmulas como `2n`, `2n+1`, `3n`, etc.

---

### 🧩 3. **Tipo de elemento**

|Pseudo-clase|Descripción|
|---|---|
|`:first-of-type`|Primer hijo de su tipo|
|`:last-of-type`|Último hijo de su tipo|
|`:nth-of-type(n)`|El enésimo hijo de ese tipo|
|`:only-of-type`|Si es el único hijo de su tipo|

```css
p:first-of-type {
  text-decoration: underline;
}
```

---

### 📥 4. **Estado de formularios**

|Pseudo-clase|Descripción|
|---|---|
|`:checked`|Elementos seleccionados (`checkbox`, `radio`)|
|`:disabled`|Elementos deshabilitados|
|`:enabled`|Elementos habilitados|
|`:required`|Campos requeridos|
|`:optional`|Campos opcionales|
|`:valid`|Campo con valor válido|
|`:invalid`|Campo con valor no válido|
|`:in-range`|Valor dentro del rango permitido|
|`:out-of-range`|Fuera del rango|
|`:read-only`, `:read-write`|Campos con lectura o edición|

```css
input:checked + label {
  color: green;
}

input:invalid {
  border-color: red;
}
```

---

### 🧠 5. **Otras pseudo-clases útiles**

|Pseudo-clase|Descripción|
|---|---|
|`:not(selector)`|Selecciona todo lo que **no** coincide|
|`:empty`|Elementos sin hijos (ni texto)|
|`:root`|Selecciona el elemento raíz (`<html>`)|
|`:is(selector1, selector2, ...)`|Agrupa múltiples selectores|
|`:where(...)`|Igual que `:is()`, pero sin aumentar especificidad|
|`:has(selector)`|Selecciona un elemento si contiene otro (solo en navegadores modernos)|

```css
div:not(.activo) {
  opacity: 0.5;
}

:root {
  --principal: #3498db;
}

.card:has(img) {
  border: 1px solid #ccc;
}
```

---

## 🧪 Ejemplo práctico

```html
<ul>
  <li>Elemento 1</li>
  <li>Elemento 2</li>
  <li class="destacado">Elemento 3</li>
  <li>Elemento 4</li>
</ul>
```

```css
li:first-child {
  color: green;
}

li:last-child {
  color: red;
}

li.destacado:hover {
  background-color: yellow;
}
```

---

## ✅ Buenas prácticas

- Usa `:not()` para excluir casos sin tener que añadir clases.

- `:is()` y `:where()` simplifican selectores complejos.

- Combina pseudo-clases con clases o elementos para mayor control.

- Usa `:focus-visible` en vez de `:focus` para mejorar accesibilidad.


---
