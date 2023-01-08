<!DOCTYPE html>

<html>
    <head>
        <meta charset="utf-8">
        <title>Starry Shop</title>
    </head>

    <body>
        <h1>Starry Shop!</h1>
        <h2>7.99€ 1200 Robux Par mois!</h2>
    </body>

    <div id="smart-button-container">
      <div style="text-align: center;">
        <div id="paypal-button-container"></div>
      </div>
    </div>
  <script src="https://www.paypal.com/sdk/js?client-id=AYGSFT5T63vou-N7X8pDjx9YyHA1IChLaMPh6XitvrpUWVMhBylBrGA3Y-eMh2AxvbJhML_d_4jk9oew&enable-funding=venmo&currency=EUR" data-sdk-integration-source="button-factory"></script>
  <script>
    function initPayPalButton() {
      paypal.Buttons({
        style: {
          shape: 'rect',
          color: 'gold',
          layout: 'vertical',
          label: 'paypal',
          
        },

        createOrder: function(data, actions) {
          return actions.order.create({
            purchase_units: [{"description":"1200 Robux par mois","amount":{"currency_code":"EUR","value":7.99}}]
          });
        },

        onApprove: function(data, actions) {
          return actions.order.capture().then(function(orderData) {
            
            // Full available details
            console.log('Capture result', orderData, JSON.stringify(orderData, null, 2));

            // Show a success message within this page, e.g.
            const element = document.getElementById('paypal-button-container');
            element.innerHTML = '';
            element.innerHTML = '<h3>Thank you for your payment!</h3>';

            // Or go to another URL:  actions.redirect('thank_you.html');
            
          });
        },

        onError: function(err) {
          console.log(err);
        }
      }).render('#paypal-button-container');
    }
    initPayPalButton();
  </script>







    </html>
