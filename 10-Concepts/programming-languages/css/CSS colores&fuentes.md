---
title: "CSS colores&fuentes"
type: concept
tags: [area/programming, topic/css, topic/css-colores&fuentes, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, property]
---

## 🎨 COLORES

CSS ofrece varias formas de definir colores:

### 1. **Por nombre**

Hay más de 140 nombres reconocidos:

```css
color: red;
background-color: lightblue;
```

### 2. **Hexadecimal**

Se usa `#` seguido de 3 o 6 caracteres:

```css
color: #ff0000;    /* Rojo */
color: #0f0;       /* Verde (forma corta de #00ff00) */
```

### 3. **RGB y RGBA**

Usa la intensidad de Rojo, Verde y Azul (0–255). `A` es la opacidad (0 = transparente, 1 = opaco):

```css
color: rgb(0, 128, 255);        /* Azul brillante */
background-color: rgba(255, 0, 0, 0.5);  /* Rojo con transparencia */
```

### 4. **HSL y HSLA**

Tonos (Hue), Saturación y Luminosidad:

```css
color: hsl(240, 100%, 50%);       /* Azul puro */
background-color: hsla(120, 60%, 70%, 0.3);  /* Verde claro translúcido */
```

---

## 🅰️ FUENTES (TIPOGRAFÍA)

### Propiedades principales:

|Propiedad|Ejemplo|Descripción|
|---|---|---|
|`font-family`|`Arial, sans-serif`|Tipo de letra|
|`font-size`|`16px`, `1.5em`, `120%`|Tamaño|
|`font-weight`|`normal`, `bold`, `400`, `700`|Grosor|
|`font-style`|`normal`, `italic`, `oblique`|Estilo|
|`text-align`|`left`, `center`, `right`, `justify`|Alineación|
|`text-decoration`|`none`, `underline`, `line-through`|Decoración|
|`line-height`|`1.5`, `20px`|Altura de línea|

---

### Ejemplo completo:

```css
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 18px;
  color: #333;
  background-color: #f9f9f9;
  line-height: 1.6;
  text-align: justify;
}
```

### Enlace a fuentes externas (Google Fonts)

```html
<!-- En el <head> del HTML -->
<link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
```

```css
/*En el CSS*/
body {
  font-family: 'Roboto', sans-serif;
}
```

### Con Fonts descargadas

```css
/*En el CSS*/
@font-face {
	font-family: Medievo; /*nombre con  el que se va a usar el font*/
	src: url(fonts/ManufacturingConsent-Regular.ttf); /*ruta al .ttf del font*/
}

body {
	font-family: Medievo;
}
```

---
