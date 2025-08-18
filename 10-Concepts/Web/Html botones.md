---
title: "Html botones"
type: concept
tags: [area/programming, topic/html, topic/html-botones, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: html
concept_type: [syntax, element, feature]
---


|Elemento / atributo|¿Para qué sirve?|Render por defecto|
|---|---|---|
|`<button>`|Botón “de verdad”, acepta texto o HTML interno.|Rectángulo clickable; estilo UA; `inline-block`.|
|`<input type="button">`|Botón genérico sin semántica de envío.|Igual a `<button>`, texto por `value`.|
|`<input type="submit">`|Envía el formulario asociado.|Igual al anterior, pero dispara `submit`.|
|`<input type="reset">`|Restaura valores iniciales del form.|Como botón; restablece inputs.|
|`type` (`button`, `submit`, `reset`)|Controla la acción predeterminada.|En `<button>`: **`submit` si no se indica**.|
|`disabled`|Desactiva la interacción.|Opacidad y cursor gris/“no-drop”.|
|`autofocus`|Foco automático al cargar.|Resaltado por UA.|
|`form`, `formaction`, `formenctype`...|Permite apuntar a un formulario externo o sobreescribir su acción.|Depende del navegador.|
|`aria-pressed`|Estado “on/off” para botones tipo _toggle_.|No cambia lo visual: solo accesibilidad.|

---

#### Ejemplo

```html
<form id="alta">
  <!-- Botón de acción primaria -->
  <button type="submit" class="btn btn--primario">
    Alta inmediata
  </button>

  <!-- Botón que solo lanza JS -->
  <button type="button" class="btn btn--secundario" id="preview">
    Vista previa
  </button>

  <!-- Botón toggle accesible -->
  <button type="button"
          class="btn btn--toggle"
          aria-pressed="false"
          aria-controls="detalles"
          id="ver-detalles">
    Mostrar detalles
  </button>

  <!-- Botón deshabilitado -->
  <input type="submit"
         value="Procesando…"
         class="btn"
         disabled>
</form>
```

- **`type="submit"`** es el valor por defecto, ergo **decláralo explícitamente** para evitar sorpresas.

- **`aria-pressed` + `aria-controls`** convierten un botón normal en un switch/accordion accesible.

- **`disabled`** bloquea eventos _y_ evita el foco: úsalo mientras esperas al servidor.


---

#### Atributos esenciales

|Atributo|En|Valor típico|Comentario|
|---|---|---|---|
|`type`|`<button>`, `<input>`|`button`, `submit`, `reset`|Define la semántica.|
|`name` / `value`|Ambos|Texto corto|Se envían con el form (salvo `type="button"`).|
|`disabled`|Ambos|—|Desactiva interacción y estilos.|
|`form`|`<button>`, `<input>`|`id` del formulario|Dispara/afecta a otro form sin anidarlo.|
|`formaction`|Igual|URL|Sobrescribe `action` del form en ese botón.|
|`autofocus`|Ambos|—|Único elemento con foco automático permitido.|
|`aria-*`|Ambos|Depende|Etiquetas WAI-ARIA para estados/roles.|

---

#### Buenas prácticas

1. **Usa `<button>` antes que anchors con “onclick”.** Mejor semántica y accesibilidad.

2. **Declara siempre el `type`.** Evitas que un simple click dispare un formulario por error.

3. **Añade texto legible dentro del botón.** No dependas solo de iconos; pon `<span class="sr-only">` si toca.

4. **Gestiona el estado “processing”**: deshabilita el botón hasta recibir respuesta del backend.

5. **Botones “toggle” ⇒ `aria-pressed`.** El lector de pantalla entiende el cambio “activado/desactivado”.

6. **No uses `innerHTML` para meter SVGs dinámicos.** Inserta elementos con DOM APIs, conserva eventos y accesibilidad.

7. **Estilos con clases, no inline.** Centraliza en tu hoja CSS (`.btn`, `.btn--primario`, etc.).

8. **Touch-friendly:** mínimo 44 × 44 px de área clickable; evita mini-botones imposibles de pulsar en móvil.

9. **Focus visible siempre.** Personaliza `:focus-visible` pero **no lo quites**; la gente con teclado lo necesita.

10. **Prueba con lectores de pantalla** (NVDA, VoiceOver). Si lo entienden ellos, lo entenderá todo el mundo.


---
