# screenshotmachine-php

This demo shows how to call online screenshot machine API using PHP.

## Installation

a) using Composer - package manager for PHP
```php
php composer.phar require screenshotmachine/screenshotmachine-php
```
b) or download source code directly from GitHub.com

First, you need to create a free/premium account at [www.screenshotmachine.com](https://www.screenshotmachine.com) website. After registration, you will see your customer key in your user profile. Also secret phrase is maintained here. Please, use secret phrase always, when your API calls are called from publicly available websites.  

Set-up your customer key and secret phrase (if needed) in the script:

```php
$customer_key = "PUT_YOUR_CUSTOMER_KEY_HERE";
$secret_phrase = ""; //leave secret phrase empty, if not needed
```

Set other options to fulfill your needs: 

```php
//mandatory parameter
$options['url'] = "https://www.google.com";

// all next parameters are optional, see our API guide for more details
$options['dimension'] = "1366x768";  // or "1366xfull" for full length screenshot
$options['device'] = "desktop";
$options['format'] = "png";
$options['cacheLimit'] = "0";
$options['delay'] = "200";
```
More info about options can be found in our [API guide](https://www.screenshotmachine.com/apiguide.php).  

 Sample code
-----

```php
<?php
$customer_key = "PUT_YOUR_CUSTOMER_KEY_HERE";
$secret_phrase = ""; //leave secret phrase empty, if not needed

$machine = new ScreenshotMachine($customer_key, $secret_phrase);

//mandatory parameter
$options['url'] = "https://www.google.com";

// all next parameters are optional, see our API guide for more details
$options['dimension'] = "1366x768";  // or "1366xfull" for full length screenshot
$options['device'] = "desktop";
$options['format'] = "png";
$options['cacheLimit'] = "0";
$options['delay'] = "200";

$api_url = $machine->generate_api_url($options);

//put link to your html code
echo '<img src="' . $api_url . '">' . PHP_EOL; 
```
Generated ```api_url```  link can be placed in ```<img>``` tag or used in your business logic later.

If you need to store captured screenshot as an image, just call:

```php
<?php
$customer_key = "PUT_YOUR_CUSTOMER_KEY_HERE";
$secret_phrase = ""; //leave secret phrase empty, if not needed

$machine = new ScreenshotMachine($customer_key, $secret_phrase);

//mandatory parameter
$options['url'] = "https://www.google.com";

// all next parameters are optional, see our API guide for more details
$options['dimension'] = "1366x768";  // or "1366xfull" for full length screenshot
$options['device'] = "desktop";
$options['format'] = "png";
$options['cacheLimit'] = "0";
$options['delay'] = "200";

$api_url = $machine->generate_api_url($options);

//or save screenshot as an image
$output_file = 'output.png';
file_put_contents($output_file, file_get_contents($api_url));
echo 'Screenshot saved as ' . $output_file . PHP_EOL;
```

Captured screenshot will be saved as ```output.png``` file in current directory.

# License

The MIT License (MIT)    