# 🏗️ Creando una Maquetación Web con HTML Semántico y CSS

Para construir un sitio web bien organizado y adaptable, usamos **HTML semántico** para definir la estructura y **CSS** para el diseño visual y la disposición de los elementos.

---

## 뼈 HTML Semántico: El Esqueleto con Significado

En lugar de usar `<div>` para todo, el HTML semántico utiliza etiquetas que describen su propio contenido. Esto mejora la accesibilidad para lectores de pantalla y el posicionamiento en buscadores (SEO).

### Estructura Principal

Una página web bien estructurada se divide en las siguientes partes:

- **`<header>`**: El encabezado. Contiene el título principal, el logo o la información de introducción.
    
- **`<nav>`**: La barra de navegación. Alberga los enlaces principales del sitio.
    
- **`<main>`**: El contenido principal. Es el contenedor para la información más importante de la página.
    
- **`<footer>`**: El pie de página. Incluye información de cierre como derechos de autor, contacto o enlaces secundarios.
    

### Contenedores dentro de `<main>`

Dentro del contenido principal, podemos organizar la información con más detalle:

- **`<section>`**: Agrupa contenido relacionado que forma parte de un todo.
    
- **`<article>`**: Contiene un bloque de contenido independiente y autocontenido, como una noticia o una publicación de blog, que podría tener sentido por sí solo.
    
- **`<aside>`**: Para contenido secundario o relacionado, como una barra lateral con información extra, publicidad o enlaces de interés.
    

---

## 🎨 CSS: Dando Estilo y Posición

Una vez definida la estructura con HTML, usamos CSS para darle vida y organizarla visualmente.

### 1. Preparación y Estilos Básicos

Primero, eliminamos los márgenes que los navegadores añaden por defecto y aplicamos estilos generales a los bloques principales.


```css
/* Quitar margen por defecto para que los bloques ocupen todo el ancho */
body {
  margin: 0;
  font-family: sans-serif;
}

/* Estilos para el encabezado y pie de página */
header, footer {
  background-color: #f2f2f2;
  text-align: center;
  padding: 20px;
}

/* Estilo para la barra de navegación */
nav {
  background-color: #333;
  height: 50px;
}
```

### 2. Creando la Maquetación con `float`

Para colocar elementos como la barra lateral y el contenido principal uno al lado del otro, usamos la propiedad `float`.


```css
aside {
  float: left;
  width: 20%; /* Ocupa el 20% del ancho */
  padding: 15px;
}

section {
  float: left;
  width: 80%; /* Ocupa el 80% restante */
  padding: 15px;
}
```

🧠 **Importante**: Cuando se usan porcentajes y `padding`, los elementos pueden desbordarse. Para evitarlo, se añade `box-sizing: border-box;` que incluye el `padding` dentro del ancho total del elemento.


```css
aside, section {
  box-sizing: border-box;
}
```

### 3. Limpiando Flotantes (`clear`)

El `<footer>` debe aparecer debajo de los elementos flotantes (`aside` y `section`). Para asegurarnos de que así sea, usamos `clear: both;`.


```css
footer {
  /* ...otros estilos... */
  clear: both; /* Limpia los floats anteriores */
}
```

---

## 📱 Diseño Adaptable (Responsive Design)

Para que la página se vea bien en dispositivos móviles, usamos **Media Queries**. Estas reglas aplican estilos solo si se cumplen ciertas condiciones (como el ancho de la pantalla).

Por ejemplo, para que en pantallas de menos de 600px los elementos se apilen uno encima del otro:


```css
/* Estilos para pantallas pequeñas */
@media screen and (max-width: 600px) {
  aside, section {
    width: 100%; /* Cada elemento ocupa todo el ancho */
    float: none;   /* Se desactiva la flotación */
  }
}
```

Con esta regla, la maquetación de varias columnas se convierte en una sola columna, facilitando la lectura en móviles.