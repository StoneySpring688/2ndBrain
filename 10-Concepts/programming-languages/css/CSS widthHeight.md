---
title: "CSS widthHeight"
type: concept
tags: [area/programming, topic/css, topic/css-widthheight, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, property]
---

Las propiedades `width` y `height` controlan el **tamaño del contenido de un elemento**. Pero el **tamaño total real** puede variar debido a múltiples factores.

Este es un tema clave para evitar errores visuales y errores de diseño, especialmente cuando hay desbordamientos, solapamientos o alineaciones erróneas.

---

## 📐 Unidades válidas

|Unidad|Qué representa|
|---|---|
|`px`|píxeles (valor fijo)|
|`%`|porcentaje relativo al contenedor padre|
|`em`|relativo al tamaño de fuente del elemento|
|`rem`|relativo al tamaño de fuente raíz (`html`)|
|`vw`|porcentaje del ancho de la ventana (viewport)|
|`vh`|porcentaje del alto de la ventana (viewport)|
|`auto`|el navegador calcula el tamaño basado en el contenido|

## 🧱 Ejemplo básico

```css
.caja {
  width: 300px;
  height: 200px;
}
```

Esto establece un tamaño fijo de 300x200 píxeles para la caja.

---

## 🧮 Modelo de caja en CSS

### Estructura:

```
|<-- margin -->|<-- border -->|<-- padding -->| content |<-- padding -->|<-- border -->|<-- margin -->|
```

### Por defecto:

```css
box-sizing: content-box;
```

- `width` y `height` solo definen el **contenido**

- `padding` y `border` se **suman** al tamaño total


---

## ✅ Modelo recomendado

```css
box-sizing: border-box;
```

- `width` y `height` incluyen **contenido + padding + border**

- Es **más predecible** y fácil de controlar


```css
* {
  box-sizing: border-box;
}
```

Usar esta línea global ayuda a mantener tamaños coherentes en todo el proyecto.

---

## 🔍 Factores que influyen en el cálculo

Aquí se detallan todas las propiedades que **afectan directa o indirectamente** al tamaño de un elemento:

---

### 1. `box-sizing`

|Valor|Efecto|
|---|---|
|`content-box`|`width`/`height` definen solo el contenido|
|`border-box`|`width`/`height` incluyen padding y border|

#### Ejemplo:

```css
width: 300px;
padding: 20px;
border: 5px solid black;
```

- Con `content-box`: el ancho **total** = 300 + 40 + 10 = **350px**

- Con `border-box`: el ancho **se mantiene** en 300px


---

### 2. `padding`

- Se suma al `content` si se usa `content-box`

- Puede **ocultar contenido** si no hay suficiente espacio


---

### 3. `border`

- Se suma igual que el `padding`

- Es visual, pero también **ocupa espacio real**

- Explicación de borders : [[3. css borders]]


---

### 4. `margin`

- **No afecta** el cálculo de `width`/`height`

- Pero **sí afecta el espacio total** que ocupa el elemento (por fuera)

- Explicación de margins : [[5. css margins]]


---

### 5. `overflow`

Define qué ocurre si el contenido **excede** el tamaño del contenedor:

```css
overflow: visible | hidden | scroll | auto;
```

- Puede permitir scroll, recortar el contenido o mostrarlo fuera del contenedor

- Afecta indirectamente si el contenido desborda

- Explicación de overflow : [[7. css overflow]]


---

### 6. `position`

- Con `absolute`, `fixed`, o `sticky`, el tamaño puede calcularse **respecto a un contenedor distinto**

- Puede requerir definir manualmente `width` o `height` si se saca del flujo normal


---

### 7. `display`

El tipo de caja también afecta si `width` y `height` tienen efecto:

|`display`|¿Acepta width/height?|
|---|---|
|`block`|✅ sí|
|`inline`|🚫 no (`width`/`height` ignorados)|
|`inline-block`|✅ sí|
|`flex`|✅ sí (pero con reglas propias)|
|`grid`|✅ sí|
|`table-*`|🟡 depende del contexto|

Explicación de display : [[9. css display]]

---

### 8. `min-width`, `max-width`, `min-height`, `max-height`

Limita el tamaño **mínimo o máximo** de un elemento:

```css
min-width: 200px;
max-width: 800px;
```

- Útil para **diseño responsive**

- Evita que el contenido se vuelva ilegible o que desborde


---

### 9. Contenido interno

- **Imágenes grandes**, texto largo sin espacios (`overflow-wrap`), tablas anchas, etc., pueden **forzar** el crecimiento del contenedor si `overflow` lo permite

- Usa:


```css
word-break: break-word;
overflow-wrap: break-word;
```

para forzar el corte de texto si es necesario.

---

### 10. Herencia y contenedores padres

Si usas:

```css
width: 100%;
height: 100%;
```

Estas medidas dependen **completamente del contenedor padre**. Si el padre no tiene altura definida, el valor `height: 100%` **no tendrá efecto**.

---

## 🧱 Ejemplo completo

```css
* {
  box-sizing: border-box;
}

.card {
  width: 400px;
  padding: 20px;
  border: 2px solid #333;
  margin: 0 auto;
  overflow: auto;
  max-height: 300px;
}
```

```html
<div class="card">
  <p>Contenido dinámico que puede ocupar más espacio...</p>
</div>
```

---

## 🧼 Buenas prácticas

- ✅ Usa `box-sizing: border-box;` globalmente

- ⚠️ Evita `height` fija si el contenido es dinámico

- ✅ Usa `max-width` o `max-height` para evitar desbordes

- ⚠️ Controla siempre `overflow` si limitas altura

- ✅ Verifica los `padding` y `border` en diseños ajustados

- 🚫 No uses `inline` si necesitas control de tamaño


---
