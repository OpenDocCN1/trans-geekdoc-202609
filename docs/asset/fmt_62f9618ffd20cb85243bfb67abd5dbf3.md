
正如我们所见，我们从通用的 `mid = (low+high)/2` 公式转变为一个看起来更复杂的公式。如果搜索键更接近 `arr[high]`，该公式将返回一个较高的值；如果键更接近 `arr[low]`，则返回一个低得多的值。现在，让我们借助二分查找代码来实现这种搜索方法：

```
function interpolationSearch(array $arr, int $key): int { 
    $low = 0; 
    $high = count($arr) - 1; 
    while ($arr[$high] != $arr[$low] && $key >= $arr[$low] && $key <= $arr[$high]) { 
        $mid = intval($low + (($key - $arr[$low]) * ($high - $low) / ($arr[$high] - $arr[$low]))); 
        if ($arr[$mid] < $key) 
            $low = $mid + 1; 
        else if ($key < $arr[$mid]) 
            $high = $mid - 1; 
        else 
            return $mid; 
    } 
    if ($key == $arr[$low]) 
        return $low; 
    else 
        return -1; 
}
```

这里，我们以一种不同的方式进行计算。虽然它需要更多的计算步骤，但好的一面是，如果列表是均匀分布的，那么该算法的平均复杂度为 `O(log (log n))`，这比二分查找的 `O(log n)` 复杂度好得多。此外，如果键的分布不均匀，我们必须小心。在这种情况下，插值搜索的性能可能会下降。

现在，我们将探索另一种称为指数搜索的二分查找变体，它可以改进算法。

## 指数搜索

在二分查找中，我们在整个列表中搜索给定的键。指数搜索通过决定搜索的下界和上界来改进二分查找，这样我们就不会搜索整个列表。它减少了查找元素所需的比较次数。搜索分为以下两个步骤进行：

1.  我们通过寻找第一个使得 `2^k` 的值大于搜索项的指数 `k` 来确定边界大小。现在，`2^k` 和 `2^(k-1)` 分别成为上界和下界。

2.  对边界 `2^k` 和 `2^(k-1)` 应用二分查找算法。

现在，让我们使用递归的 `binarySearch` 函数来实现指数搜索：

```
function exponentialSearch(array $arr, int $key): int { 
    $size = count($arr); 
    if ($size == 0) 
        return -1; 
    $bound = 1; 
    while ($bound < $size && $arr[$bound] < $key) { 
        $bound *= 2; 
    } 
    return binarySearch($arr, $key, intval($bound / 2), min($bound, $size)); 
}
```

在这里，在第一步中，我们采取 `i` 步来确定边界。因此，算法的时间复杂度为 `O(log i)`。我们必须记住，这里的 `i` 远小于 `n`。然后，我们在 `2^j` 到 `2^(j-1)` 的边界内进行二分查找，其中 `j = log i`。我们知道二分查找的时间复杂度为 `O(log n)`，其中 `n` 是列表的大小。然而，由于我们进行的是较小范围的边界搜索，实际搜索的大小为 `2^(log i) - 2^(log i) - 1 = 2^(log i - 1)`。因此，该边界的复杂度为 `log(2^(log i - 1)) = log(i) - 1 = O(log i)`。

因此，指数搜索的复杂度如下：

| 最佳时间复杂度 | `O(1)` |
| --- | --- |
| 最坏时间复杂度 | `O(log i)` |
| 平均时间复杂度 | `O(log i)` |
| 空间复杂度（最坏情况） | `O(1)` |

## 使用哈希表搜索

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

## 树搜索

搜索层次数据的最佳方法之一是创建一棵搜索树。在第 6 章 *理解并实现树* 中，我们看到了如何构建二叉搜索树并提高搜索效率。我们还发现了遍历树的不同方法。现在，我们将探索搜索树结构的两种最流行的方法，通常称为广度优先搜索（BFS）和深度优先搜索（DFS）。

## 广度优先搜索

