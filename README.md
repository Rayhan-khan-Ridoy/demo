# ![image](https://user-images.githubusercontent.com/57352037/170198396-932692aa-3354-4cf0-abc1-2b8ef43a6de3.png)

## <span style="color:green;"> <i> To integrate the shurjoPay Payment Package in your Laravel project,Please do the following seven steps sequentially.At-first make sure your device has the proper environment set-up for running PHP / Laravel project.
 </i></span>


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


### Then in your payment method you need to add below lines :-

``$request = new PaymentRequest($requestArray);
``

``$shurjopay_service = new Shurjopay();
``

``return $shurjopay_service->makePayment($request);
``

### For verifying order :-

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

# <span style="color:green;"> <i>How any user can integrate "shurjoPay" payment package ? For better understanding to users by following above steps. A sample shurjopay integration is given below for integration our package , easily : </i></span>

i) <h2 style="color:#8934eb;"> <i>First, I am going to create a laravel project to integrate shurjopay payment package named as "ShurjopayIntegration" </i></h2>
   
   ``composer create-project laravel/laravel ShurjopayIntegration
   ``
   <br>
   <br>
   Example:-
   
   ![createProject](https://user-images.githubusercontent.com/78033774/208382663-a6eb643b-ffe8-4562-8d94-cb531e9a677f.png)

ii) <h2 style="color:#8934eb;"> <i>Following, Step-1. Now, Going to change "ShurjopayIntegration" project's composer.json. </i></h2>
   <br>
   Example:-

   ![composer](https://user-images.githubusercontent.com/78033774/208382731-4346a47b-67b6-4e03-8801-0e040401dff7.png)

iii) <h2 style="color:#8934eb;"> <i>Following, Step-2. Going to termial for giving below command. </i></h2>

   ``composer update
   ``
   <br>
   <br>
   Example:-

   ![comUpdate](https://user-images.githubusercontent.com/78033774/208382865-7eab0455-b5f5-433c-824b-ee5227eb1c41.png)

iv) <h2 style="color:#8934eb;"> <i> Following, Step-3. Adding service provider in config/app.php into "providers" array. </i></h2>

   ``
   Shurjomukhi\ShurjopayLaravelPlugin\ShurjopayServiceProvider::class,
   ``
   <br>
   <br>
   Example:-

   ![appPhp](https://user-images.githubusercontent.com/78033774/208382945-8fe45cf1-7cc0-4dc8-8af9-1f1f06c0b3c8.png)

v) <h2 style="color:#8934eb;"> <i> Following, Step-4. Configuring .env file with credentials.</i></h2>
   <br>
   Example:-

   ![env](https://user-images.githubusercontent.com/78033774/208383086-36529838-b265-4cd7-945a-8cce1f300c24.png)
   
vi) <h2 style="color:#8934eb;"> <i> Following, Step-5. Plublishing "shrjopayConfig.php" with below command. After publishing, it will be added under config folder. </i></h2>
   <br>
   Example:-

   ![vendorPublish](https://user-images.githubusercontent.com/78033774/208383348-75645cd1-b4bf-4159-98a6-1e73e54464b6.png)
   <br>
   
   Checking /config folder for making sure about Is "shrjopayConfig.php" added or not ?  :
   <br>
   ![config](https://user-images.githubusercontent.com/78033774/208407401-88a45685-c1a5-400c-8d79-0e6a9aada900.png)
   <br>
    Ok. "shrjopayConfig.php" file is found under /config folder.
   Next, using some optional commands :
   <br>
   <br>
   Example:-

   ![dump](https://user-images.githubusercontent.com/78033774/208383629-6636f2ff-fa14-4479-8be9-f0609f29774b.png)
   <br>
   <br>
   Example:-

   ![clearCache](https://user-images.githubusercontent.com/78033774/208383760-94317b5a-21fa-4baa-bd1c-12e326284725.png)

vii) <h2 style="color:#8934eb;"> <i> Following, Step-6. Adding "Shurjopay" controller's namespace and also "PaymentRequest" class's namespace.
   Then creating two methods [ initialPayment() & verifyPayment() ] </i></h2>
   <br>
   Example:-

   ![controller](https://user-images.githubusercontent.com/78033774/208383848-9ec869ad-473d-4805-954f-887998a6b21f.png)

viii) <h2 style="color:#8934eb;"> <i> Defining Routes in web.php :- </i></h2>
   <br>
   Example:-
   
   ![routes](https://user-images.githubusercontent.com/78033774/208384072-38683b45-1f87-48ef-a091-3f3bdc1b2002.png)

ix) <h2 style="color:#8934eb;"> <i> Following Step-7. Going to termial for giving below commands. </i></h2>
   <br>
   Example:-
   
   ![serve](https://user-images.githubusercontent.com/78033774/208384292-b6736c75-9a4a-42c0-8d08-50bc7e2f8c38.png)

x)<h2 style="color:#8934eb;"> <i> Blade file looks like below :-  </i></h2>
   <br>
   Example:-

   ![image](https://user-images.githubusercontent.com/78033774/208404560-a9fbac89-b34e-4357-8213-ba65cfef79bf.png)



