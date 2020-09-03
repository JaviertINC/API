# jtDown.js

jtDown.js es un script simple escrito en Javascript, que tiene la función de formatear texto simple a código HTML, similar a [MarkDown](https://www.markdownguide.org/), pero una versión adaptada a mis herramientas.

# ¿Dónde se usa?

Actualmente está integrado en el editor de mi herramienta [Teextus](https://javiertinc.cl/teextus) y en mi creador de publicaciones en [mi blog](https://javiertinc.cl/blog).

# Sintaxis

### Títulos

Para crear un encabezado, agregue signos numéricos o hashtag (#) delante de una palabra o frase. El número de signos numéricos que utilice debe corresponder al nivel de título. Por ejemplo, para crear un título de nivel tres (<h3>), utilice tres signos numéricos (por ejemplo, ### Mi encabezado).
Por compatibilidad, siempre ponga un espacio entre los signos numéricos y el nombre del encabezado. En caso contrario, no se considerará como un título.

| jtDown | Código en HTML |

|---|---|
| # Título 1 | <h1>Título 1</h1> |
| ## Título 2 | <h2>Título 2</h2> |
| ### Título 3 | <h3>Título 3</h3> |
| #### Título 4 | <h4>Título 4</h4> |
| ##### Título 5 | <h5>Título 5</h5> |
| ###### Título 6 | <h6>Título 6</h6> |
