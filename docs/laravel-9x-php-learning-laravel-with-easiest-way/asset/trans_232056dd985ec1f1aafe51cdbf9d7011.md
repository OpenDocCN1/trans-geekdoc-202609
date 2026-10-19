

```bash
php artisan breeze:install api

php artisan migrate
```

在安装过程中，Breeze 会在你的应用 `.env` 文件中添加一个 `FRONTEND_URL` 环境变量。这个 URL 应该是你的 JavaScript 应用的地址。在本地开发时，通常是 `http://localhost:3000`。此外，你应确保 `APP_URL` 设置为 `http://localhost:8000`，这是 `serve` Artisan 命令使用的默认 URL。

## Next.js 参考实现

最后，你可以将此后端与你选择的前端配对。Breeze 前端的 Next 参考实现可在 GitHub 上获取。该前端由 Laravel 维护，包含与 Breeze 提供的传统 Blade 和 Inertia 技术栈相同的用户界面。

## Laravel Jetstream

尽管 Laravel Breeze 为构建 Laravel 应用程序提供了一个简单且最小的起点，但 Jetstream 通过更强大的功能和额外的前端技术栈增强了该功能。对于刚接触 Laravel 的开发者，我们建议先通过 Laravel Breeze 学习基础知识，然后再升级到 Laravel Jetstream。Jetstream 为 Laravel 提供了设计精美的应用程序脚手架，包括登录、注册、电子邮件验证、双因素认证、会话管理、通过 Laravel Sanctum 提供的 API 支持，以及可选的团队管理。Jetstream 使用 Tailwind CSS 设计，并为你提供基于 Livewire 或 Inertia.js 驱动的前端脚手架。有关安装 Laravel Jetstream 的完整文档，可以在官方 Jetstream 文档中找到。

当配置被缓存时，`.env` 文件将不会被加载，所有针对 `.env` 变量的 `env` 函数调用都将返回 `null`。

## 优化路由加载

```bash
php artisan route:cache
```

该命令会将你所有的路由注册减少为缓存文件中的一次方法调用，从而在注册数百条路由时提高路由注册的性能。

## 优化视图加载

```bash
php artisan view:cache
```

该命令会预编译所有 Blade 视图，使它们不会被按需编译，从而提高每个返回视图的请求的性能。

## 调试模式

如果你想要一个完全无服务器、自动扩展且为 Laravel 调优的部署平台，请查看 Laravel Vapor。Laravel Vapor 是一个由 AWS 驱动的 Laravel 无服务器部署平台。在 Vapor 上启动你的 Laravel 基础设施，并爱上无服务器的可扩展简洁性。Laravel Vapor 由 Laravel 的创造者校准，确保与框架完美配合，因此你可以继续像往常一样构建你的 Laravel 应用程序。

## 请求生命周期

- 简介
- 生命周期概述
  - 第一步
  - HTTP / 控制台内核
  - 服务提供者
  - 路由
  - 收尾
- 专注于服务提供者

## 简介

在“现实世界”中使用任何工具时，如果你了解该工具的工作原理，你会更有信心。应用程序开发也不例外。当你了解开发工具如何运作时，你会更舒适、更有信心地使用它们。本文档的目标是让你对 Laravel 框架的工作原理有一个很好的高层概述。通过更好地了解整个框架，一切都会变得不那么“神奇”，你会更有信心构建你的应用程序。如果你不能马上理解所有术语，请不要灰心！只需试着基本掌握正在发生的事情，随着你探索文档的其他部分，你的知识会不断增长。

## 生命周期概述

### 第一步

所有请求进入 Laravel 应用程序的入口点是 `public/index.php` 文件。所有请求都由你的 Web 服务器（Apache / Nginx）配置指向该文件。`index.php` 文件包含的代码不多。相反，它是加载框架其余部分的起点。

`index.php` 文件加载 Composer 生成的自动加载器定义，然后从 `bootstrap/app.php` 获取 Laravel 应用程序实例。Laravel 自己做的第一件事是创建应用程序/服务容器的实例。

### HTTP / 控制台内核

### 路由

你的应用程序中最重要的服务提供者之一是 `App\Providers\RouteServiceProvider`。这个服务提供者加载应用程序目录中包含的路由文件。来吧，打开代码看看它是如何工作的！

一旦应用程序已经引导并且所有服务提供者都已注册，请求将被交给路由器进行分发。路由器会将请求分发到路由或控制器，并运行任何特定于路由的中间件。

中间件提供了一种方便的机制来过滤或检查进入你的应用程序的 HTTP 请求。例如，Laravel 包含一个中间件，用于验证你的应用程序用户是否已认证。如果用户未通过认证，中间件会将用户重定向到登录界面。然而，如果用户已认证，中间件将允许请求进一步进行到应用程序中。一些中间件被分配给应用程序中的所有路由，比如那些在你的 HTTP 内核属性中定义的中间件，而另一些则仅分配给特定的路由或路由组。你可以通过阅读完整的中间件文档来了解更多关于中间件的信息。如果请求通过了所有匹配路由的

服务提供者存储在 `app/Providers` 目录中。默认情况下，`AppServiceProvider` 相当空。这个提供者是一个很好的地方，可以添加你自己的引导和服务容器绑定。对于大型应用程序，你可能希望创建多个服务提供者，每个服务提供者为你的应用程序使用的特定服务提供更细粒度的引导。

## 服务容器

### 简介

- 零配置解析
- 何时使用容器

### 绑定

- 绑定基础
- 将接口绑定到实现
- 上下文绑定
- 绑定原始值
- 绑定类型化可变参数
- 标签
- 扩展绑定

### 解析

- 使用 Make 方法

```php
<?php

namespace App\Http\Controllers;

use App\Http\Controllers\Controller;
use App\Repositories\UserRepository;
use App\Models\User;

class UserController extends Controller
{
    /**
     * The user repository implementation.
     *
     * @var UserRepository
     */
    protected $users;

    /**
     * Create a new controller instance.
     *
     * @param UserRepository $users
     * @return void
     */
    public function __construct(UserRepository $users)
    {
        $this->users = $users;
    }

    /**
     * Show the profile for the given user.
     *
     * @param int $id
     * @return Response
     */
    public function show($id)
    {
        $user = $this->users->find($id);

        return view('user.profile', ['user' => $user]);
    }
}
```

在这个例子中，`UserController` 需要从数据源中检索用户。因此，我们将注入一个能够检索用户的服务。在这种情况下，我们的 `UserRepository` 很可能使用 Eloquent 从数据库中检索用户信息。然而，由于仓库是被注入的，我们可以轻松地用另一个实现替换它。在测试应用程序时，我们还可以轻松地“模拟”或创建 `UserRepository` 的虚拟实现。

深入了解 Laravel 服务容器对于构建强大、大型的应用程序以及为 Laravel 核心本身做出贡献至关重要。

### 零配置解析

如果一个类没有依赖，或者只依赖于其他具体类（而不是接口），容器不需要被指示如何解析该类。例如，你可以将以下代码放在你的 `routes/web.php` 文件中：

