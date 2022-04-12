# INTEGRACIÓN STANDALONE
Para la integración StandAlone el afiliado debe pegar este código en el lugar de la página en la que quiere insertar el enlace de pago.

```
<script src="https://modal-flask-dev-q5zse.ondigitalocean.app/static/js/banipay.js"></script> 
<script id="paymentScript"> 
BaniPay.business = "02e4b31f-20bd-43f9-9f2d-3ef7733f2d0f";
BaniPay.currency = "BOB";
BaniPay.total = 10.00;
BaniPay.description = "Pago por BaniPay";
BaniPay.image = "https://finconecta.com/wp-content/uploads/2021/04/FinConecta_ldraw-01.png";
BaniPay.externalCode = "123";
BaniPay.environmentType = "Dev";
BaniPay.notificationUrl = "https://webhook.site/4bf3a38e-a22e-4c5a-b4cf-b2f32b02746c";
BaniPay.successUrl = "https://webhook.site/4bf3a38e-a22e-4c5a-b4cf-b2f32b02746c";
BaniPay.failUrl = "https://webhook.site/4bf3a38e-a22e-4c5a-b4cf-b2f32b02746c";
paymentBaniPay('0ef291bf-0d70-444a-b949-b4144bba6557');
</script> 
```

Las variables a configurarse son:

___
### `BaniPay.business` 

Código de afiliado a BaniPay, este código se genera cuando el negocio crea una cuenta, si todavía no lo tiene el personal de BaniPay puede asistirle a obtenerlo. El formato que tiene el código es: `02e4b31f-20bd-43f9-9f2d-3ef7733f2d0f`

**Tipo:** [String]

**Ejemplo:** 

`BaniPay.business = "02e4b31f-20bd-43f9-9f2d-3ef7733f2d0f";`
___
### `BaniPay.currency`

Tipo de cambio asociado al monto, la notación del tipo de cambio está bajo el estándar [ISO 4217 CURRENCY CODES](https://www.xe.com/iso4217.php), actualmente BaniPay solo soporta `BOB` y `USD` como tipos de cambio, si enviase un monto con otro tipo de cambio diferente a esos dos, el sistema automáticamente convertirá el monto a `USD` al tipo de cambio fijado por el banco emisor de la tarjeta.

**Tipo:** [String]

**Ejemplo:**

`BaniPay.currency = "BOB";`

___

### `BaniPay.total`

Monto total para la transacción con dos espacios para decimales, los miles no llevan ninguna puntuación.

**Tipo:** [Float]

**Ejemplo:**

`BaniPay.total = 10.00;`

___

### `BaniPay.description`

Descripción del pago, el máximo de la cadena es de 255 caracteres.

**Tipo:** [String]

**Ejemplo:**

`BaniPay.description = "Pago por BaniPay";`

___

### `BaniPay.image`

URL de imagen del producto o negocio, esta variable es opcional, si no se define el sistema simplemente no mostrará una imagen, no afecta al correcto funcionamiento de la modal, la URL debe iniciar con el formato `https://` o `http://`.

**Tipo:** [URL]

**Ejemplo:**

`BaniPay.image = "https://finconecta.com/wp-content/uploads/2021/04/FinConecta_ldraw-01.png";`

___

### `BaniPay.externalCode`

Código de uso de la empresa, es un código que puede usar para señalar la transacción.

**Tipo:** [String]

**Ejemplo:**

`BaniPay.externalCode = "PROD-1023";`

___

### `BaniPay.environmentType`

El tipo de ambiente al cual se va a conectar, inicialmente es aconsejable hacer pruebas en el ambiente de **desarrollo** `Dev`, luego cuando se terminen las pruebas satisfactorias de integración se procede a conectarse al ambiente de **producción** `Prod`

**Tipo:** [String]

**Ejemplo:**

`BaniPay.environmentType = "Dev";`

`BaniPay.environmentType = "Prod";`

___

### `BaniPay.notificationUrl`

URL donde el sistema notificará la respuesta de la transacción después de haberlo procesado, esta variable es opcional, si no se declara no afecta la transacción.

**Tipo:** [URL]

**Ejemplo:**

`BaniPay.notificationUrl = "https://webhook.site/4bf3a38e-a22e-4c5a-b4cf-b2f32b02746c";`

___

### `BaniPay.successUrl`

URL donde el sistema direccionará una *transacción exitosa*, es usada para desplegar el mensaje de satisfacción personalizado, la variable es opcional, si no se declara no afecta la transacción, sin embargo es recomendable desplegar un mensaje de información después de la transacción.

**Tipo:** [URL]

**Ejemplo:**

`BaniPay.successUrl = "https://webhook.site/4bf3a38e-a22e-4c5a-b4cf-b2f32b02746c";`

___

### `BaniPay.failUrl`

URL donde el sistema direccionará una *transacción fallida*, es usada para desplegar el mensaje de error personalizado, la variable es opcional, si no se declara no afecta la transacción, sin embargo es recomendable desplegar un mensaje de error después de la transacción.

**Tipo:** [URL]

**Ejemplo:**

`BaniPay.failUrl = "https://webhook.site/4bf3a38e-a22e-4c5a-b4cf-b2f32b02746c";`

___

### `paymentBaniPay('{{affiliateId}}')`

Completar con el código de afiliado.

**Tipo:** [URL]

**Ejemplo:**

`paymentBaniPay('0ef291bf-0d70-444a-b949-b4144bba6557');`

___

El código generará un botón de pago en el espacio que lo haya insertado.


