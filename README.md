
 <!-- 
 * This is an official documentation of integrating "shurjoPay" in laravel.
 *
 * By following steps of this documentation, any user can be able to integrate "shurjoPay" pacakge easily. 
 * In this documentation , a sample integration process is also available.
 *
 * @author Rayhan Khan Ridoy
 * @since 2022-12-01 
 -->
 

# ![image](https://user-images.githubusercontent.com/57352037/170198396-932692aa-3354-4cf0-abc1-2b8ef43a6de3.png) shurjoPay Payment Package (Laravel)
[![Test Status](https://github.com/rust-random/rand/workflows/Tests/badge.svg?event=push)]()
[![Stable](https://img.shields.io/badge/Stable-v2.1.0-green)]()
[![License](https://img.shields.io/badge/License-MIT-blue)]()
[![Rating](https://img.shields.io/badge/Rating-*****-green)]()
[![Depandency](https://img.shields.io/badge/Depandency-No-blue)]()

Official shurjoPay payment package (Laravel) for merchants or service providers to connect with shurjoPay Payment Gateway v2.1.0 developed and maintained by shurjoMukhi Limited.

This payment package can be used with any version of laravel framework.This package makes it easy for you to integrate with shurjoPay v2.1.0 with just two method calls:

- **makePayment()** - Firstly, this method  checks for authenticated user using another core method named **"authenticate()"**. After getting authenticated users, it will create and send payment request.

- **verifyPayment()** -  Verify payment status at shurjoPay.

Also reduces and provides many of the things that you had to do manually -
- Handles http request and errors
- JSON serialization and deserialization
- Authentication during checkout and verification of payments
- "``ShurjopayConfig.php``" configuration file under ``/config`` folder
- "``shurjoPay-plugin.log``" logging file under ``/storage/logs``

## Audience

This document is intended for the developers and technical personnel of merchants and service providers who want to integrate the shurjoPay online payment gateway using laravel.

# How to use shurjoPay package in laravel ?
To integrate the shurjoPay Payment Gateway in your JavaScript project do the following tasks sequentially.

#### Step-1: Install the package inside your project environment.
Open your project's "composer.json" file . Then copy below line and put it into the body of require block.

```
"shurjomukhi/shurjopay-laravel-plugin":"dev-dev" 
``` 
Example:-
`` "require" ``: {
             ```
             "shurjomukhi/shurjopay-laravel-plugin":"dev-dev"
             ```
             }

Next , Copy below block of codes and put into "composer.json" 
```
"repositories":[
                   {
                     "type": "vcs",
                     "url": "https://github.com/shurjopay-plugins/sp-plugin-laravel.git"
                   }
                  ]
```
Then , please copy below command line and run on your project's terminal. By running this command , our ``shurjoPay`` package will be loaded into your project. 

```
composer update
```

#### Step-2: Add ``ShurjopayServiceProvider``.
 
Kindly go to your project and open the ``config`` folder and then click on ``app.php`` file. Append the following line into ``providers`` array.

```
Shurjomukhi\ShurjopayLaravelPlugin\ShurjopayServiceProvider::class,
```

#### After , adding above line in ``app.php`` , Please run below commands to trigger composer and ignore cache issues.

```
composer dump-autoload
php artisan optimize:clear
```
#### Step-3: Configuration set-up for ``.env``. 
Add the following credentials in ``.env`` file with provided credentials  from shurjoMukhi Limited. If there are no existing of ``.env`` file , kindly add that file and then setup below configurations into your ``.env`` file.
```
MERCHANT_USERNAME="sp_sandbox"
MERCHANT_PASSWORD="pyyk97hu&6u6"
MERCHANT_RETURN_URL="https://sandbox.shurjopayment.com/response"
MERCHANT_CANCEL_URL="https://sandbox.shurjopayment.com/response"
ENGINE_URL="https://sandbox.shurjopayment.com"
```
#### Step-4: Add ``ShurjopayConfig.php`` by running below command.
Then, Please run below commands which will give a ``ShujopayConfig.php`` file under your ``config`` folder. Our package will take necessary ``.env`` credentials from provided ``ShurjopayConfig.php`` file. So, load will be decresed for your application with ``.env`` file and application will be run faster.

```
php artisan vendor:publish --tag=shurjopay
```
``ShujopayConfig.php`` file adds under your ``config`` folder after running above command.

#### Step-5: Controller configuration.
 Now, your application is ready to integrate shurjoPay package. Add this line of code in your method where you want to call shurjoPay Payment Gateway.

Add below lines in your controller :-
```
use Shurjomukhi\ShurjopayLaravelPlugin\Http\Controllers\Shurjopay;
use Shurjomukhi\ShurjopayLaravelPlugin\Http\Controllers\TransactionClasses\PaymentRequest;
```
First make sure you are sending an array (must be an instance of "PaymentRequest" class). Which belongs below fields for making payment request by your method -
```
'currency','amount','order_id','discount_amount','disc_percent','client_ip','customer_name','customer_phone','customer_email','customer_address','customer_city','customer_state','customer_postcode','customer_country','shipping_address','shipping_city','shipping_country','received_person_name','shipping_phone_number'
```
#### Then in your payment method you need to add below lines :-
```
$request = new PaymentRequest($requestArray);
$shurjopay_service = new Shurjopay();
return $shurjopay_service->makePayment($request);
```
#### For verifying order :-
```
$shurjopay_instance = new Shurjopay();
return $shurjopay_instance->verifyPayment($order_id);
```
#### Step-6: Ready to run.
Now application is ready to work. Just give another command in terminal
```
php artisan serve
```
#### License
This code is under the [MIT open source License](http://www.opensource.org/licenses/mit-license.php).
#### Sample Integration
 Please see our [sample integration](https://github.com/shurjopay-plugins/sp-plugin-usage-examples/tree/dev/laravel-app-laravel-plugin/shurjopay_integ_usage_project_new) project which will give you some idea and help you to integrate our package !
#### Who do I talk to? 
For any technical assistance please [contact](https://shurjopay.com.bd/#contacts) now.
