
# 使用 Tarsana 和内置列表函数实现队列

我们可以使用 Tarsana 和内置的列表操作函数来实现队列。我们将使用数组来表示队列，代码如下：

```
require __DIR__ . '/vendor/autoload.php';

use Tarsana\Functional as F;

$queue = [];

$enqueue = F\append(F\__(), F\__());
$head = F\head(F\__());
$dequeue = F\tail(F\__());

$queue = $enqueue(1, $queue);
$queue = $enqueue(2, $queue);
$queue = $enqueue(3, $queue);

echo "Queue is " . F\toString($queue) . "\n";

$item = $head($queue);
$queue = $dequeue($queue);

echo "Dequeue-ed item: " . $item . "\n";
echo "Queue is " . F\toString($queue) . "\n";

$queue = $enqueue(4, $queue);

echo "Queue is " . F\toString($queue) . "\n";
```

在这里，我们使用 `append` 函数执行入队操作，使用 `head` 和 `tail` 函数分别获取队列中的第一个元素和出队。上述代码的输出如下：

```
Queue is [1, 2, 3]

Dequeue-ed item: 1

Queue is [2, 3]

Queue is [2, 3, 4]
```

# 实现树

现在，我们将重点转移到使用简单的 PHP 函数（而不是类和对象）来实现层次化数据。由于函数式编程在 PHP 中仍是一个新话题，实现层次化数据可能看起来具有挑战性且耗时。因此，我们将结合基本的函数式编程概念（如一等函数和高阶函数），使用基本的 PHP 函数来转换我们的层次化数据实现。那么，让我们来实现一棵二叉树。

我们将使用 PHP 数组和简单的基于递归函数的遍历来实现二叉树。我们只是用一个函数重写了该功能，而不是使用类。代码如下：

```
function treeTraverse(array &$tree, int $index = 0, int $level = 0, &$outputStr = "") : ?bool {

    if (isset($tree[$index])) {
        $outputStr .= str_repeat("-", $level);
        $outputStr .= $tree[$index] . "\n";

        treeTraverse($tree, 2 * $index + 1, $level + 1, $outputStr);
        treeTraverse($tree, 2 * ($index + 1), $level + 1, $outputStr);

    } else {
        return false;
    }
    return null;
}

$nodes = [];
$nodes[] = "Final";
$nodes[] = "Semi Final 1";
$nodes[] = "Semi Final 2";
$nodes[] = "Quarter Final 1";
$nodes[] = "Quarter Final 2";
$nodes[] = "Quarter Final 3";
$nodes[] = "Quarter Final 4";

$treeStr = "";
treeTraverse($nodes, 0, 0, $treeStr);
echo $treeStr;
```

如果我们查看上述代码，会发现我们只是简单地修改了遍历函数并将其转换为独立函数。这是一个纯函数，因为我们没有修改实际的输入（即 `$nodes` 变量）。我们将在每一层构建一个字符串并用于输出。现在我们可以将大多数基于类的结构转换为基于函数的结构。

---

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：** [沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

# 总结

对于 PHP 开发者来说，函数式编程相对较新，因为其前提条件的支持是在 5.4 版本中添加的。函数式编程的出现要求我们理解该范式，并在需要时编写无副作用的纯函数。PHP 对编写函数式代码有很好的支持，利用这一点，我们也可以编写函数式数据结构和算法实现，正如我们在本书中尝试展示的那样。在不久的将来，这可能有助于优化和提高我们应用程序的效率。
