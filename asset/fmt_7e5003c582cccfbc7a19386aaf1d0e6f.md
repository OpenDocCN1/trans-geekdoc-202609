
```php
$newNode = new ListNode($data);

if ($this->_firstNode === NULL) {
    $this->_firstNode = &$newNode;
}
```

从前面的代码片段中我们可以看到，我们正在用数据创建一个新节点，并将该节点对象命名为 `$newNode`。之后，它检查 `$_firstNode` 是否为 `NULL`。如果是 `NULL`，则列表为空。如果为空，则将 `$newNode` 对象赋值给 `$_firstNode` 属性。现在，`insert` 方法的剩余部分代表我们的第二个条件，即列表不为空，我们必须在列表末尾添加新项目：

```php
$currentNode = $this->_firstNode;

while ($currentNode->next !== NULL) {
    $currentNode = $currentNode->next;
}

$currentNode->next = $newNode;
```

在这里，我们从 `$_firstNode` 属性获取列表的第一个节点。现在，我们将从第一个节点迭代到列表的末尾。我们将通过检查当前节点的下一个链接是否不为 `NULL` 来确保这一点。如果它是 `NULL`，则我们已到达列表的末尾。为了确保我们不会一直循环在同一个节点上，我们在迭代过程中将当前节点的下一个节点设置为当前项目。`while` 循环代码实现了这一逻辑。一旦我们退出 `while` 循环，我们将链表的最后一个节点设置为 `$currentNode`。现在，我们必须将当前最后一个节点的下一个链接分配给新创建的名为 `$newNode` 的节点，因此我们只需将该对象放入节点的下一个链接中。此对象引用将作为两个节点对象之间的链接。最后，我们还通过后置递增 `$_totalNode` 属性将总节点计数值加 1。

我们本可以轻松地为列表创建另一个属性来跟踪最后一个节点。这本可以使我们免于每次插入新节点时都要遍历整个列表。我们有意忽略了这个选项，以便讲解链表的基本理解。在本章后面，我们将实现该功能以实现更快的操作。

如果我们看一下 `display` 方法，可以看到我们使用了几乎相似的逻辑来遍历每个节点并显示其内容。我们首先获取链表的头部项目。然后，我们遍历列表直到列表项目为 `NULL`。在循环内部，我们通过显示其 `$data` 属性来显示节点数据。现在，我们有了一个用于为链表创建单个节点的节点类 `ListNode`，以及一个用于执行基本 `insert` 和 `display` 操作的 `LinkedList` 类。让我们编写一小段代码来利用 `LinkedList` 类创建一个书名链表：

```php
$BookTitles = new LinkedList();

$BookTitles->insert("Introduction to Algorithm");

$BookTitles->insert("Introduction to PHP and Data structures");

$BookTitles->insert("Programming Intelligence");

$BookTitles->display();
```

在这里，我们为 `LinkedList` 创建一个新对象并将其命名为 `$BookTitles`。然后，我们使用 `insert` 方法插入新的书籍项目。我们添加了三本书，然后使用 `display` 方法显示书名。如果我们运行前面的代码，将看到以下输出：

```
Total book titles: 3

Introduction to Algorithm

Introduction to PHP and Data structures

Programming Intelligence
```

正如我们所见，第一行有一个计数器，显示我们有三个书名，以及它们的名称。如果我们仔细观察，会发现书名的显示顺序与我们输入的顺序相同。这意味着我们实现的链表实际上保持了顺序。这是因为我们总是在列表末尾输入新节点。如果我们想要，本可以采用不同的方式。作为我们的第一个示例，我们已经涵盖了关于链表及其构建方法的许多内容。在接下来的章节中，我们将探索更多关于如何创建不同类型的链表以及更复杂的示例。现在，我们将重点关注不同类型的链表。

## 链表的不同类型

到目前为止，我们处理的列表被称为单向链表，或线性链表。然而，根据涉及的操作，还有其他几种不同类型的链表：

*   双向链表
*   循环链表
*   多重链表

