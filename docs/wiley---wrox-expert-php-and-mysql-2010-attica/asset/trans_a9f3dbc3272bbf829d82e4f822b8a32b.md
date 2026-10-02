
## 观察者模式与发布者/订阅者模式

观察者模式和发布者/订阅者模式在基于事件的架构中比在大多数无状态的服务器端互联网应用中更常见；然而它们在 PHP 中也有用途。观察者模式实现起来更简单，在大多数情况下已足够，因此先介绍它。

在观察者模式中，观察者必须知道正在广播其想要监听的事件的对象。这是一种狙击步枪式的事件处理方法。当发布者对象上发生事件时，它会同时通知所有观察者。但如果另一个对象触发了相同的事件，除非观察者也在监视该对象，否则不会广播。在清单 1-13 中，可以用一个类和一个接口定义一个简单的可重用观察者系统：

### 清单 1-13: Observer.interface.php
```php
<?php
interface Observer {
    public function notify( $event );
};
?>
```

可观察对象随后包含一个可用于注册观察者的方法，如清单 1-14 所示。

### 清单 1-14: OBSERVABLEOBJECT.CLASS.PHP
```php
<?php
class ObservableObject {
    private $observers = array();

    public function observe( Observer $observer ) {
        $this->observers[] = $observer;
    }

    public function dispatch( $event ) {
        foreach ( $this->observers as $observer )
            $observer->notify( $event );
    }
};
?>
```

想要广播事件的类扩展 ObservableObject，而任何想要监听事件的类只需实现 Observer 接口。在更复杂的系统中，观察者可以指定其想要监听的事件类型。

发布者/订阅者模式类似，只是它将订阅者（观察者）与发布者（可观察对象）解耦。取而代之的是引入了一个名为 Event 的新类。观察者会在应用程序中的任何位置触发事件时订阅通知，而不是仅观察单个类上的事件。观察者不知道也不关心哪些类可以发布该事件。

有些系统使用控制器作为所有事件的委托来实现发布者/订阅者模式。这种方法要求所有事件都在中央位置注册。为了简单起见，事件对象本身将充当委托（清单 1-15）：

### 清单 1-15: BroadcastingEvent.class.php
```php
<?php
class BroadcastingEvent {
    private static $observers = array();

    public static function subscribe( Observer $observer ) {
        self::$observers[] = $observer;
    }

    public function publish() {
        foreach ( self::$observers as $observer )
            $observer->notify( $this );
    }
};
?>
```

BroadcastingEvent 类和 ObservableObject 类看起来非常相似。两处变化是：观察者数组现在是类中的静态变量而不是实例变量，并且事件类型不再需要传递给分发函数，因为分发是事件本身的方法。

重大的范式转变是观察者和分发对象不再需要了解彼此。这种解耦允许观察者/订阅者监听该类型的所有事件，而无需特定的应用程序知识。

在 PHP 应用中，该模式用于可以动态扩展的系统，例如内容管理系统。例如，一个对象可以监听用户加载事件并执行特定操作。CMS 不应要求对所有模块的实现级知识。

## 使用 MySQL 连接

从包含多个表的规范化关系数据库中检索数据通常涉及在 SELECT 语句中使用连接。MySQL 查询中的连接使您能够在单个 SQL 语句中从多个表中选择或操作数据。

SQL 标准提供了各种不同的连接操作，例如 INNER JOIN、OUTER JOIN、STRAIGHT_JOIN 和 NATURAL JOIN。MySQL 实现了大多数常见的连接语法；然而，您的预期可能在不同的关系数据库产品之间有所不同。

以下示例使用两个简单的基表来演示各种不同的连接。第一个表包含颜色，第二个表包含国家旗帜的颜色。示例数据包括以下行：

为了简单起见，此数据已去规范化以演示各种可能的 MySQL 连接语法。这些表结构不一定代表最佳数据库模式设计（见表 1-1）。要为本节中的所有示例构建此表和数据，请参阅代码文件 create-tables.sql

