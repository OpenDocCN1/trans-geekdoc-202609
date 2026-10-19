# Attaching Rate Limiters To Routes

Rate limiters may be attached to routes or route groups using the throttle middleware. The throttle middleware accepts the name of the rate limiter you wish to assign to the route:

```
Route::middleware(['throttle:uploads'])->group(function () {
    Route::post('/audio', function () {
        //
    });

    Route::post('/video', function () {
        //
    });
});
```

# Throttling With Redis

Typically, the throttle middleware is mapped to the Illuminate\Routing\Middleware\ThrottleRequests class. This mapping is defined in your application's HTTP kernel ( App\Http\Kernel ). However, if you are using Redis as your application's cache driver, you may wish to change this mapping to use the Illuminate\Routing\Middleware\ThrottleRequestsWithRedis class. This class is more efficient at managing rate limiting using Redis: