
Web 前端开发者使用日志来帮助管理其应用的状态。在 Redux 中，^([\[13\]](#f_0029.xhtml#FOOTNOTE-13)) 一个与 React 经常一起使用的流行 JavaScript 库，你会以纯文本对象的形式记录更改，并使用纯函数处理这些更改，这些纯函数会将更新应用于你的应用状态。

所有这些示例都使用日志来存储、共享和处理有序数据。这真的很酷，因为同一个工具可以用于复制数据库、协调分布式服务以及管理前端应用的状态。你可以通过将系统中的更改拆解为单一、原子操作来解决大量问题，特别是在分布式服务中，这些操作可以通过日志进行存储、共享和处理。

数据库通常提供一种方式，将其状态恢复到过去的某个时间点，这通常称为“时间点恢复”。你会从过去取一个数据库快照，然后通过重放写前日志直到达到你想要的时间点。如果你自始至终都有每一个日志，就不需要快照；但对于拥有长期历史且变更很多的数据库，保存每一个日志是不可行的。 Redux 使用相同的思想来实现撤销/重做操作：它在每个操作后记录应用的状态，撤销操作只需让 Redux 将 UI 中显示的状态回退到之前记录的状态。像 Git 这样的分布式版本控制系统也工作原理相同；你的提交日志历史就是字面意义上的提交日志。

如你所见，完整的日志不仅包含最新状态，还包含所有曾经存在的状态，这使得你能够构建一些原本需要复杂才能实现的酷炫功能。日志很简单——这也是它们为何出色。

## 如何工作

日志是一种仅追加的记录序列。你在日志末尾追加记录，通常从上到下、从旧到新阅读（类似运行 `tail -f` 命令查看文件）。你可以记录任何数据。历史上，人们用“日志”一词指代供人类阅读的文本行，但随着更多人使用日志系统，其中的“日志”已变为供其他程序阅读的二进制编码消息。当我在本书中谈论日志和记录时，我并不特指任何一种特定的数据类型。当你向日志中追加记录时，日志会为该记录分配一个唯一且递增的偏移量，这相当于该记录的 ID。日志就像一张始终按时间排序的表格，它为每条记录按偏移量和创建时间进行索引。

日志的具体实现必须处理我们没有无限磁盘空间的事实，这意味着我们不能无限期追加到同一个文件中。因此，我们将日志分割为若干段。当日志过大时，我们通过删除已处理或归档的旧段来释放磁盘空间。清理旧段的操作可以在后台进程中运行，而我们的服务仍可继续向最新（活动）段写入，并从其他段读取，几乎不会产生冲突，尤其是在协程访问相同数据时。

在段列表中，总有一个特殊的段，我们称之为“活动段”。因为它是唯一我们正在向其写入的段。当活动段写满时，我们会创建一个新段并使其成为活动段。

每个段包含一个存储文件和一个索引文件。段的存储文件用于存储记录数据；我们会持续向该文件追加记录。段的索引文件用于存储每条记录的索引信息。索引文件通过加速读取来提升性能，因为它将记录的偏移量映射到存储文件中的位置。给定偏移量读取记录是两步过程：首先从索引文件获取该记录的条目，该条目告诉你记录在存储文件中的位置；然后在存储文件中读取该位置的记录。由于索引文件仅需要两个字段——记录的偏移量和在存储文件中的存储位置，因此索引文件远小于存储所有记录数据的存储文件。索引文件足够小，我们可以将它们内存映射^([\[14\]](#f_0029.xhtml#FOOTNOTE-14))，使文件操作的速度与在内存中操作的速度一样快。

现在你已经了解了日志的工作原理，是时候自己构建一个了。让我们开始编码吧。

## 构建日志

我们从底层开始构建日志，先构建存储和索引文件，然后是段，最后是日志。这样我们可以在构建每个组件时编写并运行测试。由于“日志”一词可能指代至少三种不同的事物——记录、存储记录的文件以及将多个段组合在一起的抽象数据类型——为了避免混淆，在本章中我将始终使用以下术语来指代这些事物：

*   记录——我们日志中存储的数据。

*   存储——用于存储记录的文件。

*   索引——用于存储索引条目的文件。

*   段——将存储文件和索引文件捆绑在一起的抽象层。

*   日志——将所有段组合在一起的抽象层。

### 编码存储

首先，在 `internal/log` 目录下创建我们的日志包目录，然后在该目录中创建名为 `store.go` 的文件，其中包含以下代码：

[WriteALogPackage/internal/log/store.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store.go) 

| ​  || ​**package**​ log |

| --- | --- |

| ​  ||  |

| ​  || ​**import**​ ( |

| ​  || ​*"bufio"*​ |

| ​  || ​*"encoding/binary"*​ |

| ​  || ​*"os"*​ |

| ​  || ​*"sync"*​ |

| ​  || ) |

| ​  ||  |

| ​  || ​**var**​ ( |

| ​  || enc = binary.BigEndian |

| ​  || ) |

| ​  ||  |

| ​  || ​**const**​ ( |

| ​  || lenWidth = 8 |

| ​  || ) |

| ​  ||  |

| ​  || ​**type**​ store ​**struct**​ { |

| ​  || \*os.File |

| ​  || mu sync.Mutex |

| ​  || buf \*bufio.Writer |

| ​  || size ​**uint64**​ |

| ​  || } |

| ​  ||  |

| ​  || ​**func**​ newStore(f \*os.File) (\*store, ​**error**​) { |

| ​  || fi, err := os.Stat(f.Name()) |

| ​  || ​**if**​ err != nil { |

| ​  || ​**return**​ nil, err |

| ​  || } |

| ​  || size := ​**uint64**​(fi.Size()) |

| ​  || ​**return**​ &store{ |

| ​  || File: f, |

| ​  || size: size, |

| ​  || buf: bufio.NewWriter(f), |

| ​  || }, nil |

| ​  || } |

The store struct is a simple wrapper around a file with two APIs to append and read bytes to and from the file. The `newStore(\*os.File)` function creates a store for the given file. The function calls `os.Stat(name string)` to get the file’s current size, in case we’re re-creating the store from a file that has existing data, which would happen if, for example, our service had restarted.

We refer to the `enc` variable and `lenWidth` constant repeatedly in the store, so we place them up top where they’re easy to find. `enc` defines the encoding that we persist record sizes and index entries in and `lenWidth` defines the number of bytes used to store the record’s length.

Next, write the following `Append` method below `newStore`:

[WriteALogPackage/internal/log/store.go](http://media.pragprog.com/titles/tjgo/code/WriteALogPackage/internal/log/store.go) 

| ​  || ​**func**​ (s \*store) Append(p \[\]​**byte**​) (n ​**uint64**​, pos ​**uint64**​, err ​**error**​) { |

| --- | --- |

| ​  || s.mu.Lock() |

| ​  || ​**defer**​ s.mu.Unlock() |

| ​  || pos = s.size |

| ​  || ​**if**​ err := binary.Write(s.buf, enc, ​**uint64**​(len(p))); err != nil { |

| ​  || ​**return**​ 0, 0, err |

| ​  || } |

| ​  || w, err := s.buf.Write(p) |

| ​  || ​**if**​ err != nil { |

| ​  || ​**return**​ 0, 0, err |

| ​  || } |

| ​  || w += lenWidth |

| ​  || s.size += ​**uint64**​(w) |

| ​  || ​**return**​ ​**uint64**​(w), pos, nil |

| ​  || } |