## 双向链表

在双向链表中，每个节点上有两个链接：一个指向下一个节点，另一个指向前一个节点。单向链表是单向的，而双向链表是双向的。我们可以在列表中毫无问题地向前或向后移动。下图显示了一个双向链表的示例。稍后，在 *用 PHP 实现双向链表* 部分，我们将探讨如何实现双向链表：

![](img/Image00022.gif)

## 循环链表

在单向或双向链表中，最后一个节点之后没有节点，因此最后一个节点没有任何后续节点可供迭代。如果我们允许最后一个节点指向第一个节点，就形成了一个环。这样的链表称为循环链表。单向链表和双向链表都可以作为循环链表。我们将在本章中实现一个循环链表。下图描绘了一个循环链表：

![](img/Image00023.gif)

## 多重链表

多重链表是一种特殊类型的链表，它拥有两个或更多链接将每个节点链接到另一个节点。根据链表的目的，它可以多方向增长。例如，如果我们以学生名单为例，每个学生是一个具有姓名、年龄、性别、系别、专业等属性的节点，那么我们不仅可以将每个学生的节点与下一个和上一个节点链接，还可以按年龄、性别、系别和专业进行链接。虽然使用这种链表需要对链表概念有很好的理解，但我们可以在需要时使用这种特殊的链表。下图描绘了一个多重链表：

![](img/Image00024.jpg)

## 插入、删除和搜索项目

到目前为止，我们只看到了插入节点和显示所有节点内容的操作。现在，我们将探索链表中可用的其他操作。我们将主要关注以下操作：

*   在第一个节点处插入
*   搜索节点
*   在特定节点前插入
*   在特定节点后插入
*   删除第一个节点
*   删除最后一个节点
*   搜索并删除一个节点
*   反转链表
*   获取第 N 个位置的元素

## 在第一个节点处插入

当我们在前端（即头部）添加节点时，必须考虑两种简单的可能性。列表可以为空，因此新节点即为头节点。这种可能性简单明了。然而，如果列表已经有头节点，则必须执行以下操作：

1.  创建新节点。
2.  将新节点设为第一个节点或头节点。
3.  将之前的头节点或第一个节点指定为新创建的第一个节点的下一个节点。

以下是实现代码：

```php
public function insertAtFirst(string $data = NULL) {
    $newNode = new ListNode($data);

    if ($this->_firstNode === NULL) {
        $this->_firstNode = &$newNode;
    } else {
        $currentFirstNode = $this->_firstNode;
        $this->_firstNode = &$newNode;
        $newNode->next = $currentFirstNode;
    }

    $this->_totalNode++;
    return TRUE;
}
```

## 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

### 搜索节点

搜索节点非常简单。我们需要遍历每个节点，并检查目标数据是否与节点数据匹配。如果找到数据，则返回该节点；否则返回 `FALSE`。实现如下所示：

```php
public function search(string $data = NULL) {
    if ($this->_totalNode) {
        $currentNode = $this->_firstNode;
        while ($currentNode !== NULL) {
            if ($currentNode->data === $data) {
                return $currentNode;
            }
            $currentNode = $currentNode->next;
        }
    }
    return FALSE;
}
```

### 在特定节点前插入

此过程类似于我们之前查看的第一个操作。主要区别在于我们需要找到特定节点，然后在其前面插入新节点。当找到目标节点时，我们可以将新创建节点的 `next` 指向目标节点，并将前一个节点的 `next` 指向新创建的节点。这在下图中展示：

![](img/Image00025.jpg)

以下是实现上述逻辑的代码：

```php
public function insertBefore(string $data = NULL, string $query = NULL) {
    $newNode = new ListNode($data);

    if ($this->_firstNode) {
        $previous = NULL;
        $currentNode = $this->_firstNode;
        while ($currentNode !== NULL) {
            if ($currentNode->data === $query) {
                $newNode->next = $currentNode;
                $previous->next = $newNode;
                $this->_totalNode++;
                break;
            }
            $previous = $currentNode;
            $currentNode = $currentNode->next;
        }
    }
}
```

