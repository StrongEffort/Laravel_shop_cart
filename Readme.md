<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

## This is a Laravel + Vue.js e-commerce template that will make it easy for you to start your own online store.


There is the [DEMO](https://lara-shop.westeurope.cloudapp.azure.com/) ULE-shop.

[Video presentation](https://youtu.be/McmVr2FEo-0)

<p><img src="https://preview.ibb.co/dyyGMb/sshot_shop.png" alt="sshot_shop" border="0"></p>

1. Setup docker and docker-compose on your local machine.
2. Create the .local_data folder in the root directory of the project
3. Install git. Fetch this project from Github (git clone).
4. Copy ".env.example" file and rename to ".env". Edit the .env file (connect to DB).
5. Run "docker-compose up" (you may need to restart docker-compose up 3-4 times).

It uses roadrunner, Laravel/Octane and temporal.
If you prefer more traditional nginx/php server, checkout to the version 0.01 please.

### Local endpoints:
- localhost  -- Main App
- localhost:8088 -- [Temporal](https://temporal.io) UI 

HTTPS locally
```
mkdir ssl && cd ssl && mkcert -install
```

Populate database
```
docker-compose exec roadrunner /bin/bash
composer install
php artisan migrate
php artisan db:seed --class=DatabaseSeeder
```

To reset roadrunner server execute
```
docker-compose exec roadrunner rr -c /etc/.rr.yaml reset
```
To observe roadrunner workers execute
```
docker-compose exec roadrunner rr -c /etc/.rr.yaml workers -i
```

How to use [xdebug with roadrunner](https://roadrunner.dev/docs/php-debugging/2023.x/en)
. Set in the rr settings: pool.num_workers: 1, pool.debug: false.
If you have any active XDebug listener while starting RoadRunner with XDebug enabled — disable it. This will prevent false-positive debug session.
Start server, enable listener and run:
``docker-compose exec roadrunner rr -c /etc/.rr.yaml reset http``

_Uladzimir Sadkou_: oscaraksoy@outlook.com
