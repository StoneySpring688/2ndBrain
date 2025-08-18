---
title: "CSS float"
type: concept
tags: [area/programming, topic/css, topic/css-float, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, property]
---

La propiedad `float` se utiliza para **posicionar elementos a la izquierda o derecha** dentro de su contenedor, permitiendo que el contenido fluya alrededor de ellos.

---

## 🧭 Sintaxis básica

```css
.elemento {
  float: left;  /* o right */
}
```

Opciones disponibles:

- `left` → el elemento flota hacia la izquierda

- `right` → el elemento flota hacia la derecha

- `none` → sin flotado (valor por defecto)

- `inherit` → hereda el valor del elemento padre


---

## 🖼️ Ejemplo común: Imagen flotante

```html
<img src="foto.jpg" alt="Foto" style="float: left; margin-right: 15px;">
<p>
  Este texto rodea a la imagen gracias al `float`. La imagen se mantiene a la izquierda y el texto fluye a su lado.
</p>
```

---

## 📦 Float aplicado a bloques

```html
<div class="izquierda">Bloque izquierdo</div>
<div class="derecha">Bloque derecho</div>
```

```css
.izquierda {
  float: left;
  width: 45%;
  background: lightblue;
}

.derecha {
  float: right;
  width: 45%;
  background: lightgreen;
}
```

🔸 Resultado: los dos bloques se colocan uno al lado del otro.

---

## ⚠️ Problema común: el colapso del contenedor

Cuando todos los elementos hijos están flotando, el contenedor puede **colapsar** (su altura se vuelve cero).

### Solución: limpiar el flotado

#### Opción 1: usar `clear`

```html
<div style="clear: both;"></div>
```

#### Opción 2: usar un _clearfix_

```css
.contenedor::after {
  content: "";
  display: table;
  clear: both;
}
```

Esto garantiza que el contenedor se ajuste a la altura de los elementos flotantes.

---

## 🛠️ Cuándo usar `float` hoy en día

- Es útil para **envolver texto alrededor de imágenes**

- **NO se recomienda** para crear diseños complejos (usa mejor `flexbox` o `grid`)

- Aún se usa en correos HTML y entornos muy antiguos


---

## ✅ Alternativas modernas

Hoy es más común usar:

```css
display: flex;
```

o

```css
display: grid;
```

para diseñar columnas, alineaciones o estructuras completas.

---
