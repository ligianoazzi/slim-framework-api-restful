# Slim Framework 3 Skeleton Application

Use this skeleton application to quickly setup and start working on a new Slim Framework 3 application. This application uses the latest Slim 3 with the PHP-View template renderer. It also uses the Monolog logger.

This skeleton application was built for Composer. This makes setting up a new Slim Framework application quick and easy.

## Install the Application

Run this command from the directory in which you want to install your new Slim Framework application.

    php composer.phar create-project slim/slim-skeleton [my-app-name]

Replace `[my-app-name]` with the desired directory name for your new application. You'll want to:

* Point your virtual host document root to your new application's `public/` directory.
* Ensure `logs/` is web writeable.

To run the application in development, you can also run this command. 

	php composer.phar start

Run this command to run the test suite

	php composer.phar test

That's it! Now go build something cool.

----------------------------------------------------------------------------

LIGIANO README

HTTP METHODS
GET     /api/v1/produto   (list)
GET     /api/v1/produto/1 (detail)
POST    /api/v1/produto   (insert)
PUT     /api/v1/produto/1 (update)
DELETE  /api/v1/produto/1 (detail)

STATUS CODE: 2xx(ok) / 3xx state updated / 4xx client error / 5xx server error

HTTP HEADERS: 
Authorization: <token>
Content-Type: application/x-www-form-urlencoded or Content-Type: application/json
Accept: application/json

REQUEST x RESPONSE = (CLIENT x server)

 - > route
 - > application receive the data
 - > application ask result by the database
 - > application ask the renderization on the format defined by developer or the negociation of content

 
------------------------- developing the application ------------------------- 
composer create-project slim/slim-skeleton --prefer-dist

CMD php -S localhost:8000 -t public (initializing the local server)

CMD composer require illuminate/database (installing Eloquent ORM)

OPEN file app/settings.php (and insert db configurations)

OPEN file app/dependencies.php (and insert db configurations)

CMD composer require robmorgan/phinx (installing database manager)

CREATE phinx.php (root)

CREATE THE MIGRATION
vendor\bin\phinx (will show the commands)
vendor\bin\phinx create UsersTable (will create the migration UsersTable) (not in fact the table yet)

OPEN THE MIGRATION AND CONFIGURE TO CREATE THE TABLE
src/db/migrations/__migration_you_want_to_configure

CREATE MODEL
app\Models\User.php (in the root folder, and mapped in composer.json and run composer dump 

    "autoload": {
        "psr-4": {
            "App\\": "app/"
        }
    },

"App" is the namespace used in the model

CREATE ROUTE
src\routes.php and call the file contains the routes
require __DIR__ . '/routes/users.php';

src\routes\users.php

IN  src\routes\users.php CREATE THE CRUD METHODS

CREATE MIDDLEWARE TO ALLOW CORS, HEADERS, METHODS
src\middleware.php

INSTALL JWT (JUST GENERATE THE TOKEN, THE VERIFICATION IS WITH OTHER PLUGIN)
composer require firebase/php-jwt

CREATE src\routes\auth.php

CALL src\routes\auth.php IN src\routes.php