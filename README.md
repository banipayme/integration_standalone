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

**Tipo:** [String]

**Ejemplo:**

`paymentBaniPay('0ef291bf-0d70-444a-b949-b4144bba6557');`

___

# Proceso de pago

### 1. Botón de pago

El código generará un botón de pago en el espacio donde esté embebido el código de integración.

![boton](https://github.com/banipayme/integration_standalone/blob/main/img1.png?raw=true "Boton")

Al hacer click sobre **Pagar Ahora**, se abrirá un modal para que el cliente ingrese sus datos.

### 2. Registro del cliente.

El cliente deberá llenar los datos para la validación del KYC (Know Your Customer) de BaniPay, estos datos son importantes para validar algunos parámetros de la compra y para las reglas de control de riesgos.

![boton](https://github.com/banipayme/integration_standalone/blob/main/img3.png?raw=true "Boton")

**Nombre(s), Apellido(s)**, son campos tipo `String`, para el registro del cliente.

**Número de Documento**, es un campo `String` con el número de identidad correspondiente a cada país.

**Teléfono**, el sistema admite cualquier notación, pero en versiones posteriores correrá una validación por país, es aconsejable que el cliente ingrese el teléfono con código de país.

**E-Mail, Contraseña**, el e-mail y la contraseña son importantes para el sistema BaniPay porque son la base para la creación de usuario y posterior ingreso al sistema, así como también la tokenización (mas adelante se explica la tokenización de tarjetas).

### 3. Selección del medio de pago.

Posteriormente el cliente podrá escoger el medio de pago de su preferencia.

![boton](https://github.com/banipayme/integration_standalone/blob/main/img5.png?raw=true "Boton")

La interacción del cliente con la interfaz es simplemente escoger entre los cuatro medios de pago disponibles: **QR-Simple, Tarjeta de Crédito/Débito, Tigo Money, Billetera Soli**.

#### 3.1. Pago con QR-Simple

Si el cliente escoje pago con QR-Simple el sistema generará un código QR con el monto y la moneda fijados.

![boton](https://github.com/banipayme/integration_standalone/blob/main/img4.png?raw=true "Boton")

El cliente deberá escanear el código con su aplicación de banco que tenga QR-Simple, y aprobar el pago, posteriormente el sistema direccionará a la URL de transacción satisfactoria o erronea.

#### 3.2. Pago con Tarjeta de Crédito/Débito

Si el cliente escoje pago con Tarjeta de Débito/Crédito, el sistema desplegará un formulario para que el cliente ingrese los datos de su tarjeta.

![boton](https://github.com/banipayme/integration_standalone/blob/main/img6.png?raw=true "Boton")

Los datos **Número de teléfono, Dirección, Ciudad, País, Departamento y Código Postal** son muy importantes para las reglas de riesgo que se aplican a la transacción, la localización por ejemplo sirve para detectar transacciones sospechosas en lugares muy alejados en un mismo día, el **Código** postal puede ser llenado con *00000* en el caso de Bolivia, pero para tarjetas del exterior (especialmente USA) es muy importante para las reglas.

El correcto llenado de estos datos puede determinar una transacción exitosa o fallida, los mayores rechazos en transacciones suceden por datos que no coinciden.

**Nro de Tarjeta, CCV, Mes/Año (Expiración)**, son datos que van cifrados directamente a la red de VISA/MasterCard, no son guardados por nuestro sistema.

- **[x] ¿Quieres guardar esta tarjeta en tu cuenta BaniPay?**

Esta opción permite que los datos de la tarjeta sean guardados (tokenizados) en la cuenta BaniPay del usuario, como mencionamos en el paso **2 (Registro del cliente)** cuando un cliente crea un usuario e ingresa su correo y contraseña y escoge guardar la tarjeta, la red VISA/MasterCard genera un código (Token) con los datos de la tarjeta, el sistema BaniPay guarda ese token y lo utiliza para los próximos pagos que pueda hacer el cliente simplemente escogiendo su tarjeta sin necesidad de volver a ingresar sus datos nuevamente.

Cabe recalcar que por razones de seguridad, en ningún momento BaniPay guarda los datos de tarjeta del cliente, es VISA/MasterCard quien los guarda y BaniPay solo posee el token de acceso.

Si el cliente escoge la opción de guardar su tarjeta, en la próxima compra tendrá este ventana.

![boton](https://github.com/banipayme/integration_standalone/blob/main/img2.png?raw=true "Boton")

Donde solo ingresará su correo y contraseña, escogerá la tarjeta guardada y hará el pago.

### 4. Estado de la transacción.

Una vez terminada la transacción el sistema devuelve un mensaje de satisfacción o error, como explicamos arriba, el sistema devuelve el URL y el portal lo captura y despliega.

![boton](https://github.com/banipayme/integration_standalone/blob/main/img7.png?raw=true "Boton")