在树结构中，根节点连接到其子节点，每个子节点都可以表示为一棵树。我们已经在第 6 章 *理解并实现树* 中看到了这一点。在广度优先搜索（通常称为 BFS）中，我们从一个节点（通常是根节点）开始，首先访问所有相邻或邻居节点，然后再访问其他邻居节点。换句话说，在应用 BFS 时，我们必须逐层移动。因为我们是逐层搜索，所以这种技术称为广度优先搜索。在下面的树结构中，我们可以使用 BFS：

![](img/Image00065.jpg)

对于这棵树，BFS 将按以下顺序访问节点：![](img/Image00066.jpg)

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

## 实现广度优先搜索

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

我们在 `Tree` 类中实现了 `BFS()` 方法。我们将根节点作为广度优先搜索的起点。这里我们有两个队列：一个用于保存我们需要访问的节点，另一个用于保存我们已经访问过的节点。我们还在方法结束时返回已访问队列。现在让我们模仿本节开头看到的树。我们想要像图中所示的树那样放置数据，并检查 BFS 是否真的返回我们预期的模式：![](img/Image00066.jpg)：

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

我们在这里通过创建节点并将它们附加到根节点和其他节点来构建整个树结构。树构建完成后，我们调用 `BFS` 方法以查找完整的遍历序列。最后的 `while` 循环打印我们访问过的节点序列。以下是前面代码的输出：

```
8
3
10
1
6
14
4
7
13
```

我们得到了预期的结果。现在，如果我们想要搜索以查找某个节点是否存在，可以为 `$current` 节点值添加一个简单的条件检查。如果匹配，则可以返回已访问队列。

BFS 的最坏时间复杂度为 `O(|V| + |E|)`，其中 `V` 是顶点或节点的数量，`E` 是节点之间的边或连接数量。对于空间复杂度，最坏情况为 `O(|V|)`。

图的 BFS 类似，但有一个细微差别。由于图可以是循环的（可以形成环），我们需要确保不会反复访问同一个节点而导致无限循环。为了避免重复访问图节点，我们必须记录已访问的节点。对于标记已访问节点，我们可以使用队列，也可以使用图着色算法。我们将在下一章探讨这一点。

---

## 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

---

## 深度优先搜索

深度优先搜索（DFS）是一种搜索技术，我们从一个节点开始搜索，并通过分支尽可能深地向目标节点推进。DFS 与 BFS 不同，我们尝试先深入挖掘而不是先广泛扩散。DFS 垂直增长，当到达分支末端时回溯，并移动到下一个可用的相邻节点，直到搜索结束。我们可以使用上一节中的相同树图像，如下所示：

![](img/Image00067.jpg)

如果在此处应用 DFS，遍历顺序将为 ![](img/Image00068.jpg)。我们从根节点开始，然后访问第一个子节点 `3`。然而，不同于 BFS 转向 `10`，我们将探索 `3` 的子节点，并重复此过程直到到达分支底部。在 BFS 中，我们采用了迭代方法。对于 DFS，我们将采用递归方法。现在让我们编写 DFS 的伪代码：

```
procedure DFS(Node current)       
     for each node v that is childnode of current  
        DFS(v) 
     end for each 
end procedure 
```

## 实现深度优先搜索

DFS 的伪代码看起来很简单。为了跟踪节点访问序列，我们需要使用一个队列，它将在 `Tree` 类中跟踪节点。以下是带有递归 DFS 的 `Tree` 类实现：

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
    public $visited; 

    public function __construct(TreeNode $node) { 
      $this->root = $node; 
      $this->visited = new SplQueue; 
    } 

    public function DFS(TreeNode $node) { 
      $this->visited->enqueue($node); 

      if($node->children){ 
          foreach ($node->children as $child) { 
            $this->DFS($child); 
          } 
      } 
    }
}
```

正如我们所见，我们在 `Tree` 类中添加了一个额外的属性 `$visited` 来跟踪已访问的节点。当我们调用 `DFS` 方法时，将节点添加到队列中。现在，如果我们使用上一节中的相同树结构，并仅添加 DFS 调用和获取访问部分，代码将如下所示：