如果我们检查前面的代码，可以看到逻辑非常直接。此方法有两个参数：一个是 `data`，一个是 `query`。我们遍历每个节点。在此过程中，我们还跟踪当前节点和前一个节点。跟踪前一个节点很重要，因为当找到目标节点时，我们将把前一个节点的 `next` 设置为新创建的节点。

### 在特定节点后插入

此过程类似于在目标节点前插入节点。区别在于我们需要在目标节点后插入新节点。在这里，我们需要同时考虑目标节点及其指向的下一个节点。当找到目标节点时，我们可以将新创建节点的 `next` 指向目标节点原本的下一个节点，并将目标节点的 `next` 指向新创建的节点。以下是实现此操作的代码：

```php
public function insertAfter(string $data = NULL, string $query = NULL) {
    $newNode = new ListNode($data);

    if ($this->_firstNode) {
        $nextNode = NULL;
        $currentNode = $this->_firstNode;
        while ($currentNode !== NULL) {
            if ($currentNode->data === $query) {
                if ($nextNode !== NULL) {
                    $newNode->next = $nextNode;
                }
                $currentNode->next = $newNode;
                $this->_totalNode++;
                break;
            }
            $currentNode = $currentNode->next;
            $nextNode = $currentNode->next;
        }
    }
}
```

### 删除第一个节点

删除节点仅意味着取出该节点并重新排列前一个和后一个节点的链接。如果我们只是移除一个节点，并将前一个节点的 `next` 链接与被删除节点的下一个节点连接起来，删除操作就完成了。请看下面的示例：

![](img/Image00026.jpg)

当我们删除第一个节点时，只需将第二个节点设为头节点或第一个节点。我们可以通过以下代码轻松实现：

```php
public function deleteFirst() {
    if ($this->_firstNode !== NULL) {
        if ($this->_firstNode->next !== NULL) {
            $this->_firstNode = $this->_firstNode->next;
        } else {
            $this->_firstNode = NULL;
        }
        $this->_totalNode--;
        return TRUE;
    }
    return FALSE;
}
```

现在，我们必须考虑一种特殊情况，即将总节点数减一。

### 删除最后一个节点

删除最后一个节点要求我们将倒数第二个节点的 `next` 链接设为 `NULL`。我们将迭代直到最后一个节点，并在过程中跟踪前一个节点。一旦到达最后一个节点，将前一个节点的 `next` 属性设为 `NULL`，如下例所示：

```php
public function deleteLast() {
    if ($this->_firstNode !== NULL) {
        $currentNode = $this->_firstNode;
        if ($currentNode->next === NULL) {
            $this->_firstNode = NULL;
        } else {
            $previousNode = NULL;

            while ($currentNode->next !== NULL) {
                $previousNode = $currentNode;
                $currentNode = $currentNode->next;
            }

            $previousNode->next = NULL;
            $this->_totalNode--;
            return TRUE;
        }
    }
    return FALSE;
}
```

首先，我们检查列表是否为空。然后，我们检查列表是否有多个节点。根据结果，我们遍历到最后一个节点并跟踪前一个节点。接着，我们将前一个节点的 next 链接赋值为 `NULL`，以便从列表中移除最后一个节点。

## 搜索并删除节点

我们可以使用搜索和删除操作从列表中删除任意节点。首先，我们在列表中搜索该节点，然后通过移除该节点的引用来删除它。以下是实现此功能的代码：

```php
public function delete(string $query = NULL) {
    if ($this->_firstNode) {
        $previous = NULL;
        $currentNode = $this->_firstNode;
        while ($currentNode !== NULL) {
            if ($currentNode->data === $query) {
                if ($currentNode->next === NULL) {
                    $previous->next = NULL;
                } else {
                    $previous->next = $currentNode->next;
                }
                $this->_totalNode--;
                break;
            }
            $previous = $currentNode;
            $currentNode = $currentNode->next;
        }
    }
}
```

## 反转列表
