# jtVoicer

jtVoicer es una herramienta de accesibilidad para páginas web, implementando Texto a Voz, para personas con dificultad visual y/o personas que no saben leer.

# ¿Dónde se usa?

Actualmente está integrado en mi página web personal [JaviertINC.cl](https://javiertinc.cl), para aumentar la accesibilidad al sitio web.

# ¿Cómo se usa?

Es muy fácil, solo debes clickear o accionar el botón para escuchar, y se transformará el texto elegido a voz.

##### API Key Required

Es necesario contar una clave api, para poder utilizar esta herramienta en tus proyectos.

# ¿Cómo se integra?

La API  está diseñada para funcionar de una forma simple, solo se deben integrar algunos valores y retornará un archivo `.jt-audio` de *128bits*, reproducible como audio en cualquier navegador y/o reproductor multimedia.

### Endpoint
```
GET https://javiertinc.cl/api/v1/jtVoicer/jt.voicer
```

### Parámetros

| Parámetro | Tipo | Valor por Defecto | Importancia | Descripción |
|:---------:|:----:|:-----------------:|:-----------:|-------------|
| `text` | `VARCHAR` | `NULL` | Requerido | Ingresa el texto que quieres transformar a Voz. Debe estar codificado para URL |
| `lang` | `VARCHAR` | `es-MX` | Opcional | Idioma con el que hablará la voz, revisa [aquí](#idiomas) la lista de idiomas disponibles. |
| `volume` | `FLOAT` | `1.0` | Opcional | Volumen de la voz en el audio. |
| `api` | `VARCHAR` | `NULL` | Requerido | Debes ingresar tu Clave API Pública. |

### Retorno
```
GET https://javiertinc.cl/api/v1/jtVoicer/jt.voicer?text=Hola%20Mundo&lang=es-MX&volume=0.7&api={CLAVE_API}
```

# Idiomas

| Idioma | Código |
| --- | :-----: |
| Español Latino | `es-MX` |
| Español España | `es-ES` |
| Inglés USA | `en-US` |
