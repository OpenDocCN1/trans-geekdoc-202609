
```php
<?php

namespace App\Http\Middleware;

use Closure;

class EnsureTokenIsValid
{
    /**
     * Handle an incoming request.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  \Closure  $next
     * @return mixed
     */
    public function handle($request, Closure $next)
    {
        if ($request->input('token') !== 'my-secret-token') {
            return redirect('home');
        }

        return $next($request);
    }
}
```

正如你所见，如果给定的令牌与我们的 secret token 不匹配，中间件将向客户端返回一个 HTTP 重定向；否则，请求将被传递到应用程序的更深处。要将请求传递到应用程序的更深处（允许中间件“放行”），你应该使用 $request 调用 $next 回调。最好将中间件想象成一系列“层”，HTTP 请求必须穿过这些层才能到达你的应用程序。每一层都可以检查请求，甚至完全拒绝它。

> {tip} 所有中间件都通过服务容器解析，因此你可以在中间件的构造函数中为所需的任何依赖项进行类型提示。

## 中间件与响应

当然，中间件可以在将请求传递到应用程序的更深处之前或之后执行任务。例如，以下中间件将在请求由应用程序处理之前执行某些任务：

```php
\Illuminate\Routing\Middleware\SubstituteBindings::class,
\Illuminate\Auth\Middleware\Authorize::class,
];
```

## 中间件参数

中间件还可以接收额外的参数。例如，如果你的应用程序需要在执行某个操作之前验证已认证用户是否具有给定的“角色”，你可以创建一个 EnsureUserHasRole 中间件，使其接收角色名称作为额外参数。

额外的中间件参数将在 $next 参数之后传递给中间件：

app/Http/Kernel.php 文件。当在中间件上调用 terminate 方法时，Laravel 将从服务容器解析中间件的新实例。如果你希望在调用 handle 和 terminate 方法时使用同一个中间件实例，请使用容器的 singleton 方法将中间件注册到容器中。通常这应该在你的 AppServiceProvider 的 register 方法中完成：

```php
use App\Http\Middleware\TerminatingMiddleware;

/**
 * Register any application services.
 *
 * @return void
 */
public function register()
{
    $this->app->singleton(TerminatingMiddleware::class);
}
```

email 输入字段用于包含用户希望开始使用的电子邮件地址。如果没有 CSRF 保护，恶意网站可以创建一个指向你应用程序 /user/email 路由的 HTML 表单并提交恶意用户自己的电子邮件地址：

```html
<form action="https://your-application.com/user/email" method="POST">
    <input type="email" value="malicious-email@example.com">
</form>

<script>
    document.forms[0].submit();
</script>
```

如果恶意网站在页面加载时自动提交表单，恶意用户只需诱骗你应用程序的某个毫无防备的用户访问其网站，其电子邮件地址就会在你的应用程序中被更改。

为了防止此漏洞，我们需要检查每个传入的 POST、PUT、PATCH 或 DELETE 请求，以查找恶意应用程序无法访问的 secret 会话值。

## 防止 CSRF 请求

Laravel 会为应用程序管理的每个活动用户会话自动生成一个 CSRF “token”。此令牌用于验证已认证用户确实是向应用程序发出请求的人。由于此令牌存储在用户的会话中，并且在会话每次重新生成时都会更改，恶意应用程序无法访问它。当前会话的 CSRF 令牌可以通过请求的会话或通过 csrf_token 辅助函数访问：

```php
use Illuminate\Http\Request;

Route::get('/token', function (Request $request) {
    $token = $request->session()->token();
    
    $token = csrf_token();
    
    // ...
});
```

只要你在应用程序中定义“POST”、“PUT”、“PATCH”或“DELETE” HTML 表单，你都应该在表单中包含一个隐藏的 CSRF _token 字段，以便 CSRF 保护中间件可以验证请求。为了方便，你可以使用 @csrf Blade 指令生成隐藏的令牌输入字段：

```html
<form method="POST" action="/profile">
    @csrf

    <!-- Equivalent to... -->
    <input type="hidden" name="_token" value="{{ csrf_token() }}" />
</form>
```

App\Http\Middleware\VerifyCsrfToken 中间件默认包含在 web 中间件组中，将自动验证请求输入中的令牌是否与存储在会话中的令牌匹配。当这两个令牌匹配时，我们就知道已认证用户是发起请求的人。

## CSRF 令牌与 SPA

如果你正在构建一个使用 Laravel 作为 API 后端的 SPA，你应该查阅 Laravel Sanctum 文档，了解有关使用 API 进行身份验证以及防止 CSRF 漏洞的信息。

## 从 CSRF 保护中排除 URI

有时你可能希望从 CSRF 保护中排除一组 URI。

例如，如果你使用 Stripe 处理付款并使用其 webhook 系统，你需要将 Stripe webhook 处理程序路由从 CSRF 保护中排除，因为 Stripe 不会知道向你的路由发送什么 CSRF 令牌。

通常，你应该将这类路由放在 App\Providers\RouteServiceProvider 应用于 routes/web.php 文件中所有路由的 web 中间件组之外。

然而，你也可以通过将它们的 URI 添加到 VerifyCsrfToken 中间件的 $except 属性来排除这些路由：

```php
<?php

namespace App\Http\Middleware;

use Illuminate\Foundation\Http\Middleware\VerifyCsrfToken as Middleware;

class VerifyCsrfToken extends Middleware
{
    /**
     * The URIs that should be excluded from CSRF verification.
     *
     * @var array
     */
    protected $except = [
        'stripe/*',
        'http://example.com/foo/bar',
        'http://example.com/foo/*',
    ];
}
```

> {tip} 为了方便，在运行测试时，CSRF 中间件会自动为所有路由禁用。

## X-CSRF-TOKEN

除了将 CSRF 令牌作为 POST 参数进行检查外，App\Http\Middleware\VerifyCsrfToken 中间件还会检查 X-CSRF-TOKEN 请求头。例如，你可以将令牌存储在 HTML meta 标签中

```html
<meta name="csrf-token" content="{{ csrf_token() }}">
```

然后，你可以指示像 jQuery 这样的库自动将令牌添加到所有请求头中。

这为使用传统 JavaScript 技术构建的基于 AJAX 的应用程序提供了简单便捷的 CSRF 保护：

```js
$.ajaxSetup({
    headers: {
        'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
    }
});
```

## X-XSRF-TOKEN

Laravel 将正在进行的 CSRF 令牌存储在框架创建的每个响应中都包含的编码 XSRF-TOKEN cookie 中。你可以使用 cookie 的值来设置 X-XSRF-TOKEN 请求头。

此 cookie 主要作为开发人员便利而发送，因为某些 JavaScript 框架和库（如 Angular 和 Axios）会在同源请求上自动将其值放在 X-XSRF-TOKEN 头中。

> {tip} 默认情况下，resources/js/bootstrap.js 文件包含 Axios HTTP 库，它会自动为你发送 X-XSRF-TOKEN 头。
