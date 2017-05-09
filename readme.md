# LARAVEL ROUTE::CONTROLLER SUPPORT

This repo is just a simple add-back of the Route::controller code found in 5.2. It extends the newest Router code and re-implements the controller functionality that was removed from 5.2, 5.3, 5.4, etc.

I too found the Route::controller method to be extremely helpful, clean and understandable. I simply do not agree with the removal of this functionality.

## Easy Installtion

    composer require shrimpwagon/laravel-route-controller

Modify app/Providers/RouteServiceProvider.php

Change:

    use Illuminate\Routing\Router;

To:

    use Shrimpwagon\Laravel\Router;

And add this method:

    protected function registerRouter()
    {
        $this->app['router'] = $this->app->share(function ($app) {
            return new Router($app['events'], $app);
        });
    }