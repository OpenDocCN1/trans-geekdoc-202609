
在新库存视图中有几点需要注意：

1. 表单向命名路由 `inventory.store` 提交 `POST` 请求，我们之前在 `web.php` 文件中将其定义为 `POST` 路由。
2. 你会注意到一个 `if` 语句检查字段是否未通过 `StoreInventory.php` 规则中定义的验证。Laravel 会自动重定向回创建库存页面，并在请求中携带错误消息，因此我们的 `if` 语句检查字段错误是否存在并显示第一个验证失败的错误。

你的字段可能通过一条验证规则但未通过另一条，该规则的错误会被返回；但如果所有验证都通过，请求将继续执行下一个代码块。注意我们在 `value` 字段中使用了 `old('item')` 和 `old('quantity')`，当表单出错且页面重定向回时，这会获取用户输入的值，这样用户就不必在每次验证器重定向他们回去时重新输入所有值。

在此，我想谈谈一个非常有趣的话题，乍看之下可能会让人困惑，尤其是如果你是初学者的话。

### 依赖注入与控制器

依赖注入是一种技术，其中一个对象为另一个对象提供其依赖项。“依赖项”是指可在另一个对象中使用的对象。例如，如果你有一个包含 `start`、`accelerate` 和 `horn` 方法的 `Car` 类，以及一个包含 `repair`、`setNextRepairDate` 和 `testDrive` 方法的 `AutoShop` 类。你最初可能会想把属于 `AutoShop` 类的所有方法都塞进 `Car` 类里，但通过 DI（依赖注入），我们可以遵循 SOLID 设计模式中的单一职责原则。在我们的例子中，我们可以将 `Car` 对象注入到 `AutoShop` 类中，并在 `testDrive` 方法中调用 `accelerate` 方法，因为试驾汽车需要你加速汽车。

Laravel 允许你通过控制器构造函数（构造函数注入）和控制器方法（方法注入）进行注入，这些将通过服务容器自动解析。下面我们将在 `store` 方法中注入 `StoreInventory` 对象，随后 Laravel 知道我们注入了一个 Form Request 类，将使用该类中的规则验证传入的请求。

别急着困惑！这只是 Laravel 开箱即用为我们提供的功能，这样我们就不必编写大量代码来执行所有这些操作。

> **注意**
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

很快你将从控制器中看到，包含数据库中所有库存列表的库存对象数组是如何传递给视图的。我们使用 Blade 模板的 `@foreach` 指令遍历数组，并为每个条目显示项目、数量和操作按钮。这里有一个奇怪的地方需要注意，即 `method_field` 用于表单方法伪造。

## HTML 表单不支持 PUT、PATCH 或 DELETE 操作

因此，当定义从 HTML 表单调用的 `PUT`、`PATCH` 或 `DELETE` 路由时，你需要向表单添加一个隐藏的 `_method` 字段。`_method` 字段发送的值将被用作 HTTP 请求方法。

如果你现在刷新浏览器并点击“查看库存”菜单，将看到一个空表格。现在让我们进入数据库插入部分。

### 更新 InventoryController

请更新 `InventoryController` 以匹配下面的代码，我将在之后详细解释。

```php
<?php

namespace App\Http\Controllers;

use App\Http\Requests\StoreInventory;
use App\Inventory;
use Illuminate\Http\Request;

class InventoryController extends Controller
{
    public $inventory;

    public function __construct(Inventory $inventory)
    {
        $this->inventory = $inventory;
    }

    public function createInventory()
    {
        return view('new-inventory');
    }

    public function storeInventory(StoreInventory $storeInventory)
    {
        $data = $storeInventory->only('item','quantity');
        auth()->user()->inventory()->create($data);
        $msg = 'New inventory successfully added!';
        return redirect()->route('inventory.all')->with('message',$msg);
    }

    public function viewInventories()
    {
        $inventories = $this->inventory->all();
        return view('view-inventories',compact('inventories'));
    }

    /**
     * @param Inventory $inventory
     * @return \Illuminate\Http\RedirectResponse
     * @throws \Exception
     */
    public function drop(Inventory $inventory)
    {
        $inventory->delete();
        return redirect()->route('inventory.all')
            ->with('message','New inventory successfully added!');
    }
}
```

