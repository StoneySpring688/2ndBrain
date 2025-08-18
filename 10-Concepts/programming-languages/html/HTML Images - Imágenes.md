---
title: "HTML Images - Imágenes"
type: concept
tags: [area/programming, topic/html, topic/images, level/beginner]
status: draft
last_reviewed: 2024-12-28
related_concepts: []
difficulty: beginner
domain: programming
language: html
concept_type: [syntax, element, feature]
---

Para poner imágenes basta con poner  ```<img>``` dentro del body, este tiene los siguientes parámetros:
- ```src=""``` ruta a la imagen
- ```height=""``` para modificar el alto de la imagen
- ```width=""``` para modificar el ancho de la imagen
- ```alt=""``` en caso de que no se muestre la imagen, se mostrará este texto, también será el texto que leerá el screen  reader

Si se pone la imagen dentro de una sección de hyperlink ```<a></a>```al hacer click a la imagen, llevará al link. Ejemplo:
```html
<body>

<h1>Esto es un pomerania</h1>

<a href="https://www.purina.es/encuentra-mascota/razas-de-perro/pomerania" target="_blank">

	<img src="pomeraniaPiscina.jpg"
	height="" width="420"
	alt="Esto es una imagen de un pomerania en una piscina">
	
</a>

<p>
	Haz click en la imagen para descubrir las razones por las 
	que deberías tener un pomerania.
</p>

</body>
```
