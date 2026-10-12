
## Blade 注册表单模板

```html
<label for="name" class="col-md-12 control-label">Name</label>

<div class="col-md-12">
    <input id="name" type="text" class="form-control" name="name" value="{{ old('name') }}" required autofocus>
    @if ($errors->has('name'))
        <span class="help-block">
            <strong>{{ $errors->first('name') }}</strong>
        </span>
    @endif
</div>

<div class="form-group{{ $errors->has('email') ? ' has-error' : '' }}">
    <label for="email" class="col-md-4 control-label">E-Mail Address</label>
    <div class="col-md-12">
        <input id="email" type="email" class="form-control" name="email" value="{{ old('email') }}" required>
        @if ($errors->has('email'))
            <span class="help-block">
                <strong>{{ $errors->first('email') }}</strong>
            </span>
        @endif
    </div>
</div>

<div class="form-group{{ $errors->has('password') ? ' has-error' : '' }}">
    <label for="password" class="col-md-4 control-label">Password</label>
    <div class="col-md-12">
        <input id="password" type="password" class="form-control" name="password" required>
        @if ($errors->has('password'))
            <span class="help-block">
                <strong>{{ $errors->first('password') }}</strong>
            </span>
        @endif
    </div>
</div>

<div class="form-group">
    <label for="password-confirm" class="col-md-12 control-label">Confirm Password</label>
    <div class="col-md-12">
        <input id="password-confirm" type="password" class="form-control" name="password_confirmation" required>
    </div>
</div>

<div class="form-group">
    <div class="col-md-12 col-md-offset-4">
        <button type="submit" class="btn btn-primary">
            Register
        </button>
        <span class="ml-3">Already have an account?</span>
        <a id="login" class="btn btn-link d-inline pl-0" href="{{ route('login') }}">
            Login
        </a>
    </div>
</div>
```

```blade
@endsection

@section('styles')
<style type="text/css">
    #login {
        position: relative;
        bottom: 2.5px;
    }
</style>
@endsection
```

## 设置应用路由与控制器

现在我们需要设置应用路由（位于 `routes/web.php`）并创建一个名为 `AppController.php` 的控制器。在终端或 Git Bash 中运行：

```bash
php artisan make:controller AppController
```

`AppController` 类将在 `app/Http/Controllers` 目录下生成。Laravel 允许你为控制器定义路由（基本上就是 URL），控制器随后渲染视图或返回数据——这些数据可能来自数据库，也可能不是；可能经过处理，也可能没有——并将其传递给视图（`.blade` 文件）进行渲染，或作为 JSON 数据端点返回。稍后你就会明白这一切。

找到 `routes/web.php`，Laravel 允许我们在其中定义 Web 路由，将其全部内容替换为以下代码：

```php
<?php

Auth::routes();

Route::get('/', function () {
    return redirect()->route('inventory.home');
});

Route::group(['prefix' => 'app', 'middleware' => 'auth'], function ($route) {
    $route->get('/', 'AppController@dashboard')->name('inventory.home');
});
```

### 路由分组说明

这里我们定义了一个路由组。Laravel 允许定义路由组，以便将相同的 URL 前缀、中间件及其他选项应用到组内的所有路由。在本例中，我们应用了前缀 `app` 和中间件 `auth`。该组内的所有 URL 都以 `/app` 开头，`auth` 中间件会阻止未登录用户访问组内的任何路由。同时注意 `name` 方法允许我们给路由起一个易于记忆的别名，这里我们将渲染仪表盘的路由命名为 `inventory.home`，并在用户访问浏览器中的 `/` 路由时通过重定向引用了它。

> **Note**
>
> 中间件为过滤进入应用的 HTTP 请求提供了便捷机制。Laravel 的 `auth` 中间件验证应用用户是否已登录。如果未登录，用户将被重定向到登录页面；如果已登录，中间件将允许请求继续深入应用内部。Laravel 自带了[多种中间件](https://laravel.com/docs/5.8/middleware)，你也可以自行创建额外的中间件。

Laravel 允许根据请求类型定义路由，包括 `get`、`post`、`put`、`delete` 和 `any` 等请求方法。查看页面适用 `get` 路由，提交表单适用 `post` 路由，更新表单适用 `put` 路由，删除数据库记录则适用 `delete` 路由。如果你是初学者这可能看起来很陌生，但其实这些只是 HTTP 动词。

以我们的 `/app` URL 定义为例，我们定义了一个 `get` 请求类型。当用户访问该 URL 时，会调用 `AppController` 中的 `dashboard` 方法。

```php
$route->get('/', 'AppController@dashboard')->name('inventory.home');
```

另一个案例是定义 Laravel 路由的基本形式：传递一个闭包，可以返回视图、数据或重定向响应。在本例中，我们返回了一个重定向到应用仪表盘的响应。

```php
Route::get('/', function () {
    return redirect()->route('inventory.home');
});
```

### 添加控制器方法

接下来打开 `AppController`，在 `AppController` 类中添加 `dashboard` 方法：

```php
public function dashboard()
{
    return view('dashboard');
}
```

现在如果你访问 `http://127.0.0.1:8000/app`，未认证用户会被重定向回登录页，因为我们的仪表盘路由受 `auth` 中间件保护。

在编辑器中打开以下两个文件：`Http/Controllers/Auth/LoginController.php` 和 `Http/Controllers/Auth/RegisterController.php`，将重定向 URL 属性从 `/home` 改为 `/app`，因为不再定义 `/home` 路由。

你的文件应更新为如下所示：

```php
protected $redirectTo = '/app';
```

## Hello Laravel Migrations, Goodbye to Labouring
