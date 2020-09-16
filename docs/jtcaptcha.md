# jtCaptcha

jtCaptcha es un simple script en PHP y Javascript que funciona como Captcha básico para evitar bots programados no deseados usen nuestros formularios para llenarnos de SPAM.
Este es un simple Captcha que usa operaciones básicas de aritmética.

[captys-512x226](https://javiertinc.cl/captys/c/0H4ehah)

# ¿Dónde se usa?

Actualmente está integrado en mi formulario de contacto.

# Código

### Genera la operación

``` php
<?php
    //Genera números aleatorios para la operación
    $captcha_num1 = rand(0,9);
    $captcha_num2 = rand(0,9);
    
    //Genera de forma aleatoria la operación
    $captcha_oper = rand(0,1);
    
    //Procesa la operación
        //1 es Suma
        if($captcha_oper == 1){
            //Obtiene el resultado de la operación
        	$captcha_num3 = $captcha_num1 + $captcha_num2;
        	
        	//Guarda el operador como carácter
        	$captcha_oper = "+";
        //0 es Resta
        }else{
            //Obtiene el resultado de la operación
        	$captcha_num3 = $captcha_num1 - $captcha_num2;
        	
        	//Guarda el operador como carácter
        	$captcha_oper = "-";
        }
?>
```

### Muestra la operación
``` php
<div class="jt-captcha">
	<div class="jt-captcha-operation">
	    <span><?= $captcha_num1; ?></span>
	    <span><?= $captcha_oper; ?></span>
	    <span><?= $captcha_num2; ?></span>
	    <span> = </span>
	</div>
    <input type="number" class="jt-captcha-input" id="jtCaptcha" placeholder="?">
</div>
```

### Comprueba la operación
En Javascript
``` php
<script>
// Debes enviar el resultado correcto codificado en base64
if(jtCaptcha("jtCaptcha","<?php echo base64_encode($captcha_num3); ?>")){
    // Código para enviar mensaje
}else{
    alert("La operación es incorrecta, sigue intentando.");
}
</script>
```

### Función verificadora
``` js
function jtCaptcha(id, n2){
    //Obtiene valor ingresado en el input
	let n1 = document.getElementById(id).value;
	
	//Verifica que el input no esté vacío
	if(n1 != ""){
	    //Comprueba que el valor ingresado en el input sea igual al resultado correcto
		if(n1 == atob(n2)){
		    //Regresa TRUE para continuar en positivo el callback
			return true;
		}else{
		    alert("Tu respuesta al ejercicio matemático es incorrecta,\nsigue intentando, ¡Ánimo!");
		}
	}else{
		alert("Debes completar el ejercicio matemático,\nno es tán díficil :D\nesto ayuda a mantener tu mente saludable");
	}
}
```

### Extra
Comprueba que no ingrese numeros que es imposible que den como resultado
``` js
$("#jtCaptcha").on("keyup",function(){
    //Verifica que no se ingresen valores mayores a 2 digitos
	if(this.value.length > 2){
		this.value = this.value.substring(0,2);
	}
	//Verifica que no se ingresen valores mayores a 18
	if(this.value > 18){
		this.value = this.value.substring(0,1);
	}
});
```