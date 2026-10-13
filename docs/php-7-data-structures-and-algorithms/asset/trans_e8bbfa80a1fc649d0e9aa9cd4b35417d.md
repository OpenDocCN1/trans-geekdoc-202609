
这行展示了一个典型数组应有的样子。相似类型的数据拥有顺序索引（从 0 到 4）来访问值。那么谁说 PHP 数组不是典型数组？让我们探索更多示例。请看下面的代码：

```
$mixedArray = [];

$mixedArray[0] = 200;

$mixedArray['name'] = "Mixed array";

$mixedArray[1] = 10.65;

$mixedArray[2] = ['I', 'am', 'another', 'array'];
```

这是我们日常使用的 PHP 数组；我们不需要定义大小，却可以存储整数、浮点数、字符串，甚至另一个数组。这听起来奇怪吗，还是说这正是 PHP 的超能力？我们可以参考 [http://php.net](http://php.net) 的定义。

PHP 中的数组实际上是一个**有序映射**。映射是一种将值关联到键的类型。此类型针对多种不同用途进行了优化；它可以被视作数组、列表（向量）、哈希表（映射的一种实现）、字典、集合、栈、队列，以及可能更多用途。由于数组值可以是其他数组，因此树和多维数组也是可能的。

所以 PHP 数组拥有真正的超能力，可用于所有可能的数据结构，如列表/向量、哈希表、字典、集合、栈、队列、双向链表等。看来 PHP 数组的构建方式使其要么针对所有场景都已优化，要么对任何场景都未优化。我们将在本章中探究这一点。

如果我们想对数组进行分类，主要有三种类型：

*   数值数组
*   关联数组
*   多维数组

我们将通过一些示例和解释来探索每种类型的数组。

## 数值数组

数值数组并不意味着它只存放数值数据。实际上，它意味着索引只能是数字。在 PHP 中，它们可以是顺序的，也可以是非顺序的，但必须是数字。在数值数组中，值以线性方式存储和访问。以下是一些 PHP 数值数组的示例：

```
$array = [10,20,30,40,50];

$array[] = 70;

$array[] = 80;

$arraySize = count($array);

for($i = 0;$i<$arraySize;$i++) {

    echo "Position ".$i." holds the value ".$array[$i]."\n";

}
```

这将产生以下输出：

```
Position 0 holds the value 10

Position 1 holds the value 20

Position 2 holds the value 30

Position 3 holds the value 40

Position 4 holds the value 50

Position 5 holds the value 70

Position 6 holds the value 80
```

这是一个非常简单的示例，我们定义了一个数组，索引从 0 开始自动生成并随数组值递增。当我们使用 `$array[]` 向数组添加新元素时，它实际上会递增索引并在新索引处赋值。这就是为什么值 70 的索引是 5，而 80 的索引是 6。

如果我们的数据是顺序的，我们总可以毫无问题地使用 `for` 循环。当我们说顺序时，并不只是指 0,1,2,3....,*n*。它可以是 0,5,10,15,20,......,*n*，其中 *n* 是 5 的倍数。也可以是 1,3,5,7,9......,*n*，其中 *n* 是奇数。我们可以创建成百上千个这样的序列来构成数值数组。

一个大问题是，如果索引不是顺序的，我们能否构建数值数组？是的，完全可以。我们只需采用不同的方式来迭代。请看下面的示例：

```
$array = [];

$array[10] = 100;

$array[21] = 200;

$array[29] = 300;

$array[500] = 1000;

$array[1001] = 10000;

$array[71] = 1971;

foreach($array as $index => $value) {

    echo "Position ".$index." holds the value ".$value."\n";

}
```

如果我们观察这些索引，它们并非顺序的。它们拥有随机索引，如 `10` 后跟 `21`、`29` 等。甚至最后我们有索引 `71`，它比之前的 `1001` 小得多。那么，最后的索引应该显示在 29 和 500 之间吗？这是输出结果：

```
Position 10 holds the value 100

Position 21 holds the value 200

Position 29 holds the value 300

Position 500 holds the value 1000

Position 1001 holds the value 10000

Position 71 holds the value 1971
```

这里有几点需要注意：

*   我们按照数据录入的顺序迭代数组。索引完全没有内部排序，尽管它们全是数字。
*   另一个有趣的事实是数组 `$array` 的大小只有 `6`。它不像 C++、Java 或其他语言那样是 `1002`，在这些语言中我们需要预先定义数组大小，且最大索引只能是 *n-1*（其中 *n* 是数组大小）。

## 关联数组

关联数组通过键来访问，键可以是任意字符串。在关联数组中，值是针对键存储的，而不是线性索引。我们可以像使用数值数组一样，使用关联数组存储任意类型的数据。让我们创建一个学生数组来存储学生信息：

```
$studentInfo = [];

$studentInfo['Name'] = "Adiyan";

$studentInfo['Age'] = 11;

$studentInfo['Class'] = 6;

$studentInfo['RollNumber'] = 71;

$studentInfo['Contact'] = "info@adiyan.com";

foreach($studentInfo as $key => $value) {

    echo $key.": ".$value."\n";

}
```

这是代码的输出：

```
Name: Adiyan

Age: 11

Class: 6

RollNumber: 71

Contact: info@adiyan.com
```

这里我们使用每个键来存放一条数据。我们可以毫无问题地添加任意数量的键。这赋予了我们灵活性，可以使用 PHP 关联数组来表示类似于结构体、映射和字典的数据结构。

## 多维数组

多维数组在其中包含多个数组。换句话说，它是数组的数组。在本书中，我们将在不同示例中使用多维数组，因为它们是存储图和其他树型数据结构数据最流行、最高效的方式之一。让我们通过一个示例来探索 PHP 多维数组：

```
$players = [];

$players[] = ["Name" => "Ronaldo", "Age" => 31, "Country" => "Portugal", "Team" => "Real Madrid"];

$players[] = ["Name" => "Messi", "Age" => 27, "Country" => "Argentina", "Team" => "Barcelona"];

$players[] = ["Name" => "Neymar", "Age" => 24, "Country" => "Brazil", "Team" => "Barcelona"];

$players[] = ["Name" => "Rooney", "Age" => 30, "Country" => "England", "Team" => "Man United"];

foreach($players as $index => $playerInfo) {

    echo "Info of player # ".($index+1)."\n";

    foreach($playerInfo as $key => $value) {

        echo $key.": ".$value."\n";

    }

    echo "\n";

}
```

我们刚才看到的示例是一个二维数组的例子。因此，我们使用两个 `foreach` 循环来迭代这个二维数组。这是代码的输出：

```
Info of player # 1

Name: Ronaldo

Age: 31

Country: Portugal

Team: Real Madrid

Info of player # 2

Name: Messi

Age: 27

Country: Argentina

Team: Barcelona

Info of player # 3

Name: Neymar

Age: 24

Country: Brazil

Team: Barcelona

Info of player # 4

Name: Rooney

Age: 30

Country: England

Team: Man United
```

我们可以根据需要使用 PHP 创建 n 维数组，但必须记住一点：维度越多，结构就越复杂。人类通常只能想象三维，因此为了拥有三维以上的数组，我们必须对数组在多维空间中的工作原理有扎实的理解。

我们在 PHP 中可以将数值数组和关联数组作为单个数组一起使用。但在这种情况下，我们必须非常小心地选择正确的方式来遍历数组元素。在这种情况下，`foreach` 将比 `for` 或 `while` 循环是更好的选择。

## 将数组用作灵活的存储
