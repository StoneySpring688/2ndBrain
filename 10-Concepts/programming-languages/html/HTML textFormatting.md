---
title: "Html textFormatting"
type: concept
tags: [area/programming, topic/html, topic/html-textformatting, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: html
concept_type: [syntax, element, feature]
---

Muestrario con las etiquetas más comunes para dar **énfasis y estructura** al texto:
```html
<p>
  <strong>Negrita semántica</strong>,
  <em>Cursiva semántica</em>,
  <b>Negrita “visual”</b>,
  <i>Cursiva “visual”</i>,
  <mark>Resaltado</mark>,
  <small>Texto pequeño</small>,
  <abbr title="HyperText Markup Language">HTML</abbr>,
  <sup>superíndice</sup>,
  <sub>subíndice</sub>,
  <code>printf("Hola");</code>,
  <pre>
function hola() {
  console.log("Hola");
}
  </pre>
  <q cite="https://ejemplo.com">Cita breve</q>
  <blockquote cite="https://ejemplo.com">
    Cita larga, para fragmentos de varios párrafos.
  </blockquote>
  <del>Texto eliminado</del>,
  <ins>Texto añadido</ins><br>
  —y un salto de línea manual justo aquí—<br>
  <hr>
</p>

```


| Etiqueta          | ¿Qué hace?                                                                                   | ¿Cuándo usarla?                                                          |
| ----------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| `<strong>`        | Resalta **fuertemente** un fragmento con importancia semántica (screen-readers lo anuncian). | Palabras clave, avisos e información crítica.                            |
| `<em>`            | Énfasis _moderado_; cambia el tono de voz en lectores de pantalla.                           | Matizar o contrastar términos (“no esto, sino _aquello_”).               |
| `<b>`             | Negrita **visual** sin valor semántico.                                                      | Sólo para destacar estético cuando la semántica no importa.              |
| `<i>`             | Cursiva _visual_ (traducido a _font-style: italic_).                                         | Títulos de obras, palabras extranjeras, etc., si no necesitas semántica. |
| `<mark>`          | Fondo amarillo (por defecto) para <mark>resaltar</mark> texto.                               | Resultados de búsqueda, fragmentos recién modificados, etc.              |
| `<small>`         | Reduce el tamaño de fuente (~80 %).                                                          | Notas al pie, disclaimers, copyright.                                    |
| `<abbr>`          | Marca una abreviatura; `title` muestra el término completo al pasar el ratón.                | Siglas (p. ej., <abbr title="As Soon As Possible">ASAP</abbr>).          |
| `<sup>` / `<sub>` | Superíndice y subíndice.                                                                     | Fórmulas químicas (H<sub>2</sub>O), potencias (x<sup>2</sup>).           |
| `<code>`          | Fuente monoespaciada; indica código inline.                                                  | Palabras clave, comandos (`git status`).                                 |
| `<pre>`           | Bloque preformateado: respeta espacios y saltos de línea.                                    | Fragmentos largos de código o ASCII art.                                 |
| `<q>`             | Cita corta _inline_; algunos navegadores añaden comillas automáticamente.                    | Frases cortas dentro de un párrafo.                                      |
| `<blockquote>`    | Cita larga en bloque; suele añadir sangría.                                                  | Extractos de artículos, discursos, etc.                                  |
| `<del>` / `<ins>` | <del>Tachado</del> y <ins>subrayado</ins> para indicar cambios.                              | Historial de revisiones, diffs.                                          |
| `<br>`            | Salto de línea manual.                                                                       | Poesía, direcciones postales; no abuses.                                 |
| `<hr>`            | Línea horizontal divisoria.                                                                  | Separar secciones temáticas dentro de un mismo documento.                |
#### Tips rápidos

1. **Prioriza la semántica sobre la apariencia.** Usa `<strong>` / `<em>` antes que `<b>` / `<i>` siempre que el énfasis tenga significado.

2. **No uses `<br>` para separar párrafos.** Cada párrafo va en su propio `<p>`; el `<br>` es solo para líneas aisladas.

3. **Combina con CSS, no la sustituyas.** Estos elementos marcan significado; el estilo final contrólalo con clases y CSS.

4. **Abreviaturas accesibles.** Pon siempre el atributo `title` en `<abbr>`; los lectores de pantalla leen la versión completa.

5. **`<pre>` + `<code>` = pareja perfecta.** Para bloques de código con formato y semántica correcta.

6. **Controla la jerarquía.** No anides `<strong>` dentro de `<em>` a menos que realmente quieras un énfasis doble.

Estas son las herramientas básicas para dar forma, tono y claridad al texto html.
