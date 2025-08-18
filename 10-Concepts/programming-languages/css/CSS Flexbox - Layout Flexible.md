---
title: "CSS Flexbox - Layout Flexible"
type: concept
tags: [area/programming, topic/css, topic/flexbox, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: css
concept_type: [syntax, feature, property]
---

# 🚀 Diseñando con Flexbox en CSS

**Flexbox** (Flexible Box Layout) es un sistema de diseño en CSS que facilita la organización de elementos en fila o columna, permitiendo alinearlos y distribuir el espacio de forma eficiente.

---

## 🛠️ Activando Flexbox

Para usar Flexbox, basta con aplicarlo al elemento padre que contiene los elementos que queremos organizar.

**CSS:**
```css
.contenedor {
  display: flex;
}

🧠 Esto convierte a todos los hijos directos del contenedor en **elementos flexibles**, listos para alinearse según las reglas de Flexbox.

---

## 📐 Propiedades Principales del Contenedor

### 1. Dirección de los elementos (`flex-direction`)

Define si los elementos se colocan en **fila** o **columna**.

```css
.contenedor {
  flex-direction: row;   /* fila (por defecto) */
  /* flex-direction: column; columna */
}
```

**Gráfico** — contenedor simple con `display:flex`:

<p>Contenedor con <code style="color:cyan;">display:flex</code>:</p> <div style="display:flex; gap:20px; align-items:center;"> <div style="width:260px; padding:12px; background:#f0f0f0; border-radius:8px;"> <div style="display:block; background:#ddd; padding:10px; border-radius:6px; color:#333;">No es flex (bloques apilados)</div> <div style="display:block; background:#ddd; padding:10px; border-radius:6px; margin-top:8px; color:#333;">No es flex</div> <div style="display:block; background:#ddd; padding:10px; border-radius:6px; margin-top:8px; color:#333;">No es flex</div> </div> <div style="width:260px; padding:12px; background:#eef6ff; border-radius:8px;"> <div style="display:flex; gap:8px; background:transparent;"> <div style="width:48px; height:48px; background:#4e79a7; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">1</div> <div style="width:48px; height:48px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">2</div> <div style="width:48px; height:48px; background:#59a14f; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">3</div> </div> <div style="margin-top:8px; font-size:12px; color:#333;">Padre con <code>display:flex</code></div> </div> </div>

---

### 2. Alineación principal (`justify-content`)

Alinea los elementos a lo largo del **eje principal**.

```css
justify-content: flex-start;   /* Inicio */
justify-content: center;       /* Centro */
justify-content: flex-end;     /* Final */
justify-content: space-between;/* Espacio entre */
justify-content: space-around; /* Espacios iguales alrededor */
```

**Gráfico** — comparación `row` vs `column`:

 <div style="display:flex; gap:30px; align-items:flex-start;"> <!-- Row --> <div style="padding:10px; border-radius:8px; background:#f7fbf9; width:240px;"> <div style="font-size:13px; margin-bottom:8px; color:black">flex-direction: row</div> <div style="display:flex; gap:8px; justify-content:flex-start;"> <div style="width:44px; height:44px; background:#76b7b2; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">A</div> <div style="width:44px; height:60px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">B</div> <div style="width:44px; height:44px; background:#f28e2c; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">C</div> </div> </div> <!-- Column --> <div style="padding:10px; border-radius:8px; background:#fff7f0; width:140px;"> <div style="font-size:13px; margin-bottom:8px; color:black">flex-direction: column</div> <div style="display:flex; flex-direction:column; gap:8px; align-items:flex-start;"> <div style="width:80px; height:40px; background:#76b7b2; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">A</div> <div style="width:80px; height:56px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">B</div> <div style="width:80px; height:40px; background:#f28e2c; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">C</div> </div> </div> </div>

---

### 3. Alineación cruzada (`align-items`)

Alinea los elementos en el **eje cruzado**.

```css
align-items: flex-start; /* Arriba */
align-items: center;     /* Centro */
align-items: flex-end;   /* Abajo */
align-items: stretch;    /* Se estiran */
```

**Gráfico** — mostrar `align-items` con cajas de alturas distintas:

<p>Variantes de <code style="color:cyan;">align-items</code> (eje vertical):</p> <div style="display:flex; gap:20px; align-items:flex-start;"> <div style="width:220px; padding:10px; background:#fff; border-radius:8px;"> <div style="font-size:13px; margin-bottom:8px; color:black">align-items: flex-start</div> <div style="display:flex; align-items:flex-start; gap:8px; height:120px; background:#f6f9f8; padding:8px; border-radius:6px;"> <div style="width:44px; height:44px; background:#4e79a7; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">A</div> <div style="width:44px; height:64px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">B</div> <div style="width:44px; height:88px; background:#59a14f; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">C</div> </div> </div> <div style="width:220px; padding:10px; background:#fff; border-radius:8px;"> <div style="font-size:13px; margin-bottom:8px; color:black">align-items: center</div> <div style="display:flex; align-items:center; gap:8px; height:120px; background:#f6f9f8; padding:8px; border-radius:6px;"> <div style="width:44px; height:44px; background:#4e79a7; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">A</div> <div style="width:44px; height:64px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">B</div> <div style="width:44px; height:88px; background:#59a14f; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">C</div> </div> </div> <div style="width:220px; padding:10px; background:#fff; border-radius:8px;"> <div style="font-size:13px; margin-bottom:8px; color:black">align-items: stretch</div> <div style="display:flex; align-items:stretch; gap:8px; height:120px; background:#f6f9f8; padding:8px; border-radius:6px;"> <div style="width:44px; background:#4e79a7; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">A</div> <div style="width:44px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">B</div> <div style="width:44px; background:#59a14f; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">C</div> </div> </div> </div>

---

### 4. Espacio entre elementos (`gap`)

Añade separación sin usar `margin`.

```css
gap: 10px; /* px, rem, % */
```

**Gráfico** — demostración de `gap`:

<p>Contenedor con <code style="color:cyan;">gap: 20px</code>:</p> <div style="display:flex; gap:24px; align-items:center; padding:8px; background:#fbfbfb; border-radius:8px; width:100%; max-width:540px;"> <div style="display:flex; gap:20px;"> <div style="width:48px; height:48px; background:#4e79a7; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">1</div> <div style="width:48px; height:48px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">2</div> <div style="width:48px; height:48px; background:#59a14f; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">3</div> </div> <div style="font-size:13px; color:#333;">gap: 20px</div> </div>

---

## 🎯 Ejemplo Básico de Uso

**HTML:**

```html
<div class="contenedor">
  <div class="caja">1</div>
  <div class="caja">2</div>
  <div class="caja">3</div>
</div>
```

**CSS:**

```css
.contenedor {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 10px;
  height: 200px;
  background: #eee;
}

.caja {
  background: tomato;
  color: white;
  padding: 20px;
  font-size: 20px;
}
```

**Gráfico** — el ejemplo anterior renderizado con estilos inline (cópialo tal cual si lo prefieres directo en HTML):

<p>Ejemplo básico (contenedor centrado):</p> <div style="display:flex; justify-content:center; align-items:center; height:200px; background:#eee; padding:12px; border-radius:8px;"> <div style="display:flex; gap:10px; align-items:center;"> <div style="background:tomato; color:white; padding:16px 18px; font-size:18px; border-radius:6px;">1</div> <div style="background:tomato; color:white; padding:16px 18px; font-size:18px; border-radius:6px;">2</div> <div style="background:tomato; color:white; padding:16px 18px; font-size:18px; border-radius:6px;">3</div> </div> </div>

---

## 📊 Concepto Clave: Ejes de Flexbox

- **Eje principal (main axis):** definido por `flex-direction`.

- **Eje cruzado (cross axis):** perpendicular al principal.


💡 Si `flex-direction: row` → eje principal es horizontal, eje cruzado vertical.  
💡 Si `flex-direction: column` → eje principal es vertical, eje cruzado horizontal.

**Gráfico** — visual rápido del eje principal / cruzado:

<p>Eje principal (→) y eje cruzado (↓):</p> <div style="display:flex; gap:30px; align-items:flex-start;"> <div style="padding:10px; border-radius:8px; background:#f7fbff;"> <div style="font-size:13px; margin-bottom:8px; color:black">Row — eje principal: horizontal</div> <div style="display:flex; gap:8px; align-items:center;"> <div style="width:44px; height:44px; background:#4e79a7; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">→</div> <div style="width:44px; height:44px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">→</div> <div style="width:44px; height:44px; background:#59a14f; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">→</div> </div> </div> <div style="padding:10px; border-radius:8px; background:#fff7f7;"> <div style="font-size:13px; margin-bottom:8px; color:black">Column — eje principal: vertical</div> <div style="display:flex; flex-direction:column; gap:8px; align-items:flex-start;"> <div style="width:44px; height:44px; background:#4e79a7; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">↓</div> <div style="width:44px; height:44px; background:#e15759; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">↓</div> <div style="width:44px; height:44px; background:#59a14f; display:flex; align-items:center; justify-content:center; color:white; border-radius:6px;">↓</div> </div> </div> </div>

---

## 🧪 Tip de Práctica

Para dominar Flexbox, prueba cambiando:

- `flex-direction` entre `row` y `column`.

- `justify-content` para ver la distribución horizontal.

- `align-items` para ver la alineación vertical.
