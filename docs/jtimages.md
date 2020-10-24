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

#### Return (Upload)
Al subir una imagen correctamente, retornará esta información en JSON:
```json
    {
        "status": 200,
        "hash": "P4eJog",
        "dhash": e2U8NnUEqba3,
        "size": 125472,
        "width": 512,
        "height": 512
    }
```

#### Error 500 (Upload)
Si al subir una imagen ha ocurrido un error al guardar la información, retornará lo siguiente:
```json
    {
        "status": 500,
        "msg": "No se han podido guardar los datos"
    }
```
#### Error 401 (Upload)
Si al enviar la imagen, no se envía el parametro `info`, retornará lo siguiente:
```json
    {
        "status": 401,
        "msg": "Falta información de la imagen"
    }
```
Si al enviar la imagen, esta está dañada, retornará lo siguiente
```json
    {
        "status": 401,
        "msg": "La imagen está dañada"
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

#### Return (Get)
Al solicitar información de una imagen, retornará lo siguiente:
```json
    {
        "status": 200,
        "name": "2_cover.jpg",
        "hash": "P4eJog",
        "mime": "image/jpeg",
        "width": 512,
        "height": 512,
        "size": 125472,
        "date": 1603460392
    }
```
#### Error 404 (Get)
Si la imagen solicitada no existe, retornará lo siguiente:
```json
    {
        "status": 404,
        "msg": "La imagen no existe"
    }
```
#### Error 401 (Get)
Si la solicitud no es correcta, retornará lo siguiente:
```json
    {
        "status": 401,
        "msg": "Ha fallado la solicitud"
    }
```

### Delete
Pronto.

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