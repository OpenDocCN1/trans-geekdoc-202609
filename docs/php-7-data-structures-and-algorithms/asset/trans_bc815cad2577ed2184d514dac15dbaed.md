
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

# 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

---

# 深度优先搜索

深度优先搜索（DFS）是一种搜索技术，我们从一个节点开始搜索，并通过分支尽可能深地向目标节点推进。DFS 与 BFS 不同，我们尝试先深入挖掘而不是先广泛扩散。DFS 垂直增长，当到达分支末端时回溯，并移动到下一个可用的相邻节点，直到搜索结束。我们可以使用上一节中的相同树图像，如下所示：

![](Image00067.jpg)

如果在此处应用 DFS，遍历顺序将为 ![](Image00068.jpg)。我们从根节点开始，然后访问第一个子节点 **3**。然而，不同于 BFS 转向 **10**，我们将探索 **3** 的子节点，并重复此过程直到到达分支底部。在 BFS 中，我们采用了迭代方法。对于 DFS，我们将采用递归方法。现在让我们编写 DFS 的伪代码：

```
procedure DFS(Node current)       
     for each node v that is childnode of current  
        DFS(v) 
     end for each 
end procedure 
```

# 实现深度优先搜索

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

```
try { 
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

    $tree->DFS($tree->root); 

    $visited = $tree->visited; 
    while (!$visited->isEmpty()) { 
      echo $visited->dequeue()->data . "\n"; 
    } 
} catch (Exception $e) { 
    echo $e->getMessage(); 
}
```

由于 `DFS` 不返回任何内容，我们使用类属性 `visited` 来获取队列，以便显示访问节点的序列。如果在控制台运行此程序，将得到以下输出：

```
8
3
1
6
4
7
10
14
13
```

结果与预期相符。如果我们需要 DFS 的迭代解决方案，必须记住需要使用栈而不是队列来跟踪下一个要访问的节点。然而，由于栈遵循后进先出（LIFO）原则，对于我们提到的图像，输出将与我们最初的想法不同。以下是使用迭代方法的实现：

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

    public function DFS(TreeNode $node): SplQueue { 
      $stack = new SplStack;
      $visited = new SplQueue;

      $stack->push($node);

      while (!$stack->isEmpty()) { 
          $current = $stack->pop(); 
          $visited->enqueue($current); 
          foreach ($current->children as $child) { 
            $stack->push($child); 
          } 
      } 
      return $visited; 
    }
}

try {
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

    $visited = $tree->DFS($tree->root); 

    while (!$visited->isEmpty()) { 
      echo $visited->dequeue()->data . "\n"; 
    } 
} catch (Exception $e) { 
    echo $e->getMessage(); 
}
```
