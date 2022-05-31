# ConnectMongoDB_laravel

To begin with, install composer into your localmachine or the environment that you are using.
> Use the following command to install laravel  globally to composer.

$ composer global require laravel/installer
 
$ laravel new example-app
 
$ cd example-app
 
$ php artisan serve

> Now download MongoDB from the official website and install the setup. It is an easy step therefore does not need more cconfiguration.
> Download mongodb library and insert it in your php folder 
  Download link https://pecl.php.net/package/mongodb/1.13.0/windows it also depends on the PHP version that you are using.
  Exact the mongodb.dll and add it to your PHP8 or PHP7  folder e.g C:\php8\ext for Windows
> Add this line into your php-ini "extension=php_mongodb.dll"


> In your laravel project, go to env file and add this code

MONGO_DB_HOST=127.0.0.1
MONGO_DB_PORT=27017
MONGO_DB_DATABASE=mongocrud
MONGO_DB_USERNAME=
MONGO_DB_PASSWORD=

> Then in config >> database.php add the following code to providers

'mongodb' => [
            'driver'   => 'mongodb',
            'host'     => env('MONGO_DB_HOST', 'localhost'),
            'port'     => env('MONGO_DB_PORT', 27017),
            'database' => env('MONGO_DB_DATABASE'),
            'username' => env('MONGO_DB_USERNAME'),
            'password' => env('MONGO_DB_PASSWORD'),
            'options'  => []
        ],
  > Now install mongodb package in your project
  $ composer require jenssegers/mongodb
  
  Find the providers in config >> app.php file and register the MongodbServiceProvider.
  
  'providers' => [
        Jenssegers\Mongodb\MongodbServiceProvider::class,
           ]
  # In your user model make it look as this:
   
use Jenssegers\Mongodb\Auth\User as Authenticatable;

class User extends Authenticatable
{
   //
}
In addition, for other model use

use Jenssegers\Mongodb\Eloquent\Model;

