
# 实现可迭代的链表

```
class LinkedList implements Iterator { 
} 
```

现在，让我们实现这五个新方法，使我们的链表对象可迭代。这五个方法非常直接且易于实现。代码如下：

```
public function current() { 
    return $this->_currentNode->data; 
} 

public function next() { 
    $this->_currentPosition++; 
    $this->_currentNode = $this->_currentNode->next; 
} 

public function key() { 
    return $this->_currentPosition; 
} 

public function rewind() { 
    $this->_currentPosition = 0; 
    $this->_currentNode = $this->_firstNode; 
} 

public function valid() { 
    return $this->_currentNode !== NULL; 
} 
```

现在，我们拥有了一个可迭代的列表。这意味着现在我们可以使用 `foreach` 循环或任何其他我们希望遵循的迭代过程来遍历我们的链表对象。因此，如果我们编写以下代码，将看到所有书名：

```
foreach ($BookTitles as $title) { 
    echo $title . "\n"; 
}
```

另一种方法是使用可迭代接口中的 `rewind()`、`valid()`、`next()` 和 `current()` 方法。它将产生与前面代码相同的输出：

```
for ($BookTitles->rewind(); $BookTitles->valid(); $BookTitles->next()) { 
    echo $BookTitles->current() . "\n"; 
}
```

# 构建循环链表

构建循环链表并不像其名称听起来那么难。到目前为止，我们已经看到在末尾添加新节点非常简单；我们将最后一个节点的 `next` 引用设置为 `NULL`。在循环链表中，最后一个节点的 `next` 引用实际上会指向第一个节点，从而创建一个循环列表。让我们编写一个简单的循环链表，其中节点将插入到列表末尾：

```
class CircularLinkedList { 
    private $_firstNode = NULL; 
    private $_totalNode = 0; 

    public function insertAtEnd(string $data = NULL) { 
        $newNode = new ListNode($data); 
        if ($this->_firstNode === NULL) { 
            $this->_firstNode = &$newNode; 
        } else { 
            $currentNode = $this->_firstNode; 
            while ($currentNode->next !== $this->_firstNode) { 
                $currentNode = $currentNode->next; 
            } 
            $currentNode->next = $newNode; 
        } 
        $newNode->next = $this->_firstNode; 
        $this->_totalNode++; 
        return TRUE; 
    } 
}
```

如果我们仔细观察前面的代码，它看起来完全像我们的单向链表实现。唯一的区别是我们不检查列表的末尾，而是确保当前节点不与第一个节点相同。此外，在以下代码行中，我们将新创建节点的 `next` 引用赋值为列表的第一个节点：

```
$newNode->next = $this->_firstNode; 
```

当我们实现这一点时，新节点被添加到列表的后端。我们所需要做的就是将新节点的 `next` 引用设置为列表中的第一个节点。通过这样做，我们实际上创建了一个循环链表。我们必须确保不会陷入无限循环。这就是为什么我们将 `$currentNode->next` 与 `$this->_firstNode` 进行比较。当我们显示循环链表中的所有元素时，同样的原则也适用。我们需要确保在显示标题时不会陷入无限循环。以下是显示循环链表中所有标题的代码：

```
public function display() { 
    echo "Total book titles: " . $this->_totalNode . "\n"; 
    $currentNode = $this->_firstNode; 
    while ($currentNode->next !== $this->_firstNode) { 
        echo $currentNode->data . "\n"; 
        $currentNode = $currentNode->next; 
    } 
    if ($currentNode) { 
        echo $currentNode->data . "\n"; 
    } 
}
```

到目前为止，我们已经构建了一个单向链表并实现了一个循环链表。现在，我们将使用 PHP 实现一个双向链表。

# 在 PHP 中实现双向链表

我们已经从双向链表的定义中知道，双向链表节点将有两个链接：一个指向下一个节点，另一个指向前一个节点。此外，当我们添加新节点或删除新节点时，我们需要为每个受影响的节点设置 `next` 和 `prev` 两个引用。我们在单向链表实现中看到了一种不同的方法，那里我们没有跟踪最后一个节点，因此每次都必须使用迭代器来到达最后一个节点。这一次，我们将跟踪最后一个节点，以及我们的插入和删除操作，以确保我们的插入、删除和末端操作具有 `O(1)` 复杂度。

以下是带有两个链接指针的新节点类的样子，随后是双向链表类的基本结构：

```
class ListNode {
    public $data = NULL; 
    public $next = NULL; 
    public $prev = NULL; 

    public function __construct(string $data = NULL) {
        $this->data = $data;
    }
}

class DoublyLinkedList {
    private $_firstNode = NULL;
    private $_lastNode = NULL;
    private $_totalNode = 0;
}
```

在下一节中，我们将探讨双向链表的不同操作，以便我们了解单向链表和双向链表之间的基本区别。

# 双向链表操作

我们将在双向链表实现中探讨以下操作。虽然它们听起来与单向链表中使用的操作相似，但它们的实现有重大区别：

*   在第一个节点处插入
*   在最后一个节点处插入
*   在特定节点之前插入
*   在特定节点之后插入
*   删除第一个节点
*   删除最后一个节点
*   搜索并删除一个节点
*   正向显示列表
*   反向显示列表

# 在第一个节点处插入

当我们在前端或头部添加节点时，我们必须检查列表是否为空。如果列表为空，第一个节点和最后一个节点都将指向新创建的节点。然而，如果列表已经有一个头节点，则必须执行以下操作：

1.  创建新节点。
2.  将新节点设为第一个节点或头节点。
3.  将之前的头节点或第一个节点作为 `next`，使其跟随新创建的第一个节点。
4.  将之前第一个节点的 `prev` 链接指向新的第一个节点。

代码如下：

```
public function insertAtFirst(string $data = NULL) {
    $newNode = new ListNode($data);
    if ($this->_firstNode === NULL) {
        $this->_firstNode = &$newNode;
        $this->_lastNode = $newNode; 
    } else {
        $currentFirstNode = $this->_firstNode; 
        $this->_firstNode = &$newNode; 
        $newNode->next = $currentFirstNode; 
        $currentFirstNode->prev = $newNode; 
    }
    $this->_totalNode++; 
    return TRUE;
}
```

# 在最后一个节点处插入

由于我们现在正在跟踪最后一个节点，因此在末尾插入新节点会更容易。首先，我们需要检查列表是否不为空。如果为空，则新节点同时成为第一个和最后一个节点。然而，如果列表已经有一个最后一个节点，则必须执行以下操作：

1.  创建新节点。
2.  将新节点设为最后一个节点。
3.  将之前的最后一个节点作为当前最后一个节点的 `prev` 链接。
4.  将之前最后一个节点的 `next` 链接指向新最后一个节点的 `prev` 链接。

代码如下：
