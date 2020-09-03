# jtDown.js

jtDown.js es un script simple escrito en Javascript, que tiene la función de formatear texto simple a código HTML, similar a [MarkDown](https://www.markdownguide.org/), pero una versión adaptada a mis herramientas.

# ¿Dónde se usa?

Actualmente está integrado en el editor de mi herramienta [Teextus](https://javiertinc.cl/teextus) y en mi creador de publicaciones en [mi blog](https://javiertinc.cl/blog).

# Sintaxis

El sintaxis básico de jtDown está basado en el funcionamiento básico de MarkDown.

### Títulos

Para crear un encabezado, agregue signos numéricos o hashtag (#) delante de una palabra o frase. El número de signos numéricos que utilice debe corresponder al nivel de título. Por ejemplo, para crear un título de nivel tres (\<h3>), utilice tres signos numéricos (por ejemplo, ### Mi encabezado).

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| # Título 1 | \<h1>Título 1\</h1> | <h1>Título 1</h1> | 
| ## Título 2 | \<h2>Título 2\</h2> | <h2>Título 2</h2> |
| ### Título 3 | \<h3>Título 3\</h3> | <h3>Título 3</h3> |
| #### Título 4 | \<h4>Título 4\</h4> | <h4>Título 4</h4> |
| ##### Título 5 | \<h5>Título 5\</h5> | <h5>Título 5</h5> |
| ###### Título 6 | \<h6>Título 6\</h6> | <h6>Título 6</h6> |

Por compatibilidad, siempre ponga un espacio entre los signos numéricos y el nombre del encabezado. En caso contrario, no se considerará como un título.

| Uso Correcto | Uso Incorrecto |
| --- | --- |
| # Hola Mundo | #Hola Mundo |

---

### Parrafos

Para crear párrafos, use una línea en blanco para separar una o más líneas de texto.

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| Hola Mundo | \<p>Hola Mundo\</p> | <p>Hola Mundo</p> |
| Lorem ipsum eius exercitationem expedita id sunt tempora. Totam quia nihil reprehenderit laborum. Quia suscipit aut et. | \<p>Lorem ipsum eius exercitationem expedita id sunt tempora. Totam quia nihil reprehenderit laborum. Quia suscipit aut et.\</p> | <p>Lorem ipsum eius exercitationem expedita id sunt tempora. Totam quia nihil reprehenderit laborum. Quia suscipit aut et.</p> |

---

### Saltos de Linea

Para crear un salto de línea (\<br>), finalice una línea con dos o más espacios y luego escriba ENTER.
También con dos saltos de linea (ENTER ENTER)

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| Hola Mundo  \nHello World | \<p>Hola Mundo\<br/>Hello World\</p> | <p>Hola Mundo<br/>Hello World</p> |
| Hola Mundo\n\nHello World | \<p>Hola Mundo\<br/>Hello World\</p> | <p>Hola Mundo<br/>Hello World</p> |
