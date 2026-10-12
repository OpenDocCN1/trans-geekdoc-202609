
# HTML 表单不支持 PUT、PATCH 或 DELETE 操作

因此，当定义从 HTML 表单调用的 `PUT`、`PATCH` 或 `DELETE` 路由时，你需要向表单添加一个隐藏的 `_method` 字段。`_method` 字段发送的值将被用作 HTTP 请求方法。

如果你现在刷新浏览器并点击“查看库存”菜单，将看到一个空表格。现在让我们进入数据库插入部分。

## 更新 InventoryController

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

---

### 导入类

我们使用 PHP `use` 关键字导入了 `Inventory` 模型类和 `StoreInventory` 表单请求类。

```php
use App\Http\Requests\StoreInventory;
use App\Inventory;
```

---

### 依赖注入属性

我们定义了属性 `$inventory` 来保存通过控制器注入的 `$inventory` 模型对象。

```php
public $inventory;

public function __construct(Inventory $inventory)
{
    $this->inventory = $inventory;
}
```

---

### 方法注入与表单验证

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

---

### 查询所有库存

这里我们通过调用库存模型的 `all()` 方法从数据库获取所有库存。还有其他方法，如 `latest()` 以降序获取，`first()` 获取匹配 where 条件的第一行，`select()` 选择要返回的字段以及 `get()` 方法。Laravel 为我们提供了更多查询构建器，使从数据库查询数据变得方便，在大多数情况下你不必编写或尝试记住任何 SQL 查询。

```php
public function viewInventories()
{
    $inventories = $this->inventory->all();
    return view('view-inventories',compact('inventories'));
}
```

---

## 删除库存的两个概念

关于删除库存，有两个概念我想进一步阐述。首先是我们如何定义路由以及如何在列表库存页面的循环中使用它。

在路由定义中，URL 的第二个片段是一个路由参数，将被替换为每个库存的 ID。它将由 `route()` 函数生成，我们只需将 ID 作为第二个参数传递给 `route()` 函数。你可以有多个路由参数，在这种情况下，按它们出现的顺序将参数作为数组传递给 `route()` 函数的第二个参数。

此外，Laravel 还帮助实现了一种称为**路由模型绑定**的功能。当我们向路由注入 ID 时（如本例所示），Laravel 会根据 URL 中的类型提示解析 Eloquent 模型，在我们的例子中是 `{inventory}`。简单来说，如果我们的 URL 是 `/inventories/1/drop`，Laravel 将在库存模型（`inventories` 表）中查找 ID 为 1 的行并将其返回给控制器。

```php
// Route definition
$route->delete('/inventories/{inventory}/drop','InventoryController@drop')->name('inventory.delete');

// Route usage
{{ route('inventory.delete',$inventory->id) }}
```

---

### 控制器中的删除逻辑

这里我们只需对要根据路由模型绑定注入的模型进行类型提示，并调用返回的模型对象上的 `delete()` 方法，这将删除 `inventories` 表中对应的行。

最后我们重定向到包含所有库存的页面并显示通知消息。

```php
public function drop(Inventory $inventory)
{
    $inventory->delete();
    return redirect()->route('inventory.all')
        ->with('message','New inventory successfully added!');
}
```

---

## 显示通知消息

在编辑器中打开 `resources/views/view-inventories.blade.php`，在开始的 `<table>` 标签上方放置下面的代码片段，以显示从控制器闪存到会话中的通知消息。

```blade
@if(session()->has('message'))
    <div class="alert alert-info">
        {{session('message')}} New inventory successfully added!
    </div>
@endif
```

---

## 测试功能

在浏览器中刷新应用，如果已登出则重新登录，点击“新建库存”菜单然后提交空表单。你应该会被重定向回带有输入字段下错误提示的页面。

![表单验证错误](Images/image00201.jpeg)

现在填写表单并点击“创建新库存”按钮。你应该会被重定向到列出库存的页面并显示成功通知消息。

![创建成功提示](Images/image00202.jpeg)

继续创建任意数量的库存并删除一些。你应该会对我们取得的进展印象深刻。在继续“回收站”功能之前，让我们快速更新仪表盘以反映实际创建的库存数量。

## 更新 AppController

更新 `AppController` 类以匹配下面的代码：

```php
<?php

namespace App\Http\Controllers;

use App\Inventory;
use Illuminate\Http\Request;

class AppController extends Controller
{
    public function dashboard(Inventory $inventory)
    {
        $count = $inventory->count();
        return view('dashboard',compact('count'));
    }
}
```

---

以及 `dashboard.blade.php` 文件的第 11 行。
