
在这里，在第一步中，我们采取 `i` 步来确定边界。因此，算法的时间复杂度为 `O(log i)`。我们必须记住，这里的 `i` 远小于 `n`。然后，我们在 `2^j` 到 `2^(j-1)` 的边界内进行二分查找，其中 `j = log i`。我们知道二分查找的时间复杂度为 `O(log n)`，其中 `n` 是列表的大小。然而，由于我们进行的是较小范围的边界搜索，实际搜索的大小为 `2^(log i) - 2^(log i) - 1 = 2^(log i - 1)`。因此，该边界的复杂度为 `log(2^(log i - 1)) = log(i) - 1 = O(log i)`。

因此，指数搜索的复杂度如下：

| 最佳时间复杂度 | `O(1)` |
| --- | --- |
| 最坏时间复杂度 | `O(log i)` |
| 平均时间复杂度 | `O(log i)` |
| 空间复杂度（最坏情况） | `O(1)` |

# 使用哈希表搜索

哈希表在搜索操作方面可以是一种非常高效的数据结构。由于哈希表以关联方式存储数据，如果我们知道在哪里查找数据，就可以轻松快速地获取数据。在哈希表中，每个数据都有一个与之关联的唯一索引。如果我们知道要查看哪个索引，就可以非常容易地找到键。通常，在其他编程语言中，我们必须使用单独的哈希函数来计算用于存储值的哈希索引。哈希函数的设计目的是为相同的键生成相同的索引，并避免冲突。然而，PHP 的一个伟大特性是 PHP 数组在其底层 C 实现中本身就是一个哈希表。由于数组是动态的，我们不必担心数组的大小或因值过多而导致数组溢出。我们需要将值存储在关联数组中，以便将值与键关联。如果键是字符串或整数，键可以是值本身。让我们运行一个示例来理解使用哈希表进行搜索：

```
$arr = [];

$count = rand(10, 30);

for($i = 0; $i < $count; $i++) {
    $val = rand(1, 500);
    $arr[$val] = $val;
}

$number = 100;

if(isset($arr[$number])) {
    echo "$number found ";
} else {
    echo "$number not found";
}
```

我们刚刚构建了一个简单的随机关联数组，其中值和键相同。由于我们使用的是 PHP 数组，虽然值的范围可以是 1 到 500，但实际数组大小可以是 10 到 30 之间的任何值。如果是在其他语言中，我们将不得不构建一个大小为 501 的数组来容纳该值作为键。这就是为什么要使用哈希函数来计算索引。如果我们想，也可以使用 PHP 的内置哈希函数：

```
string hash(string $algo, string $data [, bool $raw_output = false ])
```

第一个参数接受我们想要用于哈希的算法类型。我们可以从 md5、sha1、sha256、crc32 等中选择。每种算法都会生成固定长度的哈希输出，我们可以将其用作哈希表的键。

如果我们看看搜索部分，可以看到我们实际上是直接检查关联的索引。这使得我们的搜索复杂度为 `O(1)`。在 PHP 中，即使不使用哈希函数，使用哈希表进行快速搜索也可能是有益的。不过，如果我们想，始终可以使用哈希函数。

到目前为止，我们已经介绍了基于数组和线性结构的搜索。现在我们将把重点转移到层次数据结构的搜索，例如搜索树和图。虽然我们还没有讨论图（将在下一章讨论），但我们将把重点放在树搜索上，它也可以应用于图搜索。

# 树搜索

搜索层次数据的最佳方法之一是创建一棵搜索树。在第 6 章 *理解并实现树* 中，我们看到了如何构建二叉搜索树并提高搜索效率。我们还发现了遍历树的不同方法。现在，我们将探索搜索树结构的两种最流行的方法，通常称为广度优先搜索（BFS）和深度优先搜索（DFS）。

# 广度优先搜索

在树结构中，根节点连接到其子节点，每个子节点都可以表示为一棵树。我们已经在第 6 章 *理解并实现树* 中看到了这一点。在广度优先搜索（通常称为 BFS）中，我们从一个节点（通常是根节点）开始，首先访问所有相邻或邻居节点，然后再访问其他邻居节点。换句话说，在应用 BFS 时，我们必须逐层移动。因为我们是逐层搜索，所以这种技术称为广度优先搜索。在下面的树结构中，我们可以使用 BFS：

![](Image00065.jpg)

对于这棵树，BFS 将按以下顺序访问节点：![](Image00066.jpg)

BFS 的伪代码如下所示：

```
procedure BFS(Node root)

  Q := empty queue

  Q.enqueue(root);

  while(Q != empty)
     u := Q.dequeue()

     for each node w that is childnode of u
        Q.enqueue(w)
     end for each
  end while

end procedure
```

我们可以看到，我们保留了一个队列来跟踪需要访问的节点。我们可以保留另一个队列来保存访问序列，并将其返回以显示访问顺序。现在，我们将使用 PHP 7 实现 BFS。

# 实现广度优先搜索

由于我们目前尚未详细介绍图，因此我们将 BFS 和 DFS 的实现严格限制在树结构上。此外，我们将使用第 6 章 *理解并实现树* 中看到的通用树结构（甚至不是二叉树）。我们将使用相同的 `TreeNode` 类来定义节点及其与子节点的关系。那么，现在让我们定义一个带有 BFS 功能的 `Tree` 类：

```
class TreeNode {

    public $data = NULL;
    public $children = [];

    public function __construct(string $data = NULL) {
      $this->data = $data;
    }

    public function addChildren(TreeNode $node) {
      $this->children[] = $node;
    }
}

class Tree {

    public $root = NULL;

    public function __construct(TreeNode $node) {
      $this->root = $node;
    }

    public function BFS(TreeNode $node): SplQueue {

      $queue = new SplQueue;
      $visited = new SplQueue;

      $queue->enqueue($node);

      while (!$queue->isEmpty()) {
          $current = $queue->dequeue();
          $visited->enqueue($current);

          foreach ($current->children as $child) {
            $queue->enqueue($child);
          }
      }
      return $visited;
    }
}
```

我们在 `Tree` 类中实现了 `BFS()` 方法。我们将根节点作为广度优先搜索的起点。这里我们有两个队列：一个用于保存我们需要访问的节点，另一个用于保存我们已经访问过的节点。我们还在方法结束时返回已访问队列。现在让我们模仿本节开头看到的树。我们想要像图中所示的树那样放置数据，并检查 BFS 是否真的返回我们预期的模式：![](Image00066.jpg)：

```
$root = new TreeNode("8");

$tree = new Tree($root);

$node1 = new TreeNode("3");
$node2 = new TreeNode("10");
$root->addChildren($node1);
$root->addChildren($node2);

$node3 = new TreeNode("1");
$node4 = new TreeNode("6");
$node5 = new TreeNode("14");
$node1->addChildren($node3);
$node1->addChildren($node4);
$node2->addChildren($node5);

$node6 = new TreeNode("4");
$node7 = new TreeNode("7");
$node8 = new TreeNode("13");
$node4->addChildren($node6);
$node4->addChildren($node7);
$node5->addChildren($node8);

$visited = $tree->BFS($tree->root);

while (!$visited->isEmpty()) {
  echo $visited->dequeue()->data . "\n";
}
```
