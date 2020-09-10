# Captys

Una plataforma para compartir capturas e imágenes totalmente gratuita, sin registros ni contraseñas. [¡Pruebala ahora mismo!](https://javiertinc.cl/captys)

👉 Ve esto mismo a todo color en  mi página de [documentación API](https://javiertinc.cl/api/docs/captys)

# Captys Embed

¡Ahora puedes insertar tus capturas en tu página web y blogs!

### ¿Qué es Captys Embed?

*Captys Embed* es una excelente forma de mostrar tus capturas subidas a Captys fuera de la plataforma. Desde la inserción, los usuarios de tu página o blog podrán acceder a Captys para ver la imágen completa.

Para utilizarla solo debes copiar el enlace generado al momento de subir tu captura.

[captys-512x189](https://javiertinc.cl/captys/c/P3DzYwA)

El código es se verá así:
``` html
<blockquote class="jt-captys-embed" data-id="P3DzYwA" data-theme="captys" data-width="512" data-height="148">
  <a href="https://javiertinc.cl/captys/c/P3DzYwA" target="_blank">Ver captura</a>
</blockquote>
<script async src="//javiertinc.cl/libs/js/captys.embed.js" charset="utf-8"></script>
```

### ¡Más estilos!

También puedes cambiar el estilo de las targetas de inserción con estos 4 increibles temas:

- [Captys](#captys-theme)
- [Light](#light-theme)
- [Dark](#dark-theme)
- [DarkGreen](#darkgreen-theme)

```
  data-theme="THEME" 
```

#### Captys Theme

Captys Theme es el estilo original de la plataforma, si no se asigna ningún estilo, se verá con éste tema.

``` html
<blockquote class="jt-captys-embed" data-id="2ddgHDy" data-theme="captys" data-width="512" data-height="258">
  <a href="https://javiertinc.cl/captys/c/2ddgHDy" target="_blank">Ver captura</a>
</blockquote>
<script async src="//javiertinc.cl/libs/js/captys.embed.js" charset="utf-8"></script>
```

[captys-512x258](https://javiertinc.cl/captys/c/2ddgHDy)

#### Light Theme

Este tema está pensado para las páginas con un estilo de tonos claros.

``` html
<blockquote class="jt-captys-embed" data-id="T08Ftpk" data-theme="light" data-width="512" data-height="260">
  <a href="https://javiertinc.cl/captys/c/T08Ftpk" target="_blank">Ver captura</a>
</blockquote>
<script async src="//javiertinc.cl/libs/js/captys.embed.js" charset="utf-8"></script>
```

[captys-512x260](https://javiertinc.cl/captys/c/T08Ftpk)

#### Dark Theme

Este tema está pensado para las páginas con un estilo de tonos oscuros.

``` html
<blockquote class="jt-captys-embed" data-id="0dd7i4Q" data-theme="dark" data-width="512" data-height="260">
  <a href="https://javiertinc.cl/captys/c/0dd7i4Q" target="_blank">Ver captura</a>
</blockquote>
<script async src="//javiertinc.cl/libs/js/captys.embed.js" charset="utf-8"></script>
```

[captys-512x260](https://javiertinc.cl/captys/c/0dd7i4Q)

#### DarkGreen Theme

Este tema está pensado para las páginas con un estilo de tonos oscuros.

``` html
<blockquote class="jt-captys-embed" data-id="ePm22SM" data-theme="darkgreen" data-width="512" data-height="260">
  <a href="https://javiertinc.cl/captys/c/ePm22SM" target="_blank">Ver captura</a>
</blockquote>
<script async src="//javiertinc.cl/libs/js/captys.embed.js" charset="utf-8"></script>
```

[captys-512x260](https://javiertinc.cl/captys/c/ePm22SM)

# Subir una captura

### Upload Endpoint

```
POST https://javiertinc.cl/api/v1/captys/upload
```

### Upload Parameters

| Parámetro | Tipo | Valor por Defecto | Formato | Descripción |
| :---: | :---: | :---: | :---: | --- |
| `image` | `VARCHAR` | `NULL` | `base64(image_data_base64)` | Se debe ingresar la imágen codificada en base64 dos veces |
| `name` | `VARCHAR` | `captys-{hash-code}.{format_img}` | `{nombre}.{extensión}` |  El nombre de la captura |
| `mime` | `VARCHAR` | `NULL` | `image/{extensión}` | El formato MIME de la imágen, por ejemplo `image/png` |
| `api` | `VARCHAR` | `NULL` | `{CLAVE_API}` | Debes ingresar tu clave API |

### Upload Return
Retornará datos en JSON
``` json
{
    "status": 200,
    "id": "wchlMyp",
    "dhash": "oDvqzHwFvbqu0IP"
}
```
