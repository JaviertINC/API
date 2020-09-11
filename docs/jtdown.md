# jtDown.js

jtDown.js es un script simple escrito en Javascript, que tiene la función de formatear texto simple a código HTML, similar a [MarkDown](https://www.markdownguide.org/), pero una versión adaptada a mis herramientas.

👉 Ve esto mismo a todo color en  mi página de [documentación API](https://javiertinc.cl/api/docs/jtdown)

# ¿Dónde se usa?

Actualmente está integrado en el editor de mi herramienta [Teextus](https://javiertinc.cl/teextus) y en mi creador de publicaciones en [mi blog](https://javiertinc.cl/blog).

# Sintaxis

El sintaxis básico de jtDown está basado en el funcionamiento de MarkDown.


### Títulos

Para crear un encabezado, agregue signos numéricos o hashtag `#` delante de una palabra o frase. El número de signos numéricos que utilice debe corresponder al nivel de título. Por ejemplo, para crear un título de nivel tres `<h3>`, utilice tres signos numéricos (por ejemplo, `### Hola Mundo`).

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `# Título 1` | `<h1>Título 1</h1>` | <h1>Título 1</h1> | 
| `## Título 2` | `<h2>Título 2</h2>` | <h2>Título 2</h2> |
| `### Título 3` | `<h3>Título 3</h3>` | <h3>Título 3</h3> |
| `#### Título 4` | `<h4>Título 4</h4>` | <h4>Título 4</h4> |
| `##### Título 5` | `<h5>Título 5</h5>` | <h5>Título 5</h5> |
| `###### Título 6` | `<h6>Título 6</h6>` | <h6>Título 6</h6> |

Por compatibilidad, siempre ponga un espacio entre los signos numéricos y el nombre del encabezado. En caso contrario, no se considerará como un título.

| Uso Correcto | Uso Incorrecto |
| --- | --- |
| `# Hola Mundo` | `#Hola Mundo` |


### Párrafos

Para crear párrafos, use una línea en blanco para separar una o más líneas de texto.

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `Hola Mundo` | `<p>Hola Mundo</p>` | <p>Hola Mundo</p> |
| ```Lorem ipsum eius exercitationem expedita id sunt tempora. Totam quia nihil reprehenderit laborum. Quia suscipit aut et.``` | ```<p>Lorem ipsum eius exercitationem expedita id sunt tempora. Totam quia nihil reprehenderit laborum. Quia suscipit aut et.</p>``` | <p>Lorem ipsum eius exercitationem expedita id sunt tempora. Totam quia nihil reprehenderit laborum. Quia suscipit aut et.</p> |


### Saltos de Linea

Para crear un salto de línea `<br>`, finalice una línea con dos o más espacios y luego escriba ENTER.
También con dos saltos de linea (ENTER ENTER)  
(Representé los dos espacios con guines bajos para mejor visualización, pero se deben usar dos espacios)

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `Hola Mundo__`<br/>`Hello World` | `<p>Hola Mundo<br/>Hello World</p>` | <p>Hola Mundo<br/>Hello World</p> |
| `Hola Mundo`<br/><br/>`Hello World` | `<p>Hola Mundo<br/>Hello World</p>` | <p>Hola Mundo<br/>Hello World</p> |


### Bold (Negrita)

Para poner el texto en negrita, agregue dos asteriscos bajos antes y después de una palabra o frase. Para poner en negrita la mitad de una palabra para dar énfasis, agregue dos asteriscos sin espacios alrededor de las letras.


| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `**Hola Mundo**` | `<strong>Hola Mundo</strong>` | <strong>Hola Mundo</strong> |
| `**Hola M**undo` | `<strong>Hola M</strong>undo` | <strong>Hola M</strong>undo |


### Italic (Cursiva)

Para poner el texto en cursiva, agregue dos slash `//` antes y después de una palabra o frase. Para poner en cursiva la mitad de una palabra para dar énfasis, agregue el doble slash sin espacios alrededor de las letras.

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `//Hola Mundo//` | `<em>Hola Mundo</em>` | <em>Hola Mundo</em> |
| `//Hola M//undo` | `<em>Hola M</em>undo` | <em>Hola M</em>undo |


### Strikethrough (Tachado)

Para tachar el texto, agregue dos almhoadillas `~~` antes y después de una palabra o frase. Para tachar la mitad de una palabra para dar énfasis, agregue el doble almohadillas sin espacios alrededor de las letras.

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `~~Hola Mundo~~` | `<del>Hola Mundo</del>` | <del>Hola Mundo</del> |
| `~~Hola M~~undo` | `<del>Hola M\</del>undo` | <del>Hola M</del>undo |


### Underline (Subrayado)

Para subrayar el texto, agregue dos guiones bajo `__` antes y después de una palabra o frase. Para tachar la mitad de una palabra para dar énfasis, agregue los dos guiones bajos sin espacios alrededor de las letras.

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `__Hola Mundo__` | `<u>Hola Mundo</u>` | <u>Hola Mundo</u> |
| `__Hola M__undo` | `<u>Hola M</u>undo` | <u>Hola M</u>undo |


### Citas (Quotes)

Para citar textos, agregue dos puntos con doble comillas `:"` antes y doble comillas con dos puntos `":` después de una palabra o frase.

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `:"Hola Mundo":` | `<q>Hola Mundo</q>` | <q>Hola Mundo</q> |


### Citas en bloques (Blockquotes)

Para citar textos en un bloque, agregue un signo mayor al inicio de una linea de texto.

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `> Hola Mundo` | `<blockquote>Hola Mundo</blockquote>` | <blockquote>Hola Mundo</blockquote> |


### Enlaces

Para crear un enlace, incluya el texto del enlace entre corchetes (por ejemplo, `[Web de JaviertINC]`) y luego sígalo inmediatamente con la URL entre paréntesis (por ejemplo, `(https://javiertinc.cl)`).

| jtDown | Código en HTML | Previsualización |
|---|---|---|
| `[Web de JaviertINC](https://javiertinc.cl)` | `<a href="https://javiertinc.cl" target="_blank">Web de JaviertINC</a>` | <a href="https://javiertinc.cl" target="_blank">Hola Mundo</a> |


# Extras

### Icons

También es posible integrar iconos de [FontAwesome](https://fontawesome.com/icons) y jt.icons.faithful.css (PRONTO más documentación)

Ingresa `<3` para retornar un icono de corazón con FontAwesome.

```
!!fa-moon
!!far-moon
!!fab-github
!!jti-mc-diamond-pickaxe  [BETA]
```

### Captys Embed

También puedes integrar capturas compartidas a través de Captys.
Similar a un enlace, pero debes definir estos valores \[captys-ANCHOxALTO](ID o enlace de la captura)

```
[captys-512x512](wchlMyp)
[captys-512x512](https://javiertinc.cl/captys/c/wchlMyp)
```
Nota: En Captys, al subir tu captura, se generará un código de Inserción EMBED para Teextus, puedes copiarlo listo para usar con jtDown.js


### Youtube Embed Videos

También puedes insertar videos de Youtube de una forma muy fácil.
Similar a un enlace, pero debes definir estos valores \[yt](ID o enlace del video)

```
[yt](PZmhpH7DPug)
[yt](https://youtu.be/PZmhpH7DPug)
[yt](https://youtube.com/watch?v=PZmhpH7DPug)
[yt](https://youtube.com/embed/PZmhpH7DPug)
[yt](https://www.youtube.com/watch?v=PZmhpH7DPug)
[yt](https://www.youtube.com/embed/PZmhpH7DPug)
[yt](https://www.youtube-nocookie.com/embed/PZmhpH7DPug)
```
