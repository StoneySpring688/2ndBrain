---
title: "Html span&div"
type: concept
tags: [area/programming, topic/html, topic/html-span&div, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: html
concept_type: [syntax, element, feature]
---

En HTML hay dos contenedores “vacíos” que se usan para agrupar y dar estilo cuando ninguna etiqueta semántica encaja:

| Elemento | Naturaleza | ¿Para qué sirve?                                                      | Render por defecto                                   |
| -------- | ---------- | --------------------------------------------------------------------- | ---------------------------------------------------- |
| `<div>`  | **Bloque** | Agrupar secciones, maquetar rejillas, wrappers de módulos completos.  | Ocupa todo el ancho; salto de línea antes y después. |
| `<span>` | **Inline** | Marcar pequeños fragmentos de texto para aplicarles estilos o lógica. | Fluye dentro del párrafo sin saltos.                 |

>[!IMPORTANT]
>**Regla de oro:**
> Si existe una etiqueta semántica mejor (`<section>`, `<header>`, `<article>`, `<p>`, `<strong>`, etc.), úsala. 
>  Recurre a `<div>` o `<span>` solo cuando nada encaje.

---

#### Ejemplo rápido y práctico

```html
<style>
  .card   { border: 1px solid #ccc; padding: 1rem; max-width: 280px; }
  .precio { color: crimson; font-weight: bold; }
</style>

<div class="card">
  <h2>Camiseta básica</h2>
  <p>Algodón 100 %. Disponible en <span lang="en">Navy Blue</span>.</p>
  <p><span class="precio">14,95 €</span></p>
</div>

```

- **`<div class="card">`** agrupa todo el producto como un bloque.

- **`<span class="precio">`** aísla el precio dentro de la frase para pintarlo en rojo.

- **`<span lang="en">`** marca una palabra en otro idioma (ayuda a lectores de pantalla).


---

#### Atributos típicos

- **`class`** — para CSS y JS.

- **`id`** — identificador único (anclas, scripts).

- **`lang`** — idioma específico de un fragmento (`<span lang="fr">bonjour</span>`).

- **`data-*`** — datos personalizados que puede leer JavaScript.

- **`role`** — dar semántica accesible cuando sea imprescindible (ej. `role="banner"`).


---

#### Buenas prácticas

1. **Evita el “div-itis” y el “span-itis”.** Cada uno que pongas sin motivo confunde el DOM y estorba al lector de pantalla.

2. **Añade semántica con ARIA solo si no hay alternativa nativa.** Ej.: un `<div role="button">` es peor que un `<button>`.

3. **Mantén los IDs únicos.** Un solo `id="header"` en todo el documento, **nunca** repetidos.

4. **Usa clases descriptivas, no de color ni posicionamiento.** `class="tarjeta-producto"` mejor que `class="rojo-centro"`. El estilo va al CSS, no al nombre.

5. **Agrupa lógicamente.** Un `<div>` por “carta”, “fila”, “columna” o “sección visual”, no por cada línea de texto.

6. **Combina con Flexbox o Grid.** `<div>` es el caballo de batalla para layouts, pero la magia la hacen las propiedades de caja.

7. **Medita antes de anidar.** Si un `<div>` contiene otro que solo sirve para espaciar, quizá baste con `padding` o `margin`.


Con `<span>` y `<div>` hay libertad total, pero también la responsabilidad de no convertir el HTML en un espagueti ilegible. Deben usarse con cabeza, añadiendo clases claras y dejando que la semántica real brille cuando toca.
