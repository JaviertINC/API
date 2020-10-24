# jtImages

jtImages es un sistema de imágenes privado que creé para mis proyectos.

# ¿Dónde se usa?

Actualmente está integrado en muchos de mis proyectos, algúnos son:

- Mi Sitio Web Personal
- YeslyDevs
- Captys
- Teextus
- Red AFYRUS

# Integración

La integración de jtImages no es compleja

# Código

### Upload
```
POST https://javiertinc.cl/api/v1/jtimages/upload
```

| Parámetro | Tipo | Importancia | Descripción |
|:---------:|:----:|:-----------:|-------------|
| `image` | `base64(image)` | Requerido | Debes enviar la imagen codificada en base64. |
| `info` | `JSON` | Requerido | En este parametro va información como el nombre y el tipo de imagen |
| `api` | `VARCHAR` | Requerido | Debes ingresar tu Clave API Pública asociada a tu aplicación. |

Estructura del parámetro `info`
```json
    {
        "name": "{Nombre del archivo}",
        "mime": "{tipo de la imagen}",
        "ip": "{ip del usuario que subió la imagen}"
    }
```
Ejemplo:
```json
    {
        "name": "jtImages.png",
        "mime": "image/png",
        "ip": "8.8.8.8"
    }
```

### Get
```
GET https://javiertinc.cl/api/v1/jtimages/get
```

| Parámetro | Tipo | Importancia | Descripción |
|:---------:|:----:|:-----------:|-------------|
| `hash` | `VARCHAR` | Requerido | Debes ingresar el Hash de una imagen subida a jtImages. |
| `api` | `VARCHAR` | Requerido | Debes ingresar tu Clave API Pública. |

### Extras

#### Función PHP
Una integración simple con PHP

``` php
<?php
    function jtImgUrl($id, $modder = ""){
    
    	//Agrega el modificador si es que hay.
    	if($modder != ""){
    		$modder = "&m=" . $modder;
    	}
    	
    	//Regresa el enlace generado.
    	return "https://javiertinc.cl/i/". $id . $modder;
    }
?>
```

##### Uso
``` php
<img src="<?= jtImgUrl("XmadCnE.png"); ?>" class="jt-image">
```