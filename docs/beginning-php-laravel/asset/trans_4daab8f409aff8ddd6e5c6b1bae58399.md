
# 简单侧边栏

菜单的初始状态在较小屏幕上将显示为折叠状态，在较大屏幕上将显示为非折叠状态。当使用下方按钮切换时，菜单将发生变化。

请确保将所有页面内容保留在 `#page-content-wrapper` 内部。顶部导航栏是可选的，仅用于演示。只需创建一个具有 `#menu-toggle` ID 的元素，点击时即可切换菜单。

现在在浏览器中重新加载页面，一切应能正常加载，且浏览器标签页的页面标题已更改为 Welcome。

尝试调整布局，试着让 `master.blade.php` 比现在更精简，或定义一个 yield 指令以向 head 标签插入额外样式或向 footer 标签插入脚本。

# 认证

在本章中，我们将为库存应用构建注册和登录系统。Laravel 已开箱即用地提供了一切所需功能，你无需维护会话，随时可以在 `config/auth.php` 配置 Laravel 认证。

使用 artisan 命令行界面，Laravel 允许我们通过在库存项目根目录下的终端或 git bash 中运行命令来生成认证脚手架。

```
php artisan make:auth
```

成功运行命令后，你将收到一条提示“Authentication scaffolding generated successfully”的消息。为确认这一点，请访问 `http://127.0.0.1:8000/login` 和 `http://127.0.0.1:8000/register`，你会发现一个可用的登录页和注册页已为我们自动生成，这不是很棒吗？

在编辑器中，于 `views/auth` 目录下你会注意到注册、登录和忘记密码的新 blade 文件，同时在 `Http/Controllers` 下你将看到一个新生成的 `HomeController.php` 类。

> **注意**
>
> Artisan 是 Laravel 自带的命令行界面。它提供了许多有用的命令，可在构建应用程序时为你提供帮助。要查看所有可用的 Artisan 命令列表，可以使用 list 命令：

```
php artisan list
```

## 登录页

让我们编辑登录页以扩展我们自己的主模板。对于登录视图，我们不需要侧边导航、导航栏，且需要将登录表单居中显示在页面中间。以下是登录页代码的最终效果。

```php
// resources/views/auth/login.blade.php

@extends('layout.master')

@section('sidenav')
    {{--//--}}
@endsection

@section('navbar')
    {{--//--}}
@endsection

@section('content')
    <div class="row">
        <div class="col-md-4 mx-auto mt-5 border">
            <div class="panel panel-default">
                <div class="panel-heading text-center pt-4">
                    <h4>登录</h4>
                </div>
                <div class="panel-body">
                    <form class="form-horizontal" method="POST" action="{{ route('login') }}">
                        {{ csrf_field() }}
                        <div class="form-group{{ $errors->has('email') ? ' has-error' : '' }}">
                            <label for="email" class="col-md-4 control-label">电子邮箱地址</label>
                            <div class="col-md-12">
                                <input id="email" type="email" class="form-control" name="email" value="{{ old('email') }}" required autofocus>
                                @if ($errors->has('email'))
                                    <span class="help-block">
                                        <strong>{{ $errors->first('email') }}</strong>
                                    </span>
                                @endif
                            </div>
                        </div>
                        <div class="form-group{{ $errors->has('password') ? ' has-error' : '' }}">
                            <label for="password" class="col-md-4 control-label">密码</label>
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
                            <div class="ml-3">
                                <div class="checkbox">
                                    <label>
                                        <input type="checkbox" name="remember" {{ old('remember') ? 'checked' : '' }}> 记住我
                                    </label>
                                </div>
                            </div>
                        </div>
                        <div class="form-group">
                            <div class="col-md-12">
                                <button type="submit" class="btn btn-primary">登录</button>
                                <a class="btn btn-link d-inline" href="{{ route('register') }}">注册</a>
                                <a class="btn btn-link d-inline" href="{{ route('password.request') }}">忘记密码？</a>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
@endsection
```

复制上述代码并粘贴到你的 `resources/views/auth/login.blade.php` 文件中，保存并刷新登录页。现在你应该能看到区别了！看起来更好了，不是吗？

注意我们在侧边栏和导航栏区块之间添加空注释的方式，以此覆盖它们，使登录页上这两部分均不显示任何内容。

如下所示：

```php
@section('sidenav')
    {{--//--}}
@endsection

@section('navbar')
    {{--//--}}
@endsection
```

## 注册页

让我们也编辑注册页，使其扩展我们自己的主布局，而非自动生成的脚手架布局。

对于注册页，我们将使用额外的 CSS 将链接回登录页的锚标签位置稍微上移。一种更整洁的方法是在主布局中添加一个 `@yield` 标签，以便在需要时从任何子页面注入 CSS 部分。因此，只需在主 blade 布局模板的结束 body 标签之前添加以下内容。

```
@yield('styles')
```

注册页完整代码如下所示。

```php
@extends('layout.master')

@section('sidenav')
    {{--//--}}
@endsection

@section('navbar')
    {{--//--}}
@endsection

@section('content')
    <div class="row">
        <div class="col-md-4 mx-auto mt-5 border">
            <div class="panel panel-default">
                <div class="panel-heading text-center pt-4">
                    <h4>注册</h4>
                </div>
                <div class="panel-body">
                    <form class="form-horizontal" method="POST" action="{{ route('register') }}">
                        {{ csrf_field() }}
                        <div class="form-group{{ $errors->has('name') ? ' has-error' : '' }}">
```