### 表 1-1: 架构表

| 表 | 值 |
|---|---|
| Colors | Red, White, Blue, Green, Black |
| Flags | USA, Australia, Canada, Japan, Sweden |

要理解多表连接，可以使用集合的概念和 Venn 图的数学可视化方法。这显示了各种集合之间的交互，因此可以用来检索信息的连接类型。有关 Venn 图的更多背景信息，请参阅 http://en.wikipedia.org/wiki/Venn_diagram。

图 1-1 显示了两个独立信息集合的 Venn 图。

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_55_0.png)

### 图 1-1

如果您想知道美国国旗中的颜色，可以使用以下 SELECT 语句检索必要的行，如图 1-1 所描述。这在清单 1-16 中显示。

### 清单 1-16: simple-select.sql
```sql
SELECT color
FROM flags
WHERE country='USA';
```
+--------+
| color |
+--------+
| Blue |
| Red |
| White |
+--------+

请注意前一个列表中的以下内容：
- 第 1 行指定您想要检索的列。
- 第 2 行指定您想要从中检索这些列的表。
- 第 3 行指定您想要限制要检索的行类型的任何条件或条件。

图 1-2 显示了这两个集合的交集的 Venn 图，以及两个例外信息集合。

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_56_0.png)

1. 未在旗帜中出现的颜色
2. 旗帜中的颜色
3. 无效颜色

### 图 1-2

## 内连接

如果您想了解美国国旗颜色的更多属性，可以使用清单 1-17 中所示的 INNER JOIN，与 colors 表一起检索更多信息。

### 清单 1-17: inner-join.sql
```sql
SELECT flags.color, colors.is_primary, colors.is_dark, colors.is_rainbow
FROM   flags
INNER JOIN colors ON flags.color = colors.color
WHERE  flags.country='USA';
```

| color | is_primary | is_dark | is_rainbow |
|---|---|---|---|
| Blue | yes | yes | yes |
| Red | yes | no | yes |
| White | yes | no | no |

请注意前一个列表的以下内容：
- 第 1 行从 colors 表中选择额外的列。
- 第 3 行指定与 colors 表和 flags 表的 INNER JOIN，并说明您希望在 flags 中的 color 列与 colors 中的 color 列上进行连接。

### 表别名

在 MySQL 中使用连接时，对 SQL 查询中使用的表进行别名是常见做法。您可以非常轻松地重写前面的示例，如清单 1-18 所示。

### 清单 1-18: inner-join-alias.sql
```sql
SELECT f.color, c.is_primary, c.is_dark, c.is_rainbow
FROM   flags f
INNER JOIN colors c ON f.color = c.color
WHERE  f.country='USA';
```

对于每个表，您可以在 FROM 子句中在表名后可选地指定别名。对别名的长度没有一般限制；然而，最好使用适合您应用程序的命名标准。MySQL 中表别名的最大长度为 256 个字符，而表名只有 64 个字符。

### ON 和 USING

对于连接命令，ON 语法的格式为 table1.column_name = table2.column_name。

当您的模式设计在连接表之间以相同的方式命名列时，您可以使用格式为 USING(column_name) 的 USING 语法来简化 ON 语法。示例请参阅清单 1-19。

### 清单 1-19: inner-join-using.sql
```sql
SELECT f.color, c.is_primary, c.is_dark, c.is_rainbow
FROM   flags f
INNER JOIN colors c USING (color)
WHERE  f.country='USA';
```

在第 3 行您将看到 USING 语法作为前一个 SQL 示例中 ON 语法的替代方案。

> 当两个表之间的列名相同时，您可以简单地使用 ON 语法与 USING 语法。这是良好的实践，使用适当的数据库命名标准，并在不同表中包含相同数据时指定具有相同名称的列。

### 一种替代的 INNER JOIN 语法

您还可以使用逗号（,）语法指定 INNER JOIN，如清单 1-20 所示。
