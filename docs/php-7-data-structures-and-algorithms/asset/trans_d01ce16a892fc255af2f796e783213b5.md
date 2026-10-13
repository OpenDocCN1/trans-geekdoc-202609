
# AgentQueue 实现

```php
class AgentQueue implements Queue { 

    private $limit; 

    private $queue; 

    public function __construct(int $limit = 20) { 
        $this->limit = $limit; 
        $this->queue = new LinkedList(); 
    } 

    public function dequeue(): string { 
        if ($this->isEmpty()) { 
            throw new UnderflowException('Queue is empty'); 
        } else { 
            $lastItem = $this->peek(); 
            $this->queue->deleteFirst(); 
            return $lastItem; 
        } 
    } 

    public function enqueue(string $newItem) { 
        if ($this->queue->getSize() < $this->limit) { 
            $this->queue->insert($newItem); 
        } else { 
            throw new OverflowException('Queue is full'); 
        } 
    } 

    public function peek(): string { 
        return $this->queue->getNthNode(1)->data; 
    } 

    public function isEmpty(): bool { 
        return $this->queue->getSize() == 0; 
    } 
}
```

---

> 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

---

# 使用 SPL 的 SplQueue 类

如果我们不想花费精力实现队列功能，且对内置解决方案感到满意，可以使用 `SplQueue` 类满足基本的队列需求。需要注意一点：`SplQueue` 类中没有 `peek` 函数。我们必须使用 `bottom()` 函数来获取队列的第一个元素。以下是使用 `SplQueue` 实现 `AgentQueue` 的简单示例：

```php
$agents = new SplQueue(); 

$agents->enqueue("Fred"); 
$agents->enqueue("John"); 
$agents->enqueue("Keith"); 
$agents->enqueue("Adiyan"); 
$agents->enqueue("Mikhael"); 

echo $agents->dequeue()."\n"; 
echo $agents->dequeue()."\n"; 
echo $agents->bottom()."\n";
```

---

# 理解优先队列

优先队列是一种特殊的队列，元素的插入和移除基于其优先级。在编程领域，优先队列的用途非常广泛。例如，假设我们有一个大型的邮件队列系统，通过队列系统发送月度通讯。如果我们需要使用相同的队列功能向用户发送一封紧急邮件怎么办？由于普通队列的原则是在末尾添加元素，发送该消息的过程将会被严重延迟。为了解决这个问题，我们可以使用优先队列。在这种情况下，我们为每个节点分配一个优先级，并根据该优先级进行排序。优先级较高的元素会移至列表顶端，并优先出队。

构建优先队列主要有两种方法。

## 有序序列

如果我们为优先队列规划有序序列，它可以是升序或降序。有序序列的优点是我们可以快速查找最大值或移除最大优先级元素，因为可以使用 `O(1)` 复杂度找到它。但插入将耗费更多时间，因为我们必须检查队列中的每个元素，以根据其优先级将元素放在正确的位置。

## 无序序列

无序序列不要求我们遍历每个队列元素来放置新添加的元素。它始终按照普通队列的原则添加到后端。因此，我们可以用 `O(1)` 复杂度实现入队操作。但如果我们想查找或移除最高优先级元素，则必须遍历每个元素来找到正确的那个。因此，它不利于搜索。

现在我们将编写代码，使用链表实现基于有序序列的优先队列。

---

# 使用链表实现优先队列

到目前为止，我们看到的链表仅使用一个值，即节点数据。现在我们需要传递另一个值作为优先级。为了实现这一点，我们需要修改 `ListNode` 的实现：

```php
class ListNode {

    public $data = NULL; 
    public $next = NULL;
    public $priority = NULL;

    public function __construct(string $data = NULL, int $priority = NULL) { 
        $this->data = $data;
        $this->priority = $priority;
    }
}
```

现在节点同时包含数据和优先级。为了允许在插入操作期间考虑此优先级，我们还需要更改 `LinkedList` 类中 `insert()` 的实现。以下是修改后的实现：

```php
public function insert(string $data = NULL, int $priority = NULL) { 
    $newNode = new ListNode($data, $priority); 
    $this->_totalNode++; 

    if ($this->_firstNode === NULL) { 
        $this->_firstNode = &$newNode; 
    } else { 
        $previous = $this->_firstNode; 
        $currentNode = $this->_firstNode; 
        while ($currentNode !== NULL) { 
            if ($currentNode->priority < $priority) { 
                if ($currentNode == $this->_firstNode) { 
                    $previous = $this->_firstNode; 
                    $this->_firstNode = $newNode; 
                    $newNode->next = $previous; 
                    return; 
                } 
                $newNode->next = $currentNode; 
                $previous->next = $newNode; 
                return; 
            } 
            $previous = $currentNode; 
            $currentNode = $currentNode->next; 
        } 
    } 
    return TRUE; 
}
```

正如我们所见，`insert` 方法已更改为在插入操作期间同时接收数据和优先级。像往常一样，第一步是创建一个新节点并增加节点计数。插入有三种可能性：

*   列表为空，因此新节点是第一个节点。
*   列表不为空，但新项目具有最高优先级，因此它成为第一个节点，之前的第一个节点跟随其后。
*   列表不为空且优先级不是最高，因此它在列表内部插入新节点，或者可能在列表末尾。

在我们的实现中，我们考虑了所有三种可能性。因此，最高优先级的项目始终位于列表开头。现在让我们使用这段新代码运行 `AgentQueue` 实现，如下例所示：

```php
try { 
    $agents = new AgentQueue(10); 
    $agents->enqueue("Fred", 1); 
    $agents->enqueue("John", 2); 
    $agents->enqueue("Keith", 3); 
    $agents->enqueue("Adiyan", 4); 
    $agents->enqueue("Mikhael", 2); 
    $agents->display(); 
    echo $agents->dequeue()."\n"; 
    echo $agents->dequeue()."\n"; 
} catch (Exception $e) { 
    echo $e->getMessage(); 
}
```

如果没有优先级，队列应该是 `Fred`、`John`、`Keith`、`Adiyan` 和 `Mikhael`。但由于我们给列表添加了优先级，输出结果为：

```
Adiyan
Keith
John
Mikhael
Fred
```

由于 `Adiyan` 具有最高优先级，它被放置在队列开头，尽管它是在第四位插入队列的。

---

# 使用 SplPriorityQueue 实现优先队列

PHP 已经通过 SPL 内置了对优先队列实现的支持。我们可以使用 `SplPriorityQueue` 类来实现优先队列。以下是使用链表的前一个示例，但这次我们选择 SPL：

```php
class MyPQ extends SplPriorityQueue { 
    public function compare($priority1, $priority2) { 
        return $priority1 <=> $priority2; 
    }
}

$agents = new MyPQ();

$agents->insert("Fred", 1); 
$agents->insert("John", 2);
$agents->insert("Keith", 3);
$agents->insert("Adiyan", 4);
$agents->insert("Mikhael", 2);

// 提取模式
$agents->setExtractFlags(MyPQ::EXTR_BOTH); 

// 移至顶部
$agents->top();

while ($agents->valid()) {
    $current = $agents->current();
    echo $current['data'] . "\n";
    $agents->next();
}
```
