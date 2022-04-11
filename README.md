# INTEGRACIÓN STANDALONE
Para la integración StandAlone el afiliado debe pegar este código en el lugar de la página en la que quiere insertar el enlace de pago.

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
