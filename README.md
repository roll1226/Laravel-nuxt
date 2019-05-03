# Docker for Laravel + nuxt

## Docker run

```
$ docker-compose up -d --build
```


## 設定変更
```
$ docker-compose exec nuxt yarn

$ docker-compose exec app composer require barryvdh/laravel-cors

$ vim /app/Http/Kernel.php
~~~~
protected $middlewareGroups = [
    'web' => [
        \App\Http\Middleware\EncryptCookies::class,
        \Illuminate\Cookie\Middleware\AddQueuedCookiesToResponse::class,
        \Illuminate\Session\Middleware\StartSession::class,
        // \Illuminate\Session\Middleware\AuthenticateSession::class,
        \Illuminate\View\Middleware\ShareErrorsFromSession::class,
        \App\Http\Middleware\VerifyCsrfToken::class,
        \Illuminate\Routing\Middleware\SubstituteBindings::class,
    ],

    'api' => [
        'throttle:60,1',
        'bindings',
    +++     \Barryvdh\Cors\HandleCors::class,
    ],
];
~~~~
$  docker-compose exec app php artisan vendor:publish --provider="Barryvdh\Cors\ServiceProvider"
```
