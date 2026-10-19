# Routing

One of the most important service providers in your application is the App\Providers\RouteServiceProvider. This service provider loads the route files contained within your application's directory. Go ahead, crack open the code and take a look at how it works!

Once the application has been bootstrapped and all service providers have been registered, the will be handed off to the router for dispatching. The router will dispatch the request to a

route or controller, as well as run any route specific middleware.

Middleware provide a convenient mechanism for filtering or examining HTTP requests entering your application. For example, Laravel includes a middleware that verifies if the user of your application is authenticated. If the user is not authenticated, the middleware will redirect the user to the login screen. However, if the user is authenticated, the middleware will allow the request to proceed further into the application. Some middleware are assigned to all routes within the application, like those defined in the property of your HTTP kernel, while some are only assigned to specific routes or route groups. You can learn more about middleware by reading the complete middleware documentation. If the request passes through all of the matched route's