#### 导入类

我们使用 PHP `use` 关键字导入了 `Inventory` 模型类和 `StoreInventory` 表单请求类。

```php
use App\Http\Requests\StoreInventory;
use App\Inventory;
```

#### 依赖注入属性

我们定义了属性 `$inventory` 来保存通过控制器注入的 `$inventory` 模型对象。

```php
public $inventory;

public function __construct(Inventory $inventory)
{
    $this->inventory = $inventory;
}
```

#### 方法注入与表单验证

这里我们对 `StoreInventory` 对象进行了方法注入。Laravel 会自动解析并检测它是否为表单请求，如果是则应用规则验证传入的数据，这再次体现了 Laravel 试图让开发者生活更轻松。

通常当用户提交表单时，你可以使用 PHP `$_POST` 或 `$_GET` 超全局变量访问请求数据。使用 Laravel，你可以从 `Request` 对象访问数据，该对象可注入到控制器构造函数或控制器方法中。在我们的 `storeInventory` 方法中，注入了 `StoreInventory` 表单请求对象，它继承自 `Request` 类，因此我们不需要第二次注入 `Request` 对象即可从当前 HTTP 请求访问 GET 或 POST 数据。

Laravel 在请求类上提供了不同的方法来访问数据：`all()` 方法检索所有请求数据，`only()` 方法指定要检索的键，`get()` 方法访问请求参数。还有其他方法如 `except`、`intersect`、`input` 等。

我们将通过用户-库存关系在库存模型上调用 `create()` 方法，这样外键 `user_id` 将是当前登录用户。插入数据库后，我们将用户重定向到列出所有库存的页面，并显示成功通知消息。

```php
public function storeInventory(StoreInventory $storeInventory)
{
    $data = $storeInventory->only('item','quantity');
    auth()->user()->inventory()->create($data);
    $msg = 'New inventory successfully added!';
    return redirect()->route('inventory.all')->with('message',$msg);
}
```

#### 查询所有库存

这里我们通过调用库存模型的 `all()` 方法从数据库获取所有库存。还有其他方法，如 `latest()` 以降序获取，`first()` 获取匹配 where 条件的第一行，`select()` 选择要返回的字段以及 `get()` 方法。Laravel 为我们提供了更多查询构建器，使从数据库查询数据变得方便，在大多数情况下你不必编写或尝试记住任何 SQL 查询。

```php
public function viewInventories()
{
    $inventories = $this->inventory->all();
    return view('view-inventories',compact('inventories'));
}
```

### 删除库存的两个概念

关于删除库存，有两个概念我想进一步阐述。首先是我们如何定义路由以及如何在列表库存页面的循环中使用它。

在路由定义中，URL 的第二个片段是一个路由参数，将被替换为每个库存的 ID。它将由 `route()` 函数生成，我们只需将 ID 作为第二个参数传递给 `route()` 函数。你可以有多个路由参数，在这种情况下，按它们出现的顺序将参数作为数组传递给 `route()` 函数的第二个参数。

此外，Laravel 还帮助实现了一种称为**路由模型绑定**的功能。当我们向路由注入 ID 时（如本例所示），Laravel 会根据 URL 中的类型提示解析 Eloquent 模型，在我们的例子中是 `{inventory}`。简单来说，如果我们的 URL 是 `/inventories/1/drop`，Laravel 将在库存模型（`inventories` 表）中查找 ID 为 1 的行并将其返回给控制器。

```php
// Route definition
$route->delete('/inventories/{inventory}/drop','InventoryController@drop')->name('inventory.delete');

// Route usage
{{ route('inventory.delete',$inventory->id) }}
```
