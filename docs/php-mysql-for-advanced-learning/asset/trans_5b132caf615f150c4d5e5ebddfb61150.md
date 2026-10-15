

```php
return $this->greeting. "<br />";
}
}
// 创建类对象
$obj = new MyClass;
// 获取属性值
echo $obj->getProperty();
// 设置一个新值
$obj->setProperty("Good Afternoon");
// 让我们打印当前值
echo $obj->getProperty();
?>
```

## 注释

## PHP 中的 MVC（模型-视图-控制器）

MVC 是一种应用程序架构或设计模式，其基本原理基于应用逻辑应与表示层分离这一思想。简单来说，MVC 是一种更好地将应用逻辑与显示分开的方式。使用 MVC 的好处是让你的应用更易于维护。

### 模型（Model）

模型是系统所有部分中最复杂的，它将包含所有特定于应用的逻辑。它是应用程序中获取数据（来自任何来源）并处理数据的部分。简单来说，模型负责管理数据；它存储和检索应用程序使用的实体（通常来自数据库），并包含应用程序实现的逻辑。

### 视图（View）

视图包含所有显示逻辑。在 PHP 中，它是应用程序中生成 HTML 的部分。它可以直接访问模型，并可以查询模型以获取其数据。简单来说，视图负责以特定格式显示模型提供的数据。它与一些流行的 Web 应用程序（如 WordPress、Joomla 等）中的模板模块有类似的用法。

### 控制器（Controller）

控制器接收用户输入，并在需要时更新模型。请注意，控制器不是视图和模型之间的中介或网关。视图从自己的模型中获取数据。控制器可以访问模型，但自身不包含任何显示逻辑。控制器所做的只是响应用户输入。

换句话说，“控制器处理模型和视图层的协同工作。控制器接收来自客户端的请求，调用模型执行请求的操作，并将数据发送给视图。视图将数据格式化后呈现给用户，在 Web 应用程序中通常输出为 HTML。”

### MVC 程序流程

- 模型、视图和控制器被初始化
- 视图向用户显示，并从模型读取数据
- 用户与视图交互（例如按下按钮），这会调用指定的控制器动作
- 控制器以某种方式更新模型
- 视图刷新（从模型获取更新后的数据）

### 一个简单的 MVC 程序

```php
<?php

class Model
{
    public $text;

    public function __construct()
    {
        $this->text = 'Hello.. Lets learn MVC pattern in PHP';
    }
}

class View
{
    private $model;

    public function __construct(Model $model)
    {
        $this->model = $model;
    }

    public function output()
    {
        return '<h1>'. $this->model->text .'</h1>';
    }
}

class Controller
{
    private $model;

    public function __construct(Model $model)
    {
        $this->model = $model;
    }
}

$model = new Model();

$controller = new Controller($model);

$view = new View($model);

echo $view->output();

?>
```

## 注释

## MySQL/MariaDB – 进阶学习

### 连接（Joins）

MySQL JOIN 用于从多个表中检索数据。在大多数实际的 MySQL 使用场景中，你经常需要在单个查询中从多个表获取数据。因此，为了访问可能相互关联的不同表中的数据，我们在 MySQL 中使用 JOIN 子句。

MySQL 连接有三种类型：

- INNER JOIN（简单连接）
- LEFT OUTER JOIN（左连接）
- RIGHT OUTER JOIN（右连接）

![](img/9ab4a56a650535285811bb802190e58f_145_0.png)

### INNER JOIN 或简单连接

MySQL INNER JOIN 用于从表中返回满足连接条件的所有行。它也是默认的连接类型。简单来说，它可以用来从多个表中检索共同的记录/行。

![](img/9ab4a56a650535285811bb802190e58f_146_0.png)

考虑两个表“users”和“rec”，它们具有以下数据。

### 表 - Users

