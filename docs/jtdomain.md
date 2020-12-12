# jtDomain

jtDomain es una pequeña herramienta para uso personal y educativo en el cual capturo los dominios recientemente registrados y eliminados de Nic Chile. De esta forma puedo visitar páginas creadas hace poco aprendiendo nuevo estilos o patrones de diseño. Además de aumentar mi creatividad viendo nuevas ideas, junto con los dominios eliminados para crear o recrear proyectos junto a AFYRUS y YeslyDevs.

# ¿Dónde se usa?

Actualmente solo está integrada a una herramienta para un grupo cerrado de personas con claves APIs únicas.

### Agregar Registros
```
POST https://javiertinc.cl/api/v1/jtdomain/add
```

| Parámetro | Tipo | Método | Importancia | Descripción |
|:---------:|:----:|:------:|:-----------:|-------------|
| `data` | `VARCHAR` | POST | Requerido | Debes enviar un String en JSON con los datos del dominio. |
| `api` | `VARCHAR` | GET | Requerido | Debes ingresar tu Clave API única asociada a tu aplicación. |

Estructura del parámetro `data`  

| Parámetro | Tipo | Importancia | Descripción |
|:---------:|:----:|:-----------:|-------------|
| `domain` | `VARCHAR` |  Requerido | Nombre del dominio, sin el .cl |
| `length` | `INTERGER` |  Requerido | Longitud del dominio. |
| `reserve` | `INTERGER` |  Requerido | Si el dominio está reservado. (0 -> No \| 1 -> Sí) |
| `status` | `INTERGER` |  Requerido | Si el dominio está comprado o no. (0 -> No \| 1 -> Sí) |
| `date_reg` | `DATETIME` |  Requerido | Fecha en la que se registró el dominio en Nic o en tu sistema. |  

Ejemplo:
```json
    [
        {
            "domain": "luiscortes",
            "length": 10,
            "reserve": 1,
            "status": 1,
            "date_reg": "2020-11-21 23:17:36"
        },
        {
            "domain": "luiscortes2",
            "length": 11,
            "reserve": 1,
            "status": 0,
            "date_reg": "2020-12-11 20:44:00"
        }
    ]
```
Retornará información del registro, Status: 200(Satisfactorio) o 500(Error de registro), Count(La cantidad de registros que se hicieron)
```json
    {
        "status": 200,
        "count": 2
    }
```


### Listar Dominios
```
GET https://javiertinc.cl/api/v1/jtdomain/list
```

| Parámetro | Tipo | Método | Importancia | Descripción |
|:---------:|:----:|:------:|:-----------:|-------------|
| `search` | `VARCHAR` | GET | Opcional | Busca dominios que contengan el valor especificado. |
| `agent` | `NULL` | GET | Opcional | Busca dominios que el nombre del agente contengan valor especificado. (`search` requerido) |
| `length` | `INTERGER` | GET | Opcional | Mostrar solo dominios con la cantidad de caracteres especificados. |
| `status` | `INTERGER` | GET | Opcional | Mostrar solo dominios en el status especificado. |
| `reserve` | `NULL` | GET | Opcional | Mostrar solo dominios reservados. |
| `rev` | `NULL` | GET | Opcional | Mostrar dominios marcados para revisión. |
| `dis` | `NULL` | GET | Opcional | Mostrar dominios marcados como descartados. (Estos se autoeliminarán luego de 7 días) |
| `api` | `VARCHAR` | GET | Requerido | Debes ingresar tu Clave API Pública. |

Se pueden usar varios parametros a la vez.

Ejemplo:
```
GET https://javiertinc.cl/api/v1/jtdomain/list?api={CLAVE_API}&reserve&search=JaviertINC
```
Retornará:
```json
    {
    	"status": 200,
    	"count": 2,
    	"query": "javiertinc",
    	"data": [
    		[
    			{
    				"name": "javiertinc",
    				"length": 10,
    				"agent": "@JaviertINC",
    				"status": 1,
    				"reserved": 1,
    				"revision": 0,
    				"discarded": 0,
    				"date_reg": "2020-06-03 16:35:41",
    				"date_mod": "2020-12-12 20:03:11"
    			},
    			{
    				"name": "luiscortes",
    				"length": 10,
    				"agent": "@JaviertINC",
    				"status": 1,
    				"reserved": 1,
    				"revision": 0,
    				"discarded": 0,
    				"date_reg": "2020-11-21 23:17:36",
    				"date_mod": "2020-12-12 20:04:16"
    			}
    		]
    	]
    }
```