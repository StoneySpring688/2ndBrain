---
title: "Html videos"
type: concept
tags: [area/programming, topic/html, topic/html-videos, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: html
concept_type: [syntax, element, feature]
---

Insertar vídeo es tan fácil como usar la etiqueta `<video>` con uno o varios `<source>` dentro. Aquí va el patrón básico:
```html
<video controls preload="metadata" width="720" height="404" poster="img/vista-previa.jpg">
  <source src="video/clip.webm" type="video/webm">
  <source src="video/clip.mp4"  type="video/mp4">
  <!-- Subtítulos opcionales -->
  <track src="subtitulos.vtt" kind="subtitles" srclang="es" label="Español">
  Tu navegador no entiende la etiqueta <code>video</code>.
</video>

```

#### Atributos clave de `<source>`

- **`src="ruta/archivo"`** Ruta al archivo de vídeo.

- **`type="video/formato"`** MIME type: `video/mp4`, `video/webm`, `video/ogg`, etc. Incluye varios para máxima compatibilidad.


#### Atributos habituales de `<video>`

|Atributo|¿Para qué sirve?|
|---|---|
|`controls`|Muestra los controles nativos (play, pausa, volumen…).|
|`autoplay`|Reproduce nada más cargar la página.*|
|`muted`|Arranca silenciado; necesario si usas `autoplay`.|
|`loop`|Se repite en bucle infinito.|
|`preload`|`none`, `metadata` o `auto` (igual que en audio).|
|`poster="imagen.jpg"`|Imagen de portada mientras no se pulsa play.|
|`width` / `height`|Dimensiones fijas; si los omites, el vídeo mantiene su aspecto original.|
|`playsinline`|En móviles iOS evita que el vídeo se abra a pantalla completa.|

* _Los navegadores suelen bloquear `autoplay` con sonido: añade `muted` o no se reproducirá._

#### Subtítulos y accesibilidad

- Usa `<track kind="subtitles">` con archivos **WebVTT (`.vtt`)** para subtítulos.

- Añade varios idiomas (`srclang="en"`, `srclang="es"`, etc.) y usa el atributo `label`.

- Para descripciones de audio (narración para personas con discapacidad visual), emplea `kind="descriptions"`.


#### Buenas prácticas rápidas

1. **Ofrece al menos MP4 (H.264/AAC) y WebM (VP9/Vorbis).** Casi todo el mercado queda cubierto.

2. **Optimiza la resolución y el bitrate.** 720 p a ~2 Mbps es un punto medio razonable para web.

3. **Pon un `poster` atractivo** para mejorar la primera impresión y el CLS (Cumulative Layout Shift).

4. **Evita `autoplay` con sonido.** Molesta y puede aumentar la tasa de rebote.

5. **Carga diferida (`preload="none"` o lazy loading)** si incrustas muchos vídeos en la misma página.

6. **Cuida la accesibilidad:** subtítulos, descripciones de audio y contraste suficiente en los controles personalizados.

Con estas líneas tienes un reproductor de vídeo robusto, compatible y educado con tus usuarios. Sin complicaciones.
