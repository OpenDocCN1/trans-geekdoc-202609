
在自动注入其依赖的同时调用闭包：

```php
use App\Repositories\UserRepository;
use Illuminate\Support\Facades\App;

$result = App::call(function (UserRepository $repository) {
    // ...
});
```

## 容器事件

服务容器在每次解析对象时都会触发一个事件。您可以使用 resolving 方法监听此事件：

```php
use App\Services\Transistor;

$this->app->resolving(Transistor::class, function ($transistor, $app) {
    // Called when container resolves objects of type "Transistor"...
});

$this->app->resolving(function ($object, $app) {
    // Called when container resolves object of any type...
});
```

如您所见，被解析的对象将被传递给回调，从而允许您在对象交付给其使用者之前设置任何附加属性。

## 编写服务提供者

所有服务提供者都扩展 Illuminate\Support\ServiceProvider 类。

大多数服务提供者包含 register 和 boot 方法。在 register 方法中，您应该只将事物绑定到服务容器中。您绝不应尝试在 register 方法中注册任何事件监听器、路由或任何其他功能。

Artisan CLI 可以通过 make:provider 命令生成新的提供者：

```
php artisan make:provider RiakServiceProvider
```

## Register 方法

如前所述，在 register 方法中，您应该只将事物绑定到服务容器中。您绝不应尝试在 register 方法中注册任何事件监听器、路由或任何其他功能。否则，您可能会意外使用尚未加载的服务提供者提供的服务。让我们看一个基本的服务提供者。在您的任何服务提供者方法中，您始终可以访问 $app 属性，它提供了对服务容器的访问：

```php
<?php

namespace App\Providers;

use App\Services\Riak\Connection;
use Illuminate\Support\ServiceProvider;

class RiakServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     *
     * @return void
     */
    public function register()
    {
        $this->app->singleton(Connection::class, function ($app) {
            return new Connection(config('riak'));
        });
    }
}
```

此服务提供者仅定义了 register 方法，并使用该方法在服务容器中定义 App\Services\Riak\Connection 的实现。如果您尚未熟悉 Laravel 的服务容器，请查看其文档。

## bindings 和 singletons 属性

如果您的服务提供者注册了许多简单的绑定，您可能希望使用 bindings 和 singletons 属性，而不是手动注册每个容器绑定。当框架加载服务提供者时，它会自动检查这些属性并注册其绑定：

```php
<?php

namespace App\Providers;

use App\Contracts\DowntimeNotifier;
use App\Contracts\ServerProvider;
use App\Services\DigitalOceanServerProvider;
use App\Services\PingdomDowntimeNotifier;
use App\Services\ServerToolsProvider;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    /**
     * All of the container bindings that should be registered.
     *
     * @var array
     */
    public $bindings = [
        ServerProvider::class => DigitalOceanServerProvider::class,
    ];

    /**
```

```php
<?php

namespace App\Providers;

use Illuminate\Support\Facades\View;
use Illuminate\Support\ServiceProvider;

class ComposerServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        View::composer('view', function () {
            //
        });
    }
}
```

## Boot 方法依赖注入

您可以在服务提供者的 boot 方法中为依赖项添加类型提示。服务容器将自动注入您需要的任何依赖项：

view、response、url、config 等。Laravel 提供的每个辅助函数都与其对应功能一起记录；不过，完整列表可在专门的辅助函数文档中找到。例如，与使用 Illuminate\Support\Facades\Response 门面生成 JSON 响应相比，我们可以简单地使用 response 函数。由于辅助函数是全局可用的，因此您无需导入任何类即可使用它们：

```php
use Illuminate\Support\Facades\Response;

Route::get('/users', function () {
    return Response::json([
        // ...
    ]);
});

Route::get('/users', function () {
    return response()->json([
        // ...
    ]);
});
```

## 何时使用门面

门面有很多好处。它们提供简洁、易记的语法，让您无需记住必须手动注入或配置的长类名即可使用 Laravel 的功能。此外，由于其对 PHP 动态方法的独特使用，它们易于测试。然而，使用门面时必须谨慎。门面的主要危险是类的“范围蔓延”。由于门面易于使用且不需要注入，很容易让您的类不断增长并在单个类中使用许多门面。使用依赖注入，这种可能性通过大型构造函数给出的视觉反馈得到缓解，表明您的类增长过大。因此，使用门面时，请特别注意类的大小，以保持其职责范围狭窄。如果您的类变得过大，请考虑将其拆分为多个较小的类。

## 门面与依赖注入

依赖注入的主要好处之一是可以交换注入类的实现。这在测试期间很有用，因为您可以注入 mock 或 stub 并断言 stub 上的各种方法已被调用。通常，不可能模拟或 stub 真正的静态类方法。然而，由于门面使用动态方法将方法调用代理到从服务容器解析的对象，我们实际上可以像测试注入的类实例一样测试门面。例如，给定以下路由：

```php
use Illuminate\Support\Facades\Cache;

Route::get('/cache', function () {
    return Cache::get('key');
});
```

使用 Laravel 的门面测试方法，我们可以编写以下测试来验证 Cache::get 方法是否使用我们期望的参数被调用：

```php
use Illuminate\Support\Facades\Cache;

/**
 * A basic functional test example.
 *
 */
```

```php
return Illuminate\Support\Facades\View::make('profile');

return view('profile');
```

门面和辅助函数之间绝对没有任何实际区别。使用辅助函数时，您仍然可以像测试相应的门面一样对其进行测试。例如，给定以下路由：

```php
Route::get('/cache', function () {
    return cache('key');
});
```

在内部，cache 辅助函数将调用 Cache 门面底层类的 get 方法。因此，即使我们使用的是辅助函数，我们也可以编写以下测试来验证方法是否使用我们期望的参数被调用：

```php
use Illuminate\Support\Facades\Cache;

/**
 * A basic functional test example.
 *
 * @return void
 */
public function testBasicExample()
{
    Cache::shouldReceive('get')
        ->with('key')
        ->andReturn('value');

    $response = $this->get('/cache');

    $response->assertSee('value');
}
```

## 门面如何工作

在 Laravel 应用程序中，门面是一个提供对容器中对象的访问的类。使这项工作得以实现的机制在 Facade 类中。Laravel 的门面以及您创建的任何自定义门面都将扩展
