
在 `app/resources/views` 目录下创建新文件 `new-inventory.blade.php`，该子视图将继承主布局并包含创建库存的表单。将以下代码复制到文件中：

```blade
@extends('layout.master')

@section('page-title')
    New Inventory
@endsection

@section('content')
    <div class="container-fluid">
        <div class="col-12 col-md-8 mt-4">
            <form method="POST" action="{{ route('inventory.store') }}">
                {{ csrf_field() }}
                <div class="form-group">
                    <label for="item">Item</label>
                    <input type="text" value="{{ old('item') }}" class="form-control" name="item" id="item" placeholder='e.g 32" Television'>
                    @if ($errors->has('item'))
                        <small class="form-text text-danger">
                            {{ $errors->first('item') }}
                        </small>
                    @endif
                </div>
                <div class="form-group">
                    <label for="quantity">Quantity</label>
                    <input type="text" value="{{ old('quantity') }}" class="form-control" name="quantity" id="quantity" placeholder="e.g 50">
                    @if ($errors->has('quantity'))
                        <small class="form-text text-danger">
                            {{ $errors->first('quantity') }}
                        </small>
                    @endif
                </div>
                <button type="submit" class="btn btn-primary">Create New Inventory</button>
            </form>
        </div>
    </div>
@endsection
```

---

在新库存视图中有几点需要注意：
1. 表单向命名路由 `inventory.store` 提交 `POST` 请求，我们之前在 `web.php` 文件中将其定义为 `POST` 路由。
2. 你会注意到一个 `if` 语句检查字段是否未通过 `StoreInventory.php` 规则中定义的验证。Laravel 会自动重定向回创建库存页面，并在请求中携带错误消息，因此我们的 `if` 语句检查字段错误是否存在并显示第一个验证失败的错误。

你的字段可能通过一条验证规则但未通过另一条，该规则的错误会被返回；但如果所有验证都通过，请求将继续执行下一个代码块。注意我们在 `value` 字段中使用了 `old('item')` 和 `old('quantity')`，当表单出错且页面重定向回时，这会获取用户输入的值，这样用户就不必在每次验证器重定向他们回去时重新输入所有值。

在此，我想谈谈一个非常有趣的话题，乍看之下可能会让人困惑，尤其是如果你是初学者的话。

### 依赖注入与控制器

依赖注入是一种技术，其中一个对象为另一个对象提供其依赖项。“依赖项”是指可在另一个对象中使用的对象。例如，如果你有一个包含 `start`、`accelerate` 和 `horn` 方法的 `Car` 类，以及一个包含 `repair`、`setNextRepairDate` 和 `testDrive` 方法的 `AutoShop` 类。你最初可能会想把属于 `AutoShop` 类的所有方法都塞进 `Car` 类里，但通过 DI（依赖注入），我们可以遵循 SOLID 设计模式中的单一职责原则。在我们的例子中，我们可以将 `Car` 对象注入到 `AutoShop` 类中，并在 `testDrive` 方法中调用 `accelerate` 方法，因为试驾汽车需要你加速汽车。

Laravel 允许你通过控制器构造函数（构造函数注入）和控制器方法（方法注入）进行注入，这些将通过服务容器自动解析。下面我们将在 `store` 方法中注入 `StoreInventory` 对象，随后 Laravel 知道我们注入了一个 Form Request 类，将使用该类中的规则验证传入的请求。

别急着困惑！这只是 Laravel 开箱即用为我们提供的功能，这样我们就不必编写大量代码来执行所有这些操作。

> **Note**
>
> 要了解更多关于依赖注入的信息，请访问 Laravel 文档 [此处](https://laravel.com/docs/5.4/controllers#dependency-injection-and-controllers)。

### 库存列表视图

在 `app/resources/views` 目录下创建新文件 `view-inventories.blade.php` 并粘贴以下代码。

```blade
@extends('layout.master')

@section('page-title')
    New Inventory
@endsection

@section('content')
    <div class="container-fluid">
        <div class="col-12 col-md-8 mt-4">
            <table class="table table-hover table-bordered">
                <thead>
                    <tr>
                        <th scope="col">#</th>
                        <th scope="col">Item</th>
                        <th scope="col">Quantity</th>
                        <th scope="col">Actions</th>
                    </tr>
                </thead>
                <tbody>
                    @foreach($inventories as $key => $inventory)
                        <tr>
                            <th scope="row">{{ $key + 1 }}</th>
                            <td>{{ $inventory->item }}</td>
                            <td>{{ $inventory->quantity }}</td>
                            <td>
                                <a href="#" class="btn btn-outline-primary btn-sm">Edit</a>
                                <a href="#" class="btn btn-outline-danger btn-sm" onclick='event.preventDefault(); document.getElementById("delete-inventory-form-{{ $key }}").submit();'>
                                    Delete
                                    <form id="delete-inventory-form-{{ $key }}" action="{{ route('inventory.delete', $inventory->id) }}" method="POST" style="display: none;">
                                        {{ csrf_field() }}
                                    </form>
                                </a>
                            </td>
                        </tr>
                    @endforeach
                </tbody>
            </table>
        </div>
    </div>
@endsection
```

---

接下来更新 `layout/partials/_sidenav.blade.php`，以添加创建和登出路由以便于导航。

```blade
<div class="bg-light border-right" id="sidebar-wrapper">
    <div class="sidebar-heading">{{ config('app.name') }}</div>
    <div class="list-group list-group-flush">
        <a href="{{ route('inventory.home') }}" class="list-group-item list-group-item-action bg-light">Dashboard</a>
        <a href="{{ route('inventory.all') }}" class="list-group-item list-group-item-action bg-light">View Inventories</a>
        <a href="{{ route('inventory.create') }}" class="list-group-item list-group-item-action bg-light">New Inventory</a>
        <a href="#" class="list-group-item list-group-item-action bg-light">Trash</a>
        <a href="#" class="list-group-item list-group-item-action bg-light" onclick="event.preventDefault(); document.getElementById('logout-form').submit();">
            Logout
            <form id="logout-form" action="{{ route('logout') }}" method="POST" style="display: none;">
                {{ csrf_field() }}
                {{ method_field('DELETE') }}
            </form>
        </a>
    </div>
</div>
```

---

很快你将从控制器中看到，包含数据库中所有库存列表的库存对象数组是如何传递给视图的。我们使用 Blade 模板的 `@foreach` 指令遍历数组，并为每个条目显示项目、数量和操作按钮。这里有一个奇怪的地方需要注意，即 `method_field` 用于表单方法伪造。
