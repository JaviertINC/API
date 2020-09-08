# jtVoicer

jtVoicer es una herramienta de accesibilidad para páginas web, implementando Texto a Voz, para personas con dificultad visual y/o personas que no saben leer.

# ¿Dónde se usa?

Actualmente está integrado en mi página web personal [JaviertINC.cl](https://javiertinc.cl), para aumentar la accesibilidad al sitio web.

# ¿Cómo se usa?

Es muy fácil, solo debes clickear o accionar el botón para escuchar, y se transformará el texto elegido a voz.

##### API Key Required

Es necesario contar una clave api, para poder utilizar esta herramienta en tus proyectos.

# ¿Cómo se integra?



### Endpoint
```
GET https://javiertinc.cl/api/v1/jtVoicer/jt.voicer
```

### Parámetros
| Parámetro | Tipo | Valor por Defecto | Importancia | Descripción |
| :---: | :---: | :---: | :---: | --- |
| `text` | VARCHAR | `NULL` | Requerido | Ingresa el texto que quieres transformar a Voz. |
| `lang` | VARCHAR | `es-MX` | Opcional | Elige el idioma en el cual debe hablar la voz, ve [aquí](#idiomas) la lista de idiomas. |
| `volume` | FLOAT | `1.0` | Opcional | Volumen del audio de la voz. |
| `api` | VARCHAR | `NULL` | Requerido | Debes ingresar tu clave API pública. |


# Idiomas

| Idioma | Código |
| :---: | :---: |
| Español Latino | es-MX |
| Inglés USA | en-US |
| Español España | es-ES |
