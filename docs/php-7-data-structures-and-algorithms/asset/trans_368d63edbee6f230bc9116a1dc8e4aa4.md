
为了理解 PHP 数组的内部结构，我们需要深入研究 PHP 内核。这超出了本书的范围。推荐阅读：[https://nikic.github.io/2011/12/12/How-big-are-PHP-arrays-really-Hint-BIG.html](https://nikic.github.io/2011/12/12/How-big-are-PHP-arrays-really-Hint-BIG.html)

在新的 PHP 7 版本中，PHP 数组及其内部构造方式有了非常大的改进。因此，每个元素 144 字节的开销已降至仅 36 字节。这是一个巨大的改进，适用于 32 位和 64 位操作系统。下面展示了一个包含 100,000 个项目的数组对比图表：

| **$array = Range(1,100000)** | **32 位** | **64 位** |
| --- | --- | --- |
| PHP 5.6 或更低版本 | 7.4 MB | 14 MB |
| PHP 7 | 3 MB | 4 MB |

换句话说，对于数组存储，PHP 7 在 32 位系统上提升了 2.5 倍，在 64 位系统上提升了 3.5 倍。这是一个非常好的改进。但这都是关于 PHP 数组的，那 `SplFixedArray` 呢？让我们在 PHP 7 和 PHP 5.x 中使用 `SplFixedArray` 运行相同的示例：

```
$items = 100000;

$startMemory = memory_get_usage();

$array = new SplFixedArray($items);

for ($i = 0; $i < $items; $i++) {

    $array[$i] = $i;

}

$endMemory = memory_get_usage();

$memoryConsumed = ($endMemory - $startMemory) / (1024 * 1024);

$memoryConsumed = ceil($memoryConsumed);

echo "memory = {$memoryConsumed} MB\n";
```

我们在这里编写了 `SplFixedArray` 的内存消耗功能。如果我们只将 `$array = new SplFixedArray($items);` 这一行改为 `$array = [];`，我们将得到运行 PHP 数组时相同的代码。

基准测试结果可能因机器而异，因为可能存在不同的操作系统、内存大小、调试器开启/关闭等情况。始终建议在您自己的机器上运行代码，以生成用于比较的类似基准测试。

下面是在 64 位系统上，包含 100,000 个整数的数组中，PHP 数组和 `SplFixedArray` 的内存消耗对比：

| **100,000 个项目** | **使用 PHP 数组** | **SplFixedArray** |
| --- | --- | --- |
| PHP 5.6 或更低版本 | 14 MB | 6 MB |
| PHP 7 | 5 MB | 2 MB |

不仅在内存使用方面，`SplFixedArray` 在执行速度上也比常规 PHP 数组操作（如访问值、赋值等）更快。

虽然我们像使用数组一样使用 `[]` 来操作 `SplFixedArray` 对象，但 PHP 数组函数不适用于 `SplFixedArray`。我们不能直接应用任何 PHP 数组函数，例如 `array_sum`、`array_filter` 等。

# 使用 SplFixedArray 的更多示例

由于 `SplFixedArray` 具有良好的性能提升指标，我们可以在大多数数据结构和算法中利用它来代替常规 PHP 数组。现在我们将探索在不同场景下使用 `SplFixedArray` 的更多示例。

# 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

# 从 PHP 数组转换为 SplFixedArray

我们已经了解了如何创建一个具有固定长度的 `SplFixedArray`。如果我想在运行时创建一个从数组到 `SplFixedArray` 的转换怎么办？以下代码块展示了如何实现：

```
$array = [1 => 10, 2 => 100, 3 => 1000, 4 => 10000];

$splArray = SplFixedArray::fromArray($array);

print_r($splArray);
```

这里我们使用 `SplFixedArray` 类的静态方法 `fromArray`，从现有数组 `$array` 构造一个 `SplFixedArray`。然后我们使用 PHP `print_r` 函数打印该数组。它将显示如下输出：

```
SplFixedArray Object

(

    [0] =>

    [1] => 10

    [2] => 100

    [3] => 1000

    [4] => 10000

)
```

我们可以看到数组现已转换为 `SplFixedArray`，并且完全保持了实际数组中的索引编号。由于实际数组未定义索引 0，此处索引 0 保留为 null。但如果我们想忽略前一个数组的索引并分配新索引，则必须将前面代码的第二行更改为：

```
$splArray = SplFixedArray::fromArray($array, false);
```

现在如果我们再次打印数组，将得到以下输出：

```
SplFixedArray Object

(

    [0] => 10

    [1] => 100

    [2] => 1000

    [3] => 10000

)
```

如果我们想在运行时将数组转换为固定数组，如果常规 PHP 数组后续不再使用，最好将其 `unset` 掉。如果是大数组，这将节省内存使用。

# 将 SplFixedArray 转换为 PHP 数组

我们可能还需要将 `SplFixedArray` 转换为常规 PHP 数组，以应用 PHP 的一些预定义数组函数。像前面的例子一样，这也非常简单：

```
$items = 5;

$array = new SplFixedArray($items);

for ($i = 0; $i < $items; $i++) {

    $array[$i] = $i * 10;

}

$newArray = $array->toArray();

print_r($newArray);
```

这将产生以下输出：

```
Array

(

    [0] => 0

    [1] => 10

    [2] => 20

    [3] => 30

    [4] => 40

)
```

# 声明后更改 SplFixedArray 大小

由于我们在开始时定义了数组大小，稍后可能需要更改大小。为此，我们必须使用 `SplFixedArray` 类的 `setSize()` 方法。示例如下：

```
$items = 5;

$array = new SplFixedArray($items);

for ($i = 0; $i < $items; $i++) {

    $array[$i] = $i * 10;

}

$array->setSize(10);

$array[7] = 100;
```

# 使用 SplFixedArray 创建多维数组

我们可能还需要使用 `SplFixedArray` 创建二维或更多维数组。为此，建议遵循以下示例：

```
$array = new SplFixedArray(100);

for ($i = 0; $i < 100; $i++)

    $array[$i] = new SplFixedArray(100);
```

我们实际上是在每个数组索引内创建另一个 `SplFixedArray`。我们可以添加任意数量的维度。但我们必须记住，随着维度的增加，我们是在乘以数组的大小。因此它可能会非常快地变得非常大。

# 理解哈希表

在编程语言中，哈希表是一种用于使数组具有关联性的数据结构。这意味着我们可以使用键来映射值，而不是使用索引。哈希表必须使用哈希函数计算索引，以索引桶或槽位数组，从中可以找到所需的值：

![](Image00020.jpg)

正如我们多次提到的，PHP 数组实际上是一个哈希表，因此它支持关联数组。我们需要记住一点：我们不需要为关联数组实现定义哈希函数。PHP 会在内部为我们完成。因此，当我们在 PHP 中创建关联数组时，实际上是在创建一个哈希表。例如，以下代码可视为哈希表：

```
$array = [];

$array['Germany'] = "Position 1";

$array['Argentina'] = "Position 2";

$array['Portugal'] = "Position 6";

$array['Fifa_World_Cup'] = "2018 Russia";
```

事实上，我们可以直接调用任意键，复杂度仅为 **O(1)**。键将始终引用桶内的同一个索引，因为 PHP 将使用相同的哈希函数来计算索引。

# 使用 PHP 数组实现结构体

正如我们已知，结构体是一种复杂的数据类型，我们在其中将多个属性定义为一组，以便将其作为单一数据类型使用。我们可以使用 PHP 数组和类来编写结构体。以下是使用 PHP 数组实现结构体的示例：

```
$player = [

    "name" => "Ronaldo",

    "country" => "Portugal",

    "age" => 31,

    "currentTeam" => "Real Madrid"

];
```
