![image](https://user-images.githubusercontent.com/57352037/170198396-932692aa-3354-4cf0-abc1-2b8ef43a6de3.png)


# ShurjoPay

## To integrate the shurjoPay Payment Package in your Laravel project,Please do the following seven steps sequentially.At-first make sure your device has the proper environment set-up for running PHP / Laravel project.


# Step-1: 
Open your project's "composer.json" file.Then add below configuration lines in your "composer.json"

`` "require": {
              "shurjomukhi/shurjopay-laravel-plugin":"dev-feature/laravel"
             }
``

`` "repositories": [
                        {
                            "type": "vcs",
                            "url": "https://github.com/shurjopay-plugins/sp-plugin-laravel.git"
                        }
                    ]
``

# Step-2: 
Open project's terminal and give command,

``
composer update
``

# Step-3:  
Then go to your project and open config folder and then click on app.php file. Append the following line in providers array.

``
Shurjomukhi\ShurjopayLaravelPlugin\ShurjopayServiceProvider::class,
``

# Step-4: 
Add the following Keys in ".env" file with the credentials provided from shurjoMukhi Limited. If there are no existing of ".env" file then kindly add that file and then setup below configurations into your ".env" file.


``MERCHANT_USERNAME="sp_sandbox"
``

``MERCHANT_PASSWORD="pyyk97hu&6u6"
``

``MERCHANT_RETURN_URL="https://www.sandbox.shurjopayment.com/response"
``

``MERCHANT_CANCEL_URL="https://www.sandbox.shurjopayment.com/response"
``

``ENGINE_URL="https://sandbox.shurjopayment.com"
``

# Step-5: 
Then, Please run below commands  -

``php artisan vendor:publish --tag=shurjopay
`` 

Below commands are optional but you should use these for ignoring unwanted issues. [ Ex. cache issues or others]

``composer dump-autoload
``

``php artisan optimize:clear
``
  
# Step-6:
 Now, your application is ready to integrate shurjoPay package. Add this line of code in your method where you want to call shurjoPay Payment Gateway. You can use any code segment of below

### Add below lines in your controller :-


``
use Shurjomukhi\ShurjopayLaravelPlugin\Http\Controllers\Shurjopay;
``

``
use Shurjomukhi\ShurjopayLaravelPlugin\Http\Controllers\TransactionClasses\PaymentRequest;
``

### First make sure you are doing http post request [Illuminate\Http\Request] or sending an array for making payment into your method with values of below fields :-

``
'currency' =>' ',
``

``
'amount' =>' ',
``

``
'order_id' =>' ',
``

``
'discount_amount' =>' ',
``

``
'disc_percent' =>' ' ,
``

``
'client_ip' =>' ',
``

``
'customer_name' =>' ',
``

``
'customer_phone' =>' ',
``

``
'customer_email' =>' ',
``

``
'customer_address' =>' ',
``

``
'customer_city' =>' ',
``

``
'customer_state' =>' ',
``

``
'customer_postcode' =>' ',
``

``
'customer_country' =>' ',
``

``
'shipping_address' =>' ',
``

``
'shipping_city' =>' ',
``

``
'shipping_country' =>' ',
``

``
'received_person_name' =>' ',
``

``
'shipping_phone_number' =>' ',
``


# Then in your payment method you need to add below lines

``$request = new PaymentRequest($requestArray);
``

``$shurjopay_service = new Shurjopay();
``

``return $shurjopay_service->makePayment($request);
``
# For verifying :-

``
   $shurjopay_instance = new Shurjopay();
``

`` 
   return $shurjopay_instance->verifyPayment($order_id);
``	

# Step-7:
Now application is ready to work. Just give another command in terminal

``
  php artisan serve
``

### Who do I talk to? ###
	For any technical assistance please contact to: https://shurjopay.com.bd/#contacts


# A sample shurjopay integration is given below for better understanding to users :

1. First, I am going to create a laravel project to integrate shurjopay payment package named as "ShurjopayIntegration"
   
   ``composer create-project laravel/laravel ShurjopayIntegration
   ``
2. Following Step-1. Now, Going to change "ShurjopayIntegration" project's composer.json.

3. Following Step-2.

   ``composer update
   ``
4. Following Step-3. Add service provider in config/app.php into "providers" array. .

``
Shurjomukhi\ShurjopayLaravelPlugin\ShurjopayServiceProvider::class,
``
5. Following Step-4.Configuring .env file with credentials
   .env
6. Following Step-5.Plublishing "shrjopayConfig.php" with below command.After publishing, it will be added under config folder.
   Publish config
7. Following Step-6.
   controller trans. class
8. Route
9. View
10. Following Step-7.
serve