| uid | email | city | name |
|---|---|---|---|
| 1 | h@gmail.com | gurgaon | hirdesh |
| 2 | suzeet@gmail.com | delhi | sujeet |
| 3 | pooja@gmail.com | noida | pooja |
| 4 | sw@gmail.com | gurgaon | swati |

### 表 - rec

| uid | month | days |
|---|---|---|
| 1 | Jan | 23 |
| 2 | jan | 21 |
| 2 | march | 30 |
| 3 | feb | 25 |
| 4 | jul | 21 |
| 3 | mar | 12 |
| 4 | dec | 22 |
| 4 | jul | 13 |

这个 MySQL INNER JOIN 示例将返回 users 和 rec 表中所有在两个表中具有匹配 uid 值的行。

### 查询

```sql
Select * from users inner join rec on users.uid=rec.uid;
```

### 左外连接（LEFT OUTER JOIN）

MySQL LEFT OUTER JOIN 返回 ON 条件中指定的左表中的所有行，以及另一个表中连接字段相等的那些行。

![](img/9ab4a56a650535285811bb802190e58f_147_0.png)

这将返回 users 表中的所有行，以及 rec 表中连接字段相等的那些行。

### 查询

```sql
Select * from users left join rec on users.uid=rec.uid;
```

### 右外连接（RIGHT OUTER JOIN）

MySQL RIGHT OUTER JOIN 返回 ON 条件中指定的右表中的所有行，以及另一个表中连接字段相等的那些行。

![](img/9ab4a56a650535285811bb802190e58f_147_1.png)

### 查询

```sql
Select * from users right join rec on users.uid=rec.uid;
```

这将返回 **rec** 表中的所有行，以及 **users** 表中连接字段相等的那些行。

### 练习作业

1. 编写一条 SQL 语句，为同时出现在两个表中的客户准备一份包含客户姓名、城市、计划类型、付款方式及其收入来源的列表。
2. 编写一条 SQL 语句，为同时出现在两个表中且其保单状态为有效的客户准备一份包含客户姓名、城市、计划类型、付款方式及其收入来源的列表。
3. 编写一条 SQL 语句，为存款金额在 7000 到 10000 之间的订单准备一份包含客户姓名、存款金额及其城市的列表。
4. 列出不在辅助表中但也不在主表中的客户（提示：使用基于电子邮件地址的右连接）。

并且不在实际表中，因此即使应用了非聚集索引，列值也会保持在相同的位置。

你可以在同一个 SQL 表中拥有多个非聚集索引。

```sql
Create Nonclustered index emp_salary on employees (Salary ASC);
```

### 查看表中的索引的查询

```sql
show index from employee;
```

### 删除索引的命令的查询

```sql
drop index employees.emp_salary;
```

请注意，当你向列添加主键或唯一键时，会自动创建索引（类型为聚集索引），因为主键本身就是一个聚集索引。因此，自动创建索引的过程称为隐式索引。

**聚集索引：** 当你向列添加主键时，意味着你已经添加了三个约束，即主键、非空和聚集索引。所以一个表只能有一个聚集索引。（不过这一个聚集索引可以引用多个列，称为复合索引）

你也可以在有主键或没有主键的情况下创建聚集索引（也称为自定义索引），如下所示——

```sql
create clustered index ids on employees (id desc);
```

在多个列上创建复合聚集索引

```sql
create clustered index myIndex on employees (id desc,gender ASC);
```

### 非聚集索引与聚集索引

聚集索引有助于在内存中物理地排列行。因此，索引后的更改可以在表中看到，而不是在堆中。另一方面，非聚集索引不会在内存中按排序顺序物理地排列行。

请注意：MySQL InnoDB 引擎有强制性的聚集索引。这意味着总是存在一个聚集索引，通常使用主键。如果没有可用的合适唯一键，MySQL 将使用生成的行 ID 来实现该目的。MyISAM 存储引擎不支持聚集索引，并且一直使用堆表。

在 MyISAM 引擎中只能使用一种类型的索引（非聚集）。

