---
title: "Html audio"
type: concept
tags: [area/programming, topic/html, topic/html-audio, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: html
concept_type: [syntax, element, feature]
---

Para incrustar sonido en tu página solo necesitas la etiqueta `<audio>` con uno o varios `<source>` en su interior. Así de simple.

```html
<audio controls preload="metadata">
  <source src="audio/episodio.ogg"  type="audio/ogg">
  <source src="audio/episodio.mp3"  type="audio/mpeg">
  <!-- Mensaje de reserva -->
  Tu navegador no soporta la etiqueta <code>audio</code>.
</audio>

```

#### Atributos clave de `<source>`

- **`src="ruta/archivo"`** Ruta absoluta o relativa al fichero de audio.

- **`type="audio/formato"`** MIME type que indica el códec (ej. `audio/mpeg`, `audio/ogg`).  _Pon varios `<source>` con formatos distintos para que cada navegador elija el que entienda._

#### Atributos habituales de `<audio>`

- **`controls`** Muestra los controles nativos de reproducción (play, pausa, barra de progreso, volumen…).

- **`autoplay`** Empieza a sonar en cuanto se carga la página. Ojo: muchos navegadores lo bloquean si el audio no está silenciado.

- **`loop`** Reproduce en bucle infinito.

- **`muted`** Arranca silenciado—útil junto a `autoplay` para evitar bloqueos.

- **`preload`** Sugerencia al navegador sobre cuánto cargar antes de reproducir (`none`, `metadata`, `auto`). Ej : ```preload="none"```


#### Buenas prácticas rápidas

1. **Ofrece al menos MP3 y Ogg/Vorbis.** Así cubres prácticamente todos los navegadores.

2. **Incluye un texto de fallback** entre las etiquetas `<audio>` y `</audio>` para navegadores antediluvianos.

3. **No fuerces `autoplay`** salvo que tengas una razón de peso; molesta a los usuarios y puede afectar al SEO.

4. **Optimiza el bitrate.** Unos 128 kbps suelen bastar para voz y la mayoría de música en web; no malgastes ancho de banda.


Y listo: con estas cuatro cosas tienes audio web sólido, compatible y respetuoso con tu audiencia.
