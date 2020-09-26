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

Aún no disponible

---

# Código

### Extras

#### Función PHP
Una integración simple con PHP

``` php
<?php
    function jtImgUrl($id, $modder = ""){
    
        //Separa el ID de la imágen y la extensión.
    	$id = explode(".",$id);
    	
    	//Agrega el modificador si es que hay.
    	if($modder != ""){
    		$modder = "&m=" . $modder;
    	}else{
    		$modder = "";
    	}
    	
    	//Regresa el enlace generado.
    	return "https://javiertinc.cl/i/". $id[0] . "." . $id[1] . $modder;
	}
?>
```

##### Uso
``` php
<img src="<?= jtImgUrl("XmadCnE.png"); ?>" class="jt-image">
```