---
title: "CSS Display - Tipos de Visualización"
type: concept
tags: [area/programming, topic/css, topic/display, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, property]
---

# 🎭 Display en CSS

La propiedad **`display`** define cómo se comporta un elemento HTML visualmente en el flujo del documento: si es un bloque, una línea, un contenedor flexible, etc.

---

## 🧱 Valores comunes

### 1. `block`

El elemento ocupa **todo el ancho disponible** y comienza en una **nueva línea**.

```css
div {
  display: block;
}
```

Elementos como `<div>`, `<p>`, `<h1>` ya son `block` por defecto.

**Visualización:**

<div style="background-color:#fff; padding:20px; border-radius:12px; max-width:500px; margin:auto;">
  <div style="display:block; background-color:#76b7b2; color:White; padding:10px; border-radius:8px; margin-bottom:10px;">
    Bloque (block)
  </div>
  <div style="display:block; background-color:#e15759; color:White; padding:10px; border-radius:8px; margin-bottom:10px;">
    Siguiente
  </div>
</div>


---

### 2. `inline`

El elemento **no comienza en una nueva línea** y **solo ocupa el espacio que necesita**.

```css
span {
  display: inline;
}
```

Elementos como `<span>`, `<a>`, `<strong>` son `inline` por defecto.

**Visualización:**

<div style="background-color:#ffffff; padding:10px; border-radius:8px; border:1px solid #ddd; margin-top:10px;"> 
	<span style="background-color:#76b7b2; padding:5px; margin-right:5px; color:white;">Inline 1</span>
	<span style="background-color:#e15759; padding:5px; margin-right:5px; color:white;">Inline 2</span> 
	<span style="background-color:#f28e2c; padding:5px; color:white;">Inline 3</span>
</div>

---

### 3. `inline-block`

Como `inline`, **pero** permite usar propiedades de bloque (como `width`, `height`, `padding`, `margin`).

```css
button {
  display: inline-block;
}
```

**Visualización:**
<div style="background-color:#ffffff; padding:10px; border-radius:8px; border:1px solid #ddd; margin-top:10px;">
	<div style="background-color:#76b7b2; color:white; padding:20px; border-radius:6px; display:inline-block; width:240px; text-align:center;">Inline-block</div> 
	<div style="background-color:#e15759; color:white; padding:10px; border-radius:6px; display:inline-block; width:120px; text-align:center; margin-left:5px;">Otra caja</div>
</div>

---

### 4. `none`

El elemento **no se muestra** (como si no existiera en la página).

```css
.elemento {
  display: none;
}
```

🔹 Ideal para ocultar cosas dinámicamente con JavaScript.

---

## 🧲 Contenedores modernos

### 5. `flex`

Activa **[[17. flexbox]]**, ideal para diseños unidimensionales (una fila o columna).

```css
.container {
  display: flex;
}
```

➡️ Usa junto con propiedades como `justify-content` o `align-items`.

**Visualización:**

<div style="width:260px; padding:12px; background:#eef6ff; border-radius:8px;">
	<div style="display:flex; gap:8px; background:transparent;"> 
		<div style="width:48px; height:48px; background:#4e79a7; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">1</div> 
		<div style="width:48px; height:48px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">2</div>
		<div style="width:48px; height:48px; background:#59a14f; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">3</div> 
	</div> 
	<div style="margin-top:8px; font-size:12px; color:#333;">Caja con <code style="margin-top:8px; font-size:12px; ">display:flex</code></div>
</div>

---

### 6. `grid`

Activa **CSS Grid**, un sistema para diseños **bidimensionales** (filas y columnas).z

```css
.container {
  display: grid;
}
```

➡️ Usa con `grid-template-columns`, `gap`, etc.

**Visualización:**

<div style="width:260px; padding:12px; background:#eef6ff; border-radius:8px;"> <div style="display:grid; grid-template-columns: repeat(3, 1fr); gap:8px; background:transparent;"> <div style="width:48px; height:48px; background:#76b7b2; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">1</div> <div style="width:48px; height:48px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">2</div> <div style="width:48px; height:48px; background:#f28e2c; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">3</div> </div> <div style="margin-top:8px; font-size:12px; color:#333;">Caja con <code style="margin-top:8px; font-size:12px;">display:grid</code></div> </div>

---

### 7. `inline-flex` y `inline-grid`

Lo mismo que `flex` y `grid`, pero se comportan como elementos en línea.

```css
.inline-caja {
  display: inline-flex;
}
```

**Visualización:**

<div style="background-color:#ffffff; padding:10px; border-radius:8px; border:1px solid #ddd; margin-top:10px;">
	<div style="display:inline-flex; gap:10px; margin-top:10px;">
		 <div style="background-color:#76b7b2; color:white; padding:10px; border-radius:6px;">Caja 1</div> 
		 <div style="background-color:#e15759; color:white; padding:10px; border-radius:6px;">Caja 2</div>
	  </div>
</div>

---

## 📋 Otros valores útiles

|Valor|Uso|
|---|---|
|`table`, `table-row`, `table-cell`|Simula una tabla HTML usando CSS|
|`list-item`|Comportamiento de lista (como `<li>`)|
|`contents`|Hace que el contenedor desaparezca visualmente, pero sus hijos se mantienen visibles|
|`inherit`, `initial`, `unset`|Valores especiales para herencia y reseteo|

---

## 🧪 Ejemplo práctico

```html
<div class="bloque">Bloque</div>
<span class="en-linea">En línea</span>
```

```css
.bloque {
  display: block;
  background: lightblue;
  margin-bottom: 10px;
}

.en-linea {
  display: inline;
  background: lightgreen;
}
```

**Visualización:**
<div style="background-color:#ffffff; padding:10px; border-radius:8px; border:1px solid #ddd; margin-top:10px;">
	<div style="background-color:#76b7b2; color:white; padding:10px; margin-bottom:10px; border-radius:6px;">Bloque</div> 
	<span style="display:inline; background-color:#e15759; color:white; padding:5px 8px; border-radius:4px;">En línea</span>
</div>

---
