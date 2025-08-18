---
title: "HTML Forms - Formularios"
type: concept
tags: [area/programming, topic/html, topic/forms, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: html
concept_type: [syntax, element, feature]
---


| Elemento / atributo | ¿Para qué sirve?                                       | Render por defecto                                         |
| ------------------- | ------------------------------------------------------ | ---------------------------------------------------------- |
| `<form>`            | Agrupa controles y gestiona el envío de datos.         | Bloque con margen superior/inferior (UA); `display:block`. |
| `action`            | URL destino del envío.                                 | Cadena vacía ⇒ recarga la página actual.                   |
| `method`            | Verbo HTTP (`get`, `post`, etc.).                      | `get` si se omite.                                         |
| `enctype`           | Codificación del cuerpo (`multipart/form-data`, etc.). | `application/x-www-form-urlencoded`.                       |
| `autocomplete`      | Activa/inhabilita autocompletado del navegador.        | `on` por defecto.                                          |
| `target`            | Ventana/iframe donde cargar la respuesta.              | `_self`.                                                   |
| `novalidate`        | Anula la validación HTML5 automática.                  | Sin atributo ⇒ se valida.                                  |
| `accept-charset`    | Lista de encodings permitidos.                         | Codificación del documento.                                |
| `name`              | Identificador lógico para JS y envío `<iframe>`.       | No afecta al render.                                       |
| `rel`               | Relación con la URL indicada en `action`.              | Vacío; poco usado.                                         |

---

#### Ejemplo

```html
<form id="alta-usuario"
      action="/usuarios"
      method="post"
      enctype="multipart/form-data"
      autocomplete="off"
      target="_blank">

  <fieldset>
    <legend>Datos personales</legend>

    <label>
      Nombre
      <input type="text" name="nombre" required
             autocomplete="given-name">
    </label>

    <label>
      Avatar
      <input type="file" name="avatar" accept="image/*">
    </label>
  </fieldset>

  <button type="submit" class="btn btn--primario">
    Crear cuenta
  </button>
</form>
```

- **`method="post"` + `enctype="multipart/form-data"`** son imprescindibles para subir archivos.

- **`action` vacío** reenvía al mismo recurso; acláralo siempre para evitar sorpresas.

- **`autocomplete`** mejora la UX: desactívalo sólo con motivos de peso (ej. datos sensibles).


---

#### Atributos esenciales

|Atributo|En|Valor típico|Comentario|
|---|---|---|---|
|`action`|`<form>`|`/endpoint`|Ruta absoluta o relativa de destino.|
|`method`|`<form>`|`post`|`get` expone datos en la URL.|
|`enctype`|`<form>`|`multipart/form-data`|Necesario para `<input type="file">`.|
|`autocomplete`|`<form>`|`on` / `off`|Coordina con `autocomplete` por campo.|
|`target`|`<form>`|`_self`, `_blank`|Dónde se recibe la respuesta.|
|`novalidate`|`<form>`|—|Deshabilita validación nativa.|
|`accept-charset`|`<form>`|`UTF-8`|Rara vez necesario hoy.|
|`name`|`<form>`|`alta`|Útil para formularios en `<iframe>`.|
|`rel`|`<form>`|`nofollow` (p.ej.)|Semántica adicional; poco soportado.|

---

#### Buenas prácticas

1. **Prefiere `post` para datos sensibles.** Evita URLs kilométricas y cacheadas con info privada.

2. **Declara siempre `action`.** Aun si es `""`, haz explícito el destino.

3. **Aprovecha `autocomplete`.** Pon `autocomplete="given-name"`, `email`, etc. en cada campo.

4. **Agrupa con `<fieldset>` + `<legend>`.** Estructura clara y accesible para lectores de pantalla.

5. **Asocia cada `<input>` a su `<label>`.** Área clicable y foco accesible; usa `for/id` o anidamiento.

6. **Valida en cliente y servidor.** HTML5 (`required`, `pattern`) ahorra frustración, pero el backend manda.

7. **Anuncia errores con ARIA.** Usa contenedores `role="alert"` o `aria-live="polite"` para feedback dinámico.

8. **Bloquea el “submit” mientras procesas.** Previene dobles envíos y estados corruptos.

9. **Forms largos ⇒ pasos cortos.** Mejora la tasa de finalización dividiendo en wizard o multistep.

10. **Test real: teclado, móvil, lector.** Asegura orden de tabulación, `:focus-visible` y targets ≥ 44 px.
    
---
