---
title: "CSS animations"
type: concept
tags: [area/web, topic/css/animations, level/beginner]
status: active
last_reviewed: 2025-08-18
related_concepts: []
difficulty: beginner
domain: web
---

**Las animaciones en CSS** permiten que los elementos cambien de estilo de forma gradual o repetida, haciendo las páginas más dinámicas e interactivas.

---

## 🛠️ 1. Transiciones (`transition`)

Las transiciones permiten animar **cambios de estilo al interactuar** (hover, focus, etc.).

**CSS básico:**

```css
.cuadro {
  transition: transform 0.5s ease, background-color 0.5s ease;
}

.cuadro:hover {
  transform: scale(1.5);
  background-color: orange;
}
```

**Desglose:**

- `transition-property`: qué propiedades animar (`transform`, `background-color`, `all`).
    
- `transition-duration`: duración de la animación.
    
- `transition-timing-function`: curva de aceleración (`linear`, `ease`, `ease-in`, `ease-out`, `cubic-bezier(...)`).
    
- `transition-delay`: retraso antes de empezar.
    

---

## 🛠️ 2. Animaciones con `@keyframes`

Para animaciones **automáticas o complejas** con varios pasos.

**CSS básico:**

```css
.cuadro-animado {
  animation: moverYcambiar 3s infinite alternate ease-in-out;
}

@keyframes moverYcambiar {
  0%   { transform: translateX(0); background-color: red; }
  50%  { transform: translateX(200px); background-color: blue; }
  100% { transform: translateX(0); background-color: green; }
}
```

**Desglose:**

- `animation-name`: nombre de los `@keyframes`.
    
- `animation-duration`: duración de un ciclo.
    
- `animation-timing-function`: curva de aceleración.
    
- `animation-delay`: retraso antes de iniciar.
    
- `animation-iteration-count`: cuántas veces se repite (`1`, `infinite`).
    
- `animation-direction`: normal, reverse, alternate, alternate-reverse.
    
- `animation-fill-mode`: qué sucede fuera de la animación (`none`, `forwards`, `backwards`, `both`).
    
- `animation-play-state`: `running` o `paused`.
    

---

## 🛠️ 3. Animaciones con JavaScript

Se pueden controlar **animaciones por eventos**:

```html
<div class="cuadro-nohover"></div>
```

```js
<script>
const cuadro = document.querySelector('.cuadro-nohover');
cuadro.addEventListener('click', () => {
  cuadro.classList.toggle('rotado');
});
</script>
```

```css
.cuadro-nohover {
  background-color: purple;
  transition: transform 2s ease;
}

.cuadro-nohover.rotado {
  transform: rotate(360deg);
}
```

También se pueden usar **eventos de animación**:

```js
element.addEventListener("animationend", () => console.log("Animación terminada"));
element.addEventListener("animationiteration", () => console.log("Se repitió"));
element.addEventListener("animationstart", () => console.log("Inicio"));
```

---

## 🔹 4. Curvas de aceleración (`timing-function`)

- `linear`: velocidad constante
    
- `ease`, `ease-in`, `ease-out`, `ease-in-out`: aceleración/desaceleración estándar
    
- `cubic-bezier(...)`: curvas personalizadas (rebotes, elásticas)
    

```css
animation-timing-function: cubic-bezier(0.68, -0.55, 0.27, 1.55); /* efecto rebote */
```

---

## 🛠️ 5. Buenas prácticas

- Animar principalmente `transform` y `opacity` → más fluido, menos recalcado de layout.
    
- Evitar animar `width`, `height`, `left`, `top` → afectan el rendimiento.
    
- Usar `will-change` para optimizar la GPU:
    

```css
.caja {
  will-change: transform, opacity;
}
```

- No abusar de animaciones automáticas en toda la página.
    

---

## 🎯 Ejemplo completo combinando todo

**HTML:**

```html
<div class="cuadro-hover"></div>
<div class="cuadro-animado"></div>
<div class="cuadro-nohover"></div>
<script>
const cuadro = document.querySelector('.cuadro-nohover');
cuadro.addEventListener('click', () => {
  cuadro.classList.toggle('rotado');
});
</script>
```

**CSS:**

```css
.cuadro-hover { 
background: crimson; width:100px;
height:100px;
transition: transform 0.5s ease, background-color 0.5s ease;
}

.cuadro-hover:hover { 
transform: scale(1.5);
background-color: orange;
}

.cuadro-animado { 
width:100px;
height:100px;
background: steelblue;
animation: moverYcambiar 3s infinite alternate ease-in-out;
}

@keyframes moverYcambiar { 
0%{transform:translateX(0);background:red;} 
50%{transform:translateX(200px);background:blue;} 
100%{transform:translateX(0);background:green;} 
}

.cuadro-nohover { 
width:100px;
height:100px;
background:purple;
transition: transform 2s ease;
}

.cuadro-nohover.rotado { 
transform: rotate(360deg);
}
```

---
