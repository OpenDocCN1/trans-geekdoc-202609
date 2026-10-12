

`timestamps` 方法会添加可为空的 `created_at` 和 `updated_at` “TIMESTAMP” 列。当创建新行时，`created_at` 列会使用当前时间戳进行更新，而 `updated_at` 则在行更新时进行更新。最后，从终端或 git bash 运行 `migrate` 命令。

```
php artisan migrate
```

现在我们的表已经创建完成，如果你调用 MYSQL `DESCRIBE` 命令，我们的 `inventories` 表结构将如下所示。

| Field | Type | Null | Key | Default | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| id | int(10) unsigned | NO | PRI | NULL | auto_increment |
| item | varchar(255) | NO | | NULL | |
| quantity | int(11) | NO | | NULL | |
| user_id | int(10) unsigned | NO | MUL | NULL | |
| deleted_at | timestamp | YES | | NULL | |
| created_at | timestamp | YES | | NULL | |
| updated_at | timestamp | YES | | NULL | |

现在让我们继续为 `inventories` 表创建 Inventory 模型。

## 创建 Inventory 模型并定义关系

Laravel 模型代表其所对应的底层数据表的逻辑结构和关系。它允许你轻松查询表中的数据，以及插入新数据。每个表对应一个模型，这使你能够使用 Laravel ORM（对象关系映射）来与该表进行交互。

要创建模型，Laravel 允许你使用 `artisan` 命令来完成。在终端或 git bash 中运行此命令：

```
php artisan make:model Inventory
```

在 `app` 目录下，你会找到 `Inventory.php` 类。这是生成模型的默认存储位置。你可以将它们归组在 `app/Models` 目录或任何你想要的位置，但为保持简单，我们将其留在此处。

接下来，让我们在模型中定义该表的关系。同样，Laravel 允许我们在多个表上定义不同类型的关系。你可以在对应表的模型中使用 `hasMany` 方法定义一对多关系，使用 `hasOne` 方法定义一对一关系，使用 `belongsToMany` 方法定义多对多关系，以及其他几种关系。

在我们的案例中，一个用户可以创建/拥有多个库存，反之，一个库存将属于一个用户，因此我们有用户 `hasMany` 库存和库存 `belongsTo` 用户。让我们在模型中定义这一点。

> **注意**
>
> 要了解更多关于在数据库中创建不同列类型的可用方法，可以查看 [Laravel 文档](https://laravel.com/docs/5.4/migrations#creating-columns) 中的可用列类型。

在我们的 `app/User.php` 模型类中，添加 `inventories` 方法。

```php
public function inventories()
{
    return $this->hasMany(Inventory::class);
}
```

打开 `app/Inventory.php` 模型类以定义反向关系。

```php
public function ownedBy()
{
    return $this->belongsTo(User::class);
}
```

此外，在库存模型类中，添加如下受保护属性 `guarded`。

```php
protected $guarded = ['id'];
`

暂时不要困惑。`guarded` 属性是 Laravel `Model` 类（我们的 `Inventory` 模型类继承自该类）已定义的一个继承受保护属性。Laravel 允许你使用查询构造器，只需传入一个包含你想要插入的数据的数组，即可将数据批量赋值到数据库中。

有时这可能很糟糕，因为恶意用户可能会猜测你表中的字段并注入有害数据传入你的数据库。因此，为了使某些重要字段免于被批量赋值，比如在我们的例子中的 `id` 字段（因为我们不希望有人插入他们自己的 id 并破坏我们的自增行为），我们只需使该字段不可批量赋值。最后，因为我们想要实现的软删除功能，我们为此引入了 `SoftDeletes` trait。

你完整的 `Inventory` 模型类应如下所示：

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\SoftDeletes;

class Inventory extends Model
{
    use SoftDeletes;

    protected $guarded = ['id'];

    public function ownedBy()
    {
        return $this->belongsTo(User::class);
    }
}
```

## 定义路由、Inventory 控制器和请求验证

让我们处理创建库存的业务逻辑。首先，运行 artisan 命令创建一个 Inventory 控制器。为此，请运行以下命令：

```
php artisan make:controller InventoryController
```

在 `app/Http/Controllers` 下，Laravel 将生成 `InventoryController.php` 类。编辑此文件并添加以下占位符方法。我们稍后会更新它们。

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class InventoryController extends Controller
{
    public function createInventory()
    {
        return view('new-inventory');
    }

    public function storeInventory()
    {
        //validate & store in db
    }

    public function viewInventories()
    {
        //retrieve and list
    }
}
```

在我们的路由文件 `app/routes/web.php` 中，添加创建、存储和查看库存的 URL。更新路由组以匹配下方内容：

```php
Route::group(['prefix' => 'app', 'middleware' => 'auth'], function ($route) {
    $route->get('/', 'AppController@dashboard')->name('inventory.home');
    $route->get('/create', 'InventoryController@createInventory')->name('inventory.create');
    $route->post('/create', 'InventoryController@storeInventory')->name('inventory.store');
    $route->get('/inventories', 'InventoryController@viewInventories')->name('inventory.all');
    // 花括号中的值必须与我们要从中删除数据的表的模型匹配，因为这将允许 Laravel 知道要解析哪个类
    $route->delete('/inventories/{inventory}/drop', 'InventoryController@drop')->name('inventory.delete');
});
```

接下来，让我们创建一个表单请求验证来验证发送到 `storeInventory` 方法的请求。我们将为即将创建的创建表单中用户输入的两个字段定义验证规则。一个经验法则是永远不要信任用户输入，并始终致力于验证它们。要创建我们的表单请求，请运行以下命令：

```
php artisan make:request StoreInventory
```

一个新类 `StoreInventory.php` 将在 `app/Http/Requests` 目录下创建。编辑此文件。首先，在 `authorize` 方法下，将 `return false` 改为 `return true`。现在让我们为表单中将包含的两个输入字段 `item` 和 `quantity` 定义规则。

我们希望 `item` 字段始终为不超过 255 个字符的字符串（这是 mysql `VARCHAR` 的最大长度，以避免 mysql 截断数据），`quantity` 字段应为整数，不允许超过 100（假设我们永远不想创建库存超过 100 件的库存）。这两个字段均为必填。将 `rules` 方法中返回的空数组替换为下方内容：

```php
return [
    'item' => 'required|string|max:255',
    'quantity' => 'required|int|max:100'
];
```

> **注意**
>
> 要了解更多 Laravel 中可用的验证规则，请访问官方 Laravel 文档的 [可用验证规则](https://laravel.com/docs/5.4/validation#available-validation-rules) 部分。

## 创建库存表单和列出库存

