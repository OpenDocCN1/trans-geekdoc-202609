

echo '||.$products[$row]['Price']|';br />';

}

使用 `for` 循环，你可以遍历通过数字索引的外部 `$products` 数组。$products` 数组中的每一行都是一个带有索引的数组。在 `while` 循环中使用 `each()` 和 `list()` 函数，你可以遍历这些内部数组。因此，你可以在 `for` 循环内部使用 `while` 循环：

```php
for ($row = 0; $row < 3; $row++) {
    while (list($key, $value) = each($products[$row])) {
        echo '||.$value;';
    }
    echo '<br />';
}
```

你不需要停留在两个维度。就像数组元素可以包含新数组一样，这些数组反过来也可以包含更多的数组。

三维数组具有高度、宽度和深度。如果你习惯将二维数组想象成带有行和列的表格，那么请想象一叠桌子或扑扑牌。每个元素都通过其层、行和列来引用。

如果 Bob 将他的产品分为不同的类别，你可以使用三维数组来存储它们。图 3.4 显示了三维数组中的 Bob 的产品。

| 卡车零件 | | | |
| :--- | :--- | :--- | :--- |
| 代码 | 描述 | 价格 | |
| 面货车零件 | | | |
| 代码 | 描述 | 价格 | |
| 汽车零件 | | | |
| 代码 | 描述 | 价格 | |
| CAR_TIR | 轮胎 | 100 | |
| CAR_OIL | 机机油 | | |
| CAR_SPK | 火花塞 | 4 | |

图 3.4 此三维数组允许你将产品分类

从定义此数组的代码中，你可以看到三维数组是一个包含数组的数组的数组：

```php
$categories = array(
    array(array('CAR_TIR', 'Tires', 100 ),
          array('CAR_OIL', 'Oil', 10 ),
          array('CAR_SPK', 'Spark Plugs', 4)),
    array(array('VAN_TIR', 'Tires', 120 ),
          array('VAN_OIL', 'Oil', 12 ),
          array('VAN_SPK', 'Spark Plugs', 5 )),
    array(array('TRK_TIR', 'Tires', 150 ),
          array('TRK_OIL', 'Oil', 15 ),
          array('TRK_SPK', 'Spark Plugs', 6 ))
);
```

由于此数组仅包含数字索引，你可以使用循环来显示其内容：

```php
for ($layer = 0; $layer < 3; $layer++) {
    echo 'Layer'.$layer.'<br />';
    for ($row = 0; $row < 3; $row++) {
        for ($column = 0; $column < 3; $column++) {
            echo '|'.$categories[$layer][$row][$column];
        }
        echo '<br />';
    }
}
```

由于多维数组的创建方式，你可以创建五维甚至六维的数组。语言对维数没有限制，但对于人类来说，可视化超过三个维度的结构是非常困难的。大多数世界中的问题在逻辑上都与三个或更少维度的结构匹配。

## 排序数组

对数组中的数据进行排序通常有用。你可以轻松地取一个一维数组对其进行排序。

## 使用 sort()

以下代码显示了 `sort()` 函数的结果，该数组被按字母升序排序：

```php
$products = array('Tires', 'Oil', 'Spark Plugs');
sort($products);
```

数组元素现在将按照 Oil, Spark Plugs, Tires 的顺序出现。

你也可以按数值顺序对值排序。如果你有一个包含 Bob 产品价格的数组，你可以将其按数值升序排序如下：

```php
$prices = array(100, 10, 4);
sort($prices);
```

价格现在将按照 4, 10, 100 的顺序出现。

注意 `sort()` 函数是区分大小写的。所有大写字母都在小写字母之前。因此 A 小于 Z，但 Z 小于 a。

该函数还有一个可选的第二个参数。你可以传递常量之一：`SORT_REGULAR`（默认值）、`SORT_NUMERIC`、`SORT_STRING`、`SORT_LOCALE_STRING`、`SORT_NATURAL`、`SORT_FLAG_CASE`。

指定排序类型的能力在比较可能包含数字的字符串时（例如 2 和 12）非常有用。在数值上，2 小于 12，但作为字符串 '12' 小于 '2'。

传递 `LOCALE_STRING` 常量将根据当前区域将数组作为字符串排序，且排序顺序在不同的区域是不同的。`SORT_NATURAL` 会导致自然排序。你也可以通过使用 `natsort()` 函数获得这种效果。自然排序顺序是字符串和数值排序的结合，使其更加直观。对 'file1'、file2' 和 'file10' 使用字符串排序将按顺序排列为 'file1' 'file10' 'file2'。而使用自然排序，它们的顺序将是 'file1' 'file2' 'file10'，这对人类来说更直观——或者说更自然。

常量 `SORT_CASE` 与 `SORT_STRING` 或 `SORT_NATURAL` 配合使用。我们使用位运算符将它们组合。

