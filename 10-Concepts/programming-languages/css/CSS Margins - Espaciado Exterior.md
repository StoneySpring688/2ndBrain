---
title: "CSS Margins - Espaciado Exterior"
type: concept
tags: [area/programming, topic/css, topic/margins, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, property]
---

# ⚪ Márgenes en CSS

Los **márgenes** son espacios en blanco **fuera** del borde de un elemento. Se usan para **separar elementos entre sí**.

---

## 📏 Propiedad `margin`

La forma más básica de usarlo:

```css
div {
  margin: 20px;
}
```

Esto aplica 20 píxeles de margen en **todos los lados**: arriba, derecha, abajo y izquierda.

---

## 🔄 Márgenes individuales

Puedes definir el margen de cada lado por separado:

```css
margin-top: 10px;
margin-right: 15px;
margin-bottom: 20px;
margin-left: 5px;
```

---

## ⏱️ Atajo con `margin` (shorthand)

Cuando usas `margin` con múltiples valores, se aplican en este orden:

```
margin: arriba derecha abajo izquierda;
```

Ejemplos:

```css
margin: 10px;               /* todos los lados */
margin: 10px 20px;          /* arriba/abajo - derecha/izquierda */
margin: 10px 15px 20px;     /* arriba - derecha/izquierda - abajo */
margin: 10px 15px 20px 25px;/* arriba - derecha - abajo - izquierda */
```

---

## 📐 Valores posibles

- Unidades absolutas: `px`, `cm`, etc.

- Unidades relativas: `%`, `em`, `rem`, etc.

- Valor especial: `auto`


```css
div {
  margin: auto;
}
```

🔹 `auto` se usa frecuentemente para **centrar** elementos horizontalmente (como `divs` con ancho fijo).

---

## 🎯 Centrado horizontal de un `div`

```css
div {
  width: 300px;
  margin: 0 auto;
}
```

Esto centra el `div` en la pantalla.

---

## 🧱 Ejemplo completo

```css
.caja {
  background-color: #f0f0f0;
  padding: 20px;
  margin: 40px auto;
  width: 400px;
  border: 1px solid #ccc;
}
```

```html
<div class="caja">
  Esta caja tiene márgenes automáticos y está centrada horizontalmente.
</div>
```

---
