

## 检查文件是否存在：file_exists()

如果你想在不实际打开文件的情况下检查文件是否存在，可以使用 file_exists()，如下所示：

```php
if (file_exists("$document_root/../orders/orders.txt")) {
    echo 'There are orders waiting to be processed.';
} else {
    echo 'There are currently no orders.';
}
```

## 确定文件大小：filesize()

你可以使用 `filesize()` 函数来检查文件大小：
`filesize("$document_root/../orders/orders.txt")`

它返回以字节（bytes）为单位的文件大小，可以配合 `read()` 函数使用，以便一次读取文件（或文件的部分）。你甚至可以将原始脚本替换为以下内容：
```php
$fp = fopen("$document_root/../orders/orders.txt", 'rb');
echo nl2br($fp, filesize("$document_root/../orders/orders.txt"));
close($fp);
```

`nl2br` 函数将输出中的 `\n` 字符转换为 HTML 换行符如 `<br />`。

## 删除文件：unlink()

如果你想在处理订单后删除文件，可以使用 `unlink()`。（没有名为 `deleted` 的函数）。例如：
`unlink("$document_root/../orders/orders.txt");`

如果无法删除文件，该函数将返回 `false`。这种情况通常发生在文件权限不足或文件不存在时。

## 在文件内部导航：rewind(), fseek(), 和 ftell()

你可以使用 `rewind()` 和 `fseek()` 来操作和解码文件内部文件指针的位置。

`rewind()` 函数将文件指针重置为文件的开头。`ftell()` 函数报告文件指针在文件中距离开头多少字节（字节为单位）。例如，你可以将这些行添加到原始脚本的末尾（在 `fclose()` 命令之前）：

```php
echo 'Final position of the file pointer is '.ftell($fp).';';
echo '<br />';
rewind($fp);
echo 'After rewind, the position is '.ftell($fp).';';
echo '<br />';
```

浏览器中的输出应该与图 2.5 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_102_0.png)

图 2.5 读取订单后，文件指针指向文件末尾，偏移量为 198 字节。调用 `rewind` 将置回位置 0，即文件开头。

你可以使用 `fseek()` 函数将文件指针设置为文件中的某点。它的原型是：

```c
int fseek( resource fp, int offset, int whence );
```

调用 `fseek()` 将文件指针设置为从 `whence` 开始并向文件移动 `offset` 距离的点。可选的 `whence` 参数默认值为 `SEEK_SET`，它实际上是文件的开头。其他可能的值是 `SEEK_CUR`（文件指针的当前位置）和 `SEEK_END`（文件末尾）。

`rewind()` 函数等同于调用偏移量为零的 `fseek()` 函数。例如，你可以使用 `fseek()` 来查找文件中中间的记录，或执行二分查找。如果数据文件的复杂度达到了你需要进行这类操作的程度，那么使用专门的数据库会让你的生活轻松得多。

## 锁定文件

想象一种情况：两个客户正尝试同时订购产品。（这种情况并不罕见，特别是当你的网站开始产生任何流量时）。如果一个客户调用了 `fopen()` 并开始写入，另一个客户又调用了 `fopen()` 并开始写入。文件的最终内容将会是什么？是第一个订单后跟着第二个订单，还是反之？是其中一个订单还是？

## 第 2 章 存储和检索数据

或者是某些没那么用的东西，因为两者以某种方式交织在一起？答案取决于你的操作系统，但通常无法得知。

为了避免此类问题，可以使用文件锁定。在 PHP 中，你通过使用 `flock()` 函数使用此功能。在打开文件后、在从文件中读取或写入任何数据之前，应该调用此函数。

`flock()` 的原型为：

```php
bool flock(resource fp, int operation, int &wouldblock)
```

你需要传递一个指向已打开文件的指针，代表你所需的锁类型。如果成功获取锁则返回 `true`，如果未获取则返回 `false`。可选的第三参数可以包含如果获取锁可能导致当前进程阻塞（即等待）的值。

`operation` 的可能值见表 2.2。

表 2.2 flock() 操作值
| 操作值 | 含义 |
|---|---|
| LOCK_SH | 读锁。该文件可以与其他读取者共享。 |
| LOCK_EX | 写锁。此操作是排他的；文件不能共享。 |
| LOCK_UN | 释放现有的锁。 |
| LOCK_NB | 在尝试获取锁时防止阻塞。（Windows 不支持。） |

如果你打算使用 `flock()`，你将将它添加到所有使用该文件的脚本中；否则，它将毫无用处。

请注意，`flock()` 不在 NFS 或其他网络文件系统上工作。它也不不支持锁定的旧式文件系统（如 FAT）。在某些操作系统上，它是在进程级别实现的，如果你使用多线程服务器 API，它将无法正常工作。

要通过示例使用它，你可以如下修改 `processor.php`：

```php
$fp = fopen("$document_root/../orders/orders.txt", 'ab');
flock($fp, LOCK_EX);

if (!$fp) {
    echo "<p>Your order could not be processed at this time. Please try again later.</p></body></body></html>";
    exit;
}

fwrite($fp, $outputstring, strlen($outputstring));
```

## 更好的方法：数据库

```php
flock($fp, LOCK_UN);
fclose($fp);
```

你还应该给 `viewers.php` 添加锁：

```php
$fp = fopen("$document_root/../orders/orders.txt", 'rb');
flock($fp, LOCK_SH); // 锁定文件读取
// 从文件读取
flock($fp, LOCK_UN); // 释放读锁
fclose($fp);
```

代码更健壮了但并不完美。如果两个脚本同时尝试获取锁？这将导致竞态条件，在竞态条件中，竞争锁将是不确定哪个会成功。

## 更好的方法：数据库

到目前为止，我们看到的示例都是文件。在本书的第二部分中，我们将研究使用数据库。你可能会问：“为什么要费劲？”

## 使用平文件的问题

使用平文件有很多问题：

- 当文件变大时，处理平文件会非常慢。
- 在文件中查找特定的记录或一组记录很困难。如果或者是某些没那么用的东西，因为两者以某种方式交织在一起？
- 处理并发访问会变成问题。你已经看到如何锁定文件，但这可能导致瓶颈。
- 你所看到的所有文件处理都是顺序的；即你从文件开始读取到末尾。在文件中间插入或删除记录很困难，因为你必须将文件读取到内存，修改后再写回文件。
- 除了文件权限限制之外，没有强制不同访问级别的方法。

## RDBMS 如何解决这些问题

关系型数据库管理系统（RDBMS）解决了这些问题：

- RDBMS 访问数据比平文件快得多。而且我们在书中使用的 MySQL 是 RDBMS 中最快的之一。
- RDBMS 可以轻松查询提取符合条件的数据集。
- RDBMS 内置了处理并发访问的机制，让你作为程序员，可以设置并使用 MySQL 而不必担心它。
- RDBMS 提供对数据的随机访问。
- RDBMS 有内置的权限系统。MySQL 在此方面有优势。

可能使用 RDBMS 的主要原因是数据存储系统所需的所有或大部分功能已经实现。你可以自己写一套 PHP 函数库，但为什么要重复轮子呢？

在本书的第二部分“使用 MySQL”中，我们将讨论关系型数据库的一般工作原理，并专门介绍如何使用 MySQL 创建基于数据库的网站。

