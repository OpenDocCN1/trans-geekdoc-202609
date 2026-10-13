

## 构建二叉搜索树

正如我们所知，一个节点可以有两个子节点，并且本身可以用递归方式表示一棵树。我们将定义节点类使其功能更完善，并具备查找最大值、最小值、前驱和后继所需的所有功能。稍后，我们还将为节点添加删除功能。让我们看看 BST 节点类的以下代码：

```php
class Node { 



    public $data; 

    public $left; 

    public $right; 



    public function __construct(int $data = NULL) { 

       $this->data = $data; 

       $this->left = NULL; 

       $this->right = NULL; 

    } 



    public function min() { 

       $node = $this; 



       while($node->left) { 

         $node = $node->left; 

       } 

         return $node; 

    } 



    public function max() { 

         $node = $this; 



         while($node->right) { 

            $node = $node->right; 

         } 

         return $node; 

    } 



    public function successor() { 

         $node = $this; 

         if($node->right) 

               return $node->right->min(); 

         else 

               return NULL; 

    } 



    public function predecessor() { 

         $node = $this; 

         if($node->left) 

               return $node->left->max(); 

         else 

               return NULL;

    }



}
```

节点类看起来很简单，且与上一节定义的步骤相符。每个新节点都是叶子节点，因此在创建时没有左节点或右节点。正如我们所知，可以在节点的左侧找到较小的值以获取最小值，我们到达最左侧的节点以获取最小值，到达最右侧的节点以获取最大值。对于 `successor()`，我们从给定节点的右子树中查找节点的最小值；对于 `predecessor()` 部分，则从左子树中查找节点的最大值。

现在，我们需要一个 `BST` 结构来向树中添加新节点，以便遵循插入原则：

```php
class BST { 



    public $root = NULL; 



    public function __construct(int $data) { 

         $this->root = new Node($data); 

    } 



    public function isEmpty(): bool { 

         return $this->root === NULL; 

    } 



    public function insert(int $data) { 



         if($this->isEmpty()) { 

               $node = new Node($data); 

               $this->root = $node; 

               return $node; 

         }  



    $node = $this->root; 



    while($node) { 

      if($data > $node->data) { 

          if($node->right) { 

            $node = $node->right; 

          } else { 

            $node->right = new Node($data); 

            $node = $node->right; 

            break; 

          } 



      } elseif($data < $node->data) { 

          if($node->left) { 

            $node = $node->left; 

          } else { 

            $node->left = new Node($data); 

            $node = $node->left; 

            break; 

          } 

      } else { 

            break; 

      } 

    } 

    return $node; 



    } 



    public function traverse(Node $node) { 

      if ($node) { 

          if ($node->left) 

            $this->traverse($node->left); 

          echo $node->data . "\n"; 

          if ($node->right)

            $this->traverse($node->right);

      }

    }



}
```

如果我们查看前面的代码，`BST` 类只有一个属性，用于标记根节点。在构造 `BST` 对象时，我们传入单个值，该值将作为树的根节点。`isEmpty()` 方法检查树是否为空。`insert()` 方法允许我们在树中添加新节点。逻辑检查值是大于还是小于根节点，并遵循 BST 原则将新节点插入正确位置。如果值已存在，我们将忽略它，避免重复添加到树中。

我们还有一个 `traverse()` 方法来遍历节点，并以有序格式查看数据（先左节点，然后是当前节点，最后是右节点值）。它有一个特定的名称，我们将在下一节探讨。现在，让我们准备一个示例代码来使用 `BST` 类，添加一些数字，并检查数字是否以正确的方式存储。如果 `BST` 工作正常，那么 `traverse()` 将显示一个排序后的数字列表，无论我们如何插入它们：

```php
$tree = new BST(10); 



$tree->insert(12); 

$tree->insert(6); 

$tree->insert(3); 

$tree->insert(8); 

$tree->insert(15); 

$tree->insert(13); 

$tree->insert(36); 



$tree->traverse($tree->root);
```

如果我们查看前面的代码，`10` 是我们的根节点，然后我们随机添加了新节点。最后，我们调用了 `traverse()` 方法来显示节点以及它们在二叉搜索树中的存储方式。以下是前面代码的输出：

```
3



6



8



10



12



13



15



36
```

实际的树在视觉上看起来像这样，这与 `BST` 实现的预期结果完全一致：

![](Image00051.jpg)

现在，我们将在 `BST` 类中添加搜索部分。我们想要查找值是否存在于树中。如果值不在我们的 `BST` 中，它将返回 false，否则返回该节点。以下是简单的搜索功能：

```php
public function search(int $data) { 

  if ($this->isEmpty()) { 

      return FALSE; 

  } 



  $node = $this->root; 



  while ($node) { 

      if ($data > $node->data) { 

        $node = $node->right; 

      } elseif ($data < $node->data) { 

        $node = $node->left; 

      } else { 

        break; 

      } 

  } 



  return $node; 

}
```

在前面的代码中，我们可以看到我们正在从节点开始在树中搜索值，并迭代地遵循树的左侧或右侧。如果未找到具有该值的节点，则返回节点的叶子，即 `NULL`。我们可以这样测试代码：

```php
echo $tree->search(14) ? "Found" : "Not Found";

echo "\n";

echo $tree->search(36) ? "Found" : "Not Found";
```

这将产生以下输出。由于 `14` 不在我们的列表中，它将显示 `Not Found`，而对于 `36`，它将显示 `Found`：

```
Not Found



Found
```

现在，我们将进入编码中最复杂的部分：节点的删除。我们需要实现节点拥有零个、一个或两个子节点的每种情况。下图展示了我们删除节点时需要满足的三个条件，并确保操作后二叉搜索树仍然是二叉搜索树。当处理拥有两个子节点的节点时，我们必须小心。由于我们需要在节点之间来回移动，我们需要知道哪个节点是当前节点的父节点。因此，我们需要添加一个额外的属性来跟踪任意节点的父节点：

![](Image00052.jpg)

以下是我们添加到 `Node` 类的代码变更：

```php
    public $data;

    public $left;

    public $right;

    public $parent;



    public function __construct(int $data = NULL, Node $parent = NULL)   

     {

      $this->data = $data; 

      $this->parent = $parent; 

      $this->left = NULL; 

      $this->right = NULL; 

     }
```

此代码块现在还会在新创建的节点与其直接父节点之间建立父子关系。我们还希望将删除功能附加到单个节点上，以便我们可以找到一个节点，然后仅使用 `delete()` 方法将其移除。以下是删除功能的代码：

