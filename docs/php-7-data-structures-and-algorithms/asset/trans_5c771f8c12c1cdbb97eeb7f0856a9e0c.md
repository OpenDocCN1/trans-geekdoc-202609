
这将产生与链表示例相同的结果。扩展我们自己的 `MyPQ` 类的额外优势在于，我们可以定义是按升序还是降序排序。在这里，我们选择降序，使用 PHP 组合比较运算符（即太空船运算符）进行排序。

大多数情况下，优先队列是使用堆实现的。当我们进入堆章节时，我们也将使用堆来实现优先队列。

# 实现循环队列

当我们使用标准队列时，每次出队一个项目，都必须重新缓冲整个队列。为了解决这个问题，我们可以使用循环队列，其中队尾后面跟着队头，形成一个圆圈。这种特殊类型的队列要求对入队和出队操作进行特殊计算，需考虑队尾、队头和队列的容量限制。循环队列始终是固定队列，也称为循环缓冲区或环形缓冲区。下图展示了循环队列的表示：

![](Image00030.jpg)

我们可以使用 PHP 数组实现循环队列。由于我们必须计算队尾和队头部分的位置，数组可用于此目的以实现高效操作。以下是一个循环队列的示例：

```
class CircularQueue implements Queue { 



    private $queue; 

    private $limit; 

    private $front = 0; 

    private $rear = 0; 



    public function __construct(int $limit = 5) { 

      $this->limit = $limit; 

      $this->queue = []; 

    } 



    public function size() { 

      if ($this->rear > $this->front) 

          return $this->rear - $this->front; 

      return $this->limit - $this->front + $this->rear; 

    } 



    public function isEmpty() { 

      return $this->rear == $this->front; 

    } 



    public function isFull() { 

      $diff = $this->rear - $this->front; 

      if ($diff == -1 || $diff == ($this->limit - 1)) 

          return true; 

      return false; 

    } 



    public function enqueue(string $item) { 

      if ($this->isFull()) { 

          throw new OverflowException("Queue is Full."); 

      } else { 

          $this->queue[$this->rear] = $item; 

          $this->rear = ($this->rear + 1) % $this->limit; 

      } 

    } 



    public function dequeue() { 

      $item = ""; 

      if ($this->isEmpty()) { 

          throw new UnderflowException("Queue is empty"); 

      } else { 

          $item = $this->queue[$this->front]; 

          $this->queue[$this->front] = NULL; 

          $this->front = ($this->front + 1) % $this->limit; 

      } 

      return $item; 

    } 



    public function peek() { 

      return $this->queue[$this->front]; 

    }



}
```

由于我们将 `0` 视为队头标记，因此队列的总大小将为 `limit - 1`。

# 创建双端队列

到目前为止，我们实现的队列都是一端用于入队（称为队尾），另一端用于出队（称为队头）。因此，通常每一端都应用于特定目的。但如果我们需要从两端进行入队和出队操作怎么办？这可以通过双端队列的概念来实现。在双端队列中，两端都可用于入队和出队操作。如果我们查看基于链表的队列实现，会发现我们可以使用链表实现进行尾部插入、头部插入、尾部删除和头部删除。如果我们基于此实现一个新的双端队列类，就能轻松达成目标。下图描绘了一个双端队列：

![](Image00031.jpg)

以下是双端队列的实现：

```
class DeQueue { 



    private $limit; 

    private $queue; 



    public function __construct(int $limit = 20) { 

      $this->limit = $limit; 

      $this->queue = new LinkedList(); 

    } 



    public function dequeueFromFront(): string { 



      if ($this->isEmpty()) { 

          throw new UnderflowException('Queue is empty'); 

      } else { 

          $lastItem = $this->peekFront(); 

          $this->queue->deleteFirst(); 

          return $lastItem; 

      } 

    } 



    public function dequeueFromBack(): string { 



      if ($this->isEmpty()) { 

          throw new UnderflowException('Queue is empty'); 

      } else { 

          $lastItem = $this->peekBack(); 

          $this->queue->deleteLast(); 

          return $lastItem; 

      } 

    } 



    public function enqueueAtBack(string $newItem) { 



      if ($this->queue->getSize() < $this->limit) { 

          $this->queue->insert($newItem); 

      } else { 

          throw new OverflowException('Queue is full'); 

      } 

    } 



    public function enqueueAtFront(string $newItem) { 



      if ($this->queue->getSize() < $this->limit) { 

          $this->queue->insertAtFirst($newItem); 

      } else { 

          throw new OverflowException('Queue is full'); 

      } 

    } 



    public function peekFront(): string { 

      return $this->queue->getNthNode(1)->data; 

    } 



    public function peekBack(): string { 

      return $this->queue->getNthNode($this->queue->getSize())->data; 

    } 



    public function isEmpty(): bool { 

      return $this->queue->getSize() == 0; 

    } 



}
```

现在我们将使用这个类来检查双端队列的操作：

```
try { 

    $agents = new DeQueue(10); 

    $agents->enqueueAtFront("Fred"); 

    $agents->enqueueAtFront("John"); 

    $agents->enqueueAtBack("Keith"); 

    $agents->enqueueAtBack("Adiyan"); 

    $agents->enqueueAtFront("Mikhael"); 

    echo $agents->dequeueFromBack() . "\n"; 

    $agents->dequeueFromFront() . "\n"; 

    echo $agents->peekFront() . "\n"; 

} catch (Exception $e) { 

    echo $e->getMessage(); 

}
```

如果我们查看前面的代码示例，首先我们在队头添加 `Fred`，然后再次在队头添加 `John`。所以序列现在是 `John`、`Fred`。接着我们在队尾添加 `Keith`，随后在队尾添加 `Adiyan`。现在序列变为 `John`、`Fred`、`Keith`、`Adiyan`。最后，我们在开头添加 `Mikhael`。所以最终序列是 `Mikhael`、`John`、`Fred`、`Keith`、`Adiyan`。

由于我们首先执行从队尾出队操作，`Adiyan` 将最先出队，然后从队头出队 `Mikhael`。新的队头 peek 将是 `John`。运行代码时的输出如下：

```
Adiyan



Mikhael



John
```

# 总结

栈和队列是最常用的数据结构之一。在未来的算法和数据结构中，我们可以以不同方式使用这些抽象数据类型。在本章中，我们学习了实现栈和队列的不同方法，以及不同类型的队列。在下一章中，我们将讨论递归——一种通过将大问题分解为较小实例来解决的特殊方法。

# 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

# 应用递归算法 - 递归

解决复杂问题总是很难。即使对于程序员来说，解决复杂问题也可能更棘手，有时需要特殊的解决方案。递归就是这样一种计算机程序员遵循的特殊方法，用于解决复杂问题。在本章中，我们将介绍递归的定义、属性、不同类型的递归以及大量示例。递归不是一个新概念；在自然界中，我们看到许多递归元素。分形展示了递归行为。下图展示了自然界中的递归：

![](Image00032.jpg)

# 理解递归
