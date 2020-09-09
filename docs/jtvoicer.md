# jtVoicer

jtVoicer es una herramienta de accesibilidad para páginas web, implementando Texto a Voz, para personas con dificultad visual y/o personas que no saben leer.

# ¿Dónde se usa?

Actualmente está integrado en mi página web personal [JaviertINC.cl](https://javiertinc.cl), para aumentar la accesibilidad al sitio web.

# ¿Cómo se usa?

Es muy fácil, solo debes clickear o accionar el botón para escuchar, y se transformará el texto elegido a voz.

##### API Key Required

> Es necesario contar una clave api, para poder utilizar esta herramienta en tus proyectos. Puedes adquirir tu clave API [aquí](https://javiertinc.cl/api/apikey).

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

### Ejemplo
```
GET https://javiertinc.cl/api/v1/jtVoicer/jt.voicer?text=Hola%20Mundo&lang=es-MX&volume=0.7&api={CLAVE_API}
```

# Integración a la Web
La integración mostrada a continuación, requiere FontAwesome, jQuery y Popper.js
El código aquí mostrado, fue creado y diseñado para mi página web.

### HTML
```
<!-- Botón para ejecutar la función -->
    <jt data-jtvoicer="{TEXTO_A_TRANSFORMAR}" data-toggle="tooltip" title="Escuchar" tabindex="0">
        <i class="fa fa-volume-up fa-fw"></i> Escuchar
    </jt>

<!-- Aquí están los modificadores de jtVoicer -->
    <!-- Modificador de Volumen -->
    <input type="hidden" id="jtVoicerVolume" value="1.0">
    
    <!-- Modificador de Idioma -->
	<input type="hidden" id="jtVoicerLang" value="es-MX">
	
    <!-- Reproductor del audio -->
	<div data-jt-voice="{CLAVE_API}"></div>
	
    <!-- Botón de STOP para detener el audio -->
	<div id="jtVoicerStop" style="background: url('https://i.yesly.cl/jt/lxaxaTKUccBlUJCNUoh77w');">
	    <i class="fa fa-stop fa-fw"></i>
	</div>
```
### Javascript
```
    //Detecta cuando se haga click en los botónes jtVoicer y ejecuta la función
    $("[data-jtvoicer]").on('click',function(){
        var msg = $(this).data("jtvoicer");
    	jtVoicer(msg);
    });
    
    //Detecta cuando se ejecuta a través de el teclado con la tecla ENTER
    $("[data-jtvoicer]").on("keypress",function(e){
    	if(e.which == 13) {
    		var msg = $(this).data("jtvoicer");
    		jtVoicer(msg);
    	}
    });
   
   //Detecta cuando se clickea el botón de STOP
    $("#jtVoicerStop").on('click',function(){
	    jtVoicer_stop();
    });
    
    //Función para detener el audio 
    function jtVoicer_stop(){
    	$("#jtVoicerPlayer").remove();
    	$("#jtVoicerStop").removeClass("active");
    }
    
    //Función para ejecutar el audio
    function jtVoicer(txt) {
    	var lang = $("#jtVoicerLang").val();
    	var volume = $("#jtVoicerVolume").val();
    	if(volume > 0.1 && volume < 1.1){
    		$("#jtVoicerStop").addClass("active");
    		var r = "https://javiertinc.cl/api/v1/jtVoicer/jt.voicer?text="+ encodeURI(txt) +"&lang=" + lang + "&volume="+ volume +"&api={CLAVE_API}";
    		$("[data-jt-voice]").html('<audio id="jtVoicerPlayer" src="' + r +'" autoplay>');
    		$("#jtVoicerPlayer").bind("ended", function() {
    			jtVoicer_stop();
    		});
    	}
    }
    
```
### CSS

Estilos diseñados para mi página web
```
    /* Estilos para el botón jtVoicer */
    [data-jtvoicer]{
    	color: #fff;
    	margin: 0 .3rem;
    	padding: .05rem .2rem;
    	cursor: pointer;
    	border: 1px solid #4caf50;
    	background-color: rgba(255,255,255,.2);
    	border-radius: 5px;
    	display: inline-block;
    	font-size: 1rem;
    }
    [data-jtvoicer]:hover{
    	background-color: rgba(255,255,255,.3);
    }
    
    /* Estilos para el botón STOP */
    #jtVoicerStop{
    	color: #fff;
    	border: 1px solid #4caf50;
    	border-right: none;
    	position: fixed;
    	top: 200px;
    	right: 0;
    	padding: 1rem;
    	border-radius: 5px 0 0 5px;
    	cursor: pointer;
    	z-index: 99999999;
    	display: none;
    	transition: display .3s;
    	background-color: #4c4c4c!important;
    	background-size: auto 100% !important;
    }
    #jtVoicerStop.active{
    	display: block;
    }
```


# Idiomas

| Idioma | Código |
| --- | :-----: |
| Español Latino | `es-MX` |
| Español España | `es-ES` |
| Inglés USA | `en-US` |
