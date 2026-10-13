
在 `push` 方法中，我们执行与 `pop` 相反的操作。首先，我们检查栈是否已满。如果未满，我们使用 PHP 的 `array_push` 函数将字符串 `item` 添加到栈的末尾。如果栈已满，我们抛出 SPL 的 `OverFlowException`。`top` 方法返回栈顶元素。`isEmpty` 方法检查栈是否为空。

由于我们遵循 PHP 7 标准，因此在方法层面使用了标量类型声明和返回类型声明。

为了使用我们刚刚实现的栈类，我们需要构思一个可以使用所有这些操作的示例。让我们编写一个小程序来创建一个书籍栈。代码如下：

```
try { 

    $programmingBooks = new Books(10); 

    $programmingBooks->push("Introduction to PHP7"); 

    $programmingBooks->push("Mastering JavaScript"); 

    $programmingBooks->push("MySQL Workbench tutorial"); 

    echo $programmingBooks->pop()."\n"; 

    echo $programmingBooks->top()."\n"; 

} catch (Exception $e) { 

    echo $e->getMessage(); 

}
```

我们创建了一个书籍栈实例，用于存放编程书籍标题。我们执行了三次 `push` 操作。最后插入的书名是 `"MySQL Workbench tutorial"`。如果在三次 `push` 操作后执行 `pop`，将返回该书名。之后，`top` 将返回 `"Mastering JavaScript"`，它在执行 `pop` 操作后成为新的栈顶元素。我们将整段代码包裹在 `try...catch` 块中，以便处理溢出和下溢抛出的异常。上述代码将产生以下输出：

```
MySQL Workbench tutorial

Mastering JavaScript
```

现在让我们关注刚才完成的各种栈操作的复杂度。

## 理解栈操作的复杂度

以下是不同栈操作的时间复杂度。在最坏情况下，栈操作的时间复杂度如下：

| **操作** | **时间复杂度** |
| --- | --- |
| pop | `O(1)` |
| push | `O(1)` |
| top | `O(1)` |
| isEmpty | `O(1)` |

由于栈始终在一端操作并记录栈顶位置，如果我们想在栈中搜索某个项目，意味着必须遍历整个列表。访问栈中的特定项目也是同理。虽然不建议将栈用于此类操作，但如果必须这样做，必须记住其时间复杂度高于常规栈操作。

| **操作** | **时间复杂度** |
| --- | --- |
| 访问 | `O(n)` |
| 搜索 | `O(n)` |

栈的空间复杂度始终为 `O(n)`。

到目前为止，我们已经了解了如何使用 PHP 数组及其内置函数 `array_pop` 和 `array_push` 实现栈。但我们也可以忽略内置函数，使用手动数组操作实现，或者使用 `array_shift` 和 `array_unshift` 内置函数。

## 使用链表实现栈

在 [第 3 章](#text00065.html) *使用链表* 中，我们学习了如何实现链表。我们了解到在链表中可以在末尾插入节点、从末尾移除节点、在列表中间插入、在开头插入等。如果考虑单链表数据结构的“在末尾插入”和“在末尾移除”操作，我们可以轻松实现类似栈的功能。因此，让我们使用上一章的 `LinkedList` 类来实现栈。代码如下：

```
class BookList implements Stack { 



    private $stack; 



    public function __construct() { 

      $this->stack = new LinkedList(); 

    }



    public function pop(): string { 



      if ($this->isEmpty()) { 

          throw new UnderflowException('Stack is empty'); 

      } else { 

          $lastItem = $this->top(); 

          $this->stack->deleteLast(); 

          return $lastItem; 

      } 

    } 



    public function push(string $newItem) { 



      $this->stack->insert($newItem); 

    } 





public function top(): string { 

  return $this->stack->getNthNode($this->stack->getSize())->data; 

} 



    public function isEmpty(): bool { 

      return $this->stack->getSize() == 0; 

    } 

}
```

让我们逐块分析代码以理解其工作原理。从顶部开始，我们可以看到在 `constructor` 方法中，我们创建了一个新的 `LinkedList` 对象并将其赋值给 `stack` 属性，而不是像前一个示例那样使用数组。我们假设 `LinkedList` 类已自动加载，或文件已包含在脚本中。现在让我们关注 `push` 操作。`push` 操作非常简单。我们只需在链表中插入一个新节点。由于链表没有大小限制，我们这里不检查溢出。

在我们的链表实现中，没有显示最后一个节点的方法。我们曾插入新的最后节点并移除之前的最后一个节点，但在这里，我们需要在不删除的情况下获取最后一个节点的值。为了实现该功能（即栈的 `top` 操作），我们可以利用 `LinkedList` 实现中的 `getNthNode` 方法和 `getSize` 方法。这样我们可以获取节点。但必须记住一点：我们需要的是节点的字符串值，而不是完整的节点对象。这就是为什么我们返回节点的 `data` 属性。

与 `top` 操作类似，`pop` 操作也需要在从列表中移除最后一个节点之前返回其数据。为了实现这一点，我们使用 `LinkedList` 类的 `top()` 方法和 `deleteLast()` 方法。现在让我们运行一个示例代码，使用这个新实现的 `BookList` 类进行栈操作。代码如下：

```
try { 

    $programmingBooks = new BookList(); 

    $programmingBooks->push("Introduction to PHP7"); 

    $programmingBooks->push("Mastering JavaScript"); 

    $programmingBooks->push("MySQL Workbench tutorial"); 

    echo $programmingBooks->pop()."\n"; 

    echo $programmingBooks->pop()."\n"; 

    echo $programmingBooks->top()."\n"; 

} catch (Exception $e) { 

    echo $e->getMessage(); 

}
```

这看起来与上一个运行的示例非常相似，但这里我们尝试执行两次 `pop` 操作，然后执行一次 `top` 操作。因此输出将如下所示：

```
MySQL Workbench tutorial

Mastering JavaScript

Introduction to PHP7
```

如果我们了解栈的基本行为及其实现方式，就可以使用数组、链表、双向链表来实现栈。既然我们已经看过数组和链表的实现，现在将探索 SPL 对栈的实现，它实际上使用了双向链表。

## 使用 SPL 中的 SplStack 类

如果我们不想自己实现栈，可以使用 SPL 现有的栈实现。它非常易用，只需编写极少的代码。正如我们所知，`SplStack` 使用 `SplDoublyLinkedList`。它拥有 `push`、`pop`、向前移动、向后移动、`shift`、`unshift` 等所有可能的操作。为了实现我们之前看到的相同示例，我们只需编写以下代码：

```
$books = new SplStack(); 

$books->push("Introduction to PHP7"); 

$books->push("Mastering JavaScript"); 

$books->push("MySQL Workbench tutorial"); 

echo $books->pop() . "\n"; 

echo $books->top() . "\n"; 
```

是的，使用 `SplStack` 类构建栈就是这么简单。由我们决定是使用 PHP 数组、链表，还是像 `SplStack` 这样的内置类来实现。

## 栈的实际应用
