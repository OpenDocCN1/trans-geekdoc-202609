
```
`$":,datadir,/tradesfile" set trades
```

这并不是我们想要的结果。如果执行成功，返回的是作为符号格式的文件路径：

```
:C:/data/tradesfile
```

然后我们可以使用 `get` 从文件中加载表，在这种情况下，我们可以指定新表名（通过将 `get` 的结果赋值给名为该名的变量）：

```
trades1 : get "$:\,datadir,/tradesfile"
```

或者使用 `load`，在这种情况下，加载的表将赋值给新变量，变量名与文件名匹配，在此特定案例中为 `tradesfile`：

```
load "$:\,datadir,/tradesfile"
```

最后，我们注意到在上面的示例中，文件描述符——指向文件或输出资源的指示器——由一个第一个字符为冒号的符号表示。如果我们已经在处理符号路径，另一种构造文件描述符的方法是使用 `hsym` 函数：

```
path:`datadir
path
/path/to/file
hsym path
:/path/to/file
```

## 数据操作 (DATA OPERATIONS)

### 6.3 展开的表 (SPLAYED TABLES)

与其将表保存为单个二进制文件，我们可以将表保存为展开形式（splayed），即每列都保存在一个独立的二进制文件中。这对于中等规模的表（多达 1 亿行）特别有用。查询通常只引用此类表列的一小部分。将列存储在单独的文件文件中允许 kdb+ 通过仅加载这些列来节省时间。要实现这一点，我们通常会调用目录路径作为 `set` 的参数，而不是文件。然而，以下操作将无法展开表，因为它包含了未枚举（unenumerated）的 `symbol` 类型列：

```
hsm[`$datadir//tradesdir` set trades
```

我们可以移除这些列并将表保存为一个文件：

```
hsm[`$datadir//tradesdir` set mktflag
```

注意目录路径末尾的 `/`。结果是 `tradesdir` 将在 `datadir` 下创建。它将包含名为 `.d`、`code`、`comments`、`date`、`time` 和 `volume` 的文件。我们无法保存原始的 `trades` 表，因为我们要演示如何对它们进行枚举。在继续之前，如果你按照上述步骤创建了该目录，请删除包含所有内容的目录，以便从零开始。为了枚举 `trades` 中的 `symbol` 列，我们使用 `.Q`：

```
tradesdir: hsm `$datadir//tradesdir/;
tradesenum: .Q[tradesdir; trades];
```

这将创建一个 `tradesdir` 目录，其中包含一个名为 `sym` 的单一二进制文件。该文件枚举了 `symbol` 类型列中发现的值，这些值分别名为 `code`、`price` 和 `time`。一旦完成，我们运行：

```
tradesdir set tradesenum
```

该目录现在包含 `.d`、`code`、`date`、`mktflag`、`price`、`sym`、`volume` 文件。注意，这次由于枚举了 `symbol` 列，我们能够成功保存 `symbol` 类型列。请注意，与之前的命令不同，

```
tradesdir set trades
```

将像之前一样报错 'type' 错误。¹如果表是键表（keyed table），也会抛出相同的错误。我们需要在保存表之前用 `()` 移除键。

让我们查看 `tradesdir` 目录中的单个文件。`date`、`price` 和 `volume` 文件包含对应名称列的序列化数据。注意，你可以单独对列进行序列化。该命令将创建一个文件 `myfile`，其内容与 `tradesdir/price` 相同。回想 `trades[`price]` 是一个 `float` 类型的列表：

| |

| :--- |

| 38.3 1239.7 1240.5 38.04 18.85 124.2 1240 18.53 40.61 18.44 40.78 | 41.43 18.35 19.05 1257.9 1258.7 |

当我们运行

```
hsm[`$datadir,/mycols` ] set col tradesdir[datadir,/mycols` ] set col trades
```

我们将得到一个文件 `mycols`，其内容与 `tradesdir/.d`相同。这是列名（作为符号）的序列化。在这里，当我们运行

```
hsm[`$datadir,/mycode` ] set trades[`code`]
```

我们将得到 `myfile`，其内容与 `tradesdir/code` 不同。这是因为枚举表中的符号都存储在 `tradesdir/sym` 中，而 `tradesdir/code` 包含的是 `tradesdir/sym` 中的符号索引。通过运行以下命令可以重现 `tradesdir/code`：

```
hsm[`$datadir,/mycode` ] set tradesenum[`code`]
```

这强调了 `trades` 和 `tradesenum` 之间的区别：`.Q` 返回的类型结果如下：

```
type trades[`code`]
type tradesenum[`code`]
```

尽管 `meta trades` 和 `meta tradesenum` 的结果看起来完全相同。

与 `tradesdir/code` 类似，`tradesdir/mktflag` 文件包含枚举字符串的序列化，这些字符串包含 `tradesdir/sym` 中实际字符串的索引。每个对应符号值的唯一文本字符串存储在 `tradesdir/sym` 中。使用 Java 的术语，符号被内化了（interned）。列注释（类型为 `string` 而非 `symbol`）由两个文件分析：`tradesdir/comments` 和 `tradesdir/comments\`。后者 `comments\` 包含了字符串中的实际文本。枚举符号列的序列化数据（其中唯一值仅存储一次），`comments\` 包含了它们。如果你用二进制查看器打开此文件，你会发现例如 "NEXYM/CME Group trade" 出现了多次。

### Splayed.io 与分区的表

额外的输入是我们想要追加到现有 splayed（拆分）表中的表。该函数定义如下：

```
quantQ.io.appendSplayedTab:[tabPath;pvar;table;table2Add]
// tabPath -- 存储表的目录路径
// pvar -- 用于快速查询的排序和索引的变量
// table -- 保存的表之名
// table2Add -- 要追加的表
:@;pvar*] pvar xasc (` sv (tabPath;`;table`)) upsert .Q[tabPath]
; table2Add;
```

最后一个变量是传递给函数的表名，因此它是在不带回溯的情况下被调用的（换句话说，它不是作为全局变量引用传递的）。使用此类函数的示例下：

```
quantQ.appendSplayedTab[hsym $datadir,"/sdb`;code;`trades;newTrades]
```

虽然我们演示了两个用于保存 splayed 表并向其追加更多数据的函数，这两个函数几乎完全相同，区别在于初始保存时使用 `set` 而追加时使用 `upsert`。`upsert` 在表不存在时会创建表，因此封装了这两种操作，我们可以在上述两个示例中使用 `quantQ.io.appendSplayedTab`。

### 6.4 分区表 (PARTITIONED TABLES)

除了对表进行拆分，我们还可以对其进行分区：对于列的每个不同值 $v$ 定义一个分区，将创建一个独立的目录，其中将存储序列化列的二进制文件，且仅包含分区列中值为 $v$ 的行。标准的 `.Q.dpft` 函数执行分区。该函数的名称代表了它的四个参数：目录、分区、排序字段和表名。为了存储 `trades` 表，我们可以执行以下代码：

```
mydbir: hsym $datadir,"/mydb"
{
 `trd set select from trades where x=
 .Q.dpft[mydbir];x;code;`trd`;
 delete trd from `
} each distinct trades[`date]
```

我们将为 `date` 表中的每个不同值调用一次 `.Q.dpft`，结果产生以下调用：

```
Q.dpft[mydbir];2016.04.07;code;`trd1;
Q.dpft[mydbir];2016.04.08;code;`trd2;
Q.dpft[mydbir];2016.04.11;code;`trd3];
```

其中 `trd1``trd2``trd3` 分别是从 `trades` 中选择具有 2016.04.07、2016.04.08、2016.04.11 值的三个表名：

```
select from trades where date=2016.04.07;
select from trades where date=2016.04.08;
select from trades where date=2016.04.11;
```

我们无法按照如下方式实现我们的类：

```
Q.dpft[myddir; 2016.04.07; `code; select from trades where date
~=2016.04.07`;
Q.dpft[myddir; 2016.04.08; `code; select from trades where date
~=2016.04.08`;
Q.dpft[myddir; 2016.04.11; `code; select from trades where date
~=2016.04.11];
```

由于 `Q.dpft` 最后一个参数的类型原因：它期望第四个参数是表名，即全局变量引用，而不是实际表。表始终保存到同名的目录中。这就是为什么我们创建一个临时表 `trd` 并将其写入全局命名空间（`.trd`），而不是使用 `trd set .`，后者会在匿名函数的 `{...}` 块中创建变量 `trd`。我们将无法引用该变量为 `trd`。在函数结束时，我们从全局命名空间删除临时表：

```
delete trd from `.`
```

通过上述 `.Q.dpft` 将获得以下目录结构：

- C:/data/mydb

- 2016.04.07

  - trd

    - .d

    - code

    - comments

    - date

    - mktflag

    - price

    - time

    - volume

- 2016.04.08

  - trd

    - .d

    - volume

- 2016.04.11

  - trd

    - .d

    - volume

指定的 `.Q.dpft` 方向，每个分区（2016.04.07、2016.04.08 和 2016.04.11）有一个子目录。在这些目录中，有一个与传递给 `.Q.dpft` 的表名相同的子目录。在 `trd` 中，我们拥有与拆分表时相同的文件，`sym` 除外，它现在位于两层之上。之前，我们还没有显式调用 `.Q.dpft`。

我们可以向 `mydb` 目录添加另一个表。假设我们有如下（再次需要的）`quotes` 表：

#### 列表 6.1 一个 quotes 表示例

```
bidprice:float($); bidsize:short($); askprice:float($); asksize:short($); mktflag:symbol());
quotes (code:symbol(); date:date(); time:time();
2016.04.07; 10:15:00.010; 38.34; 86; );
2016.04.07; 11:02:16.663; 1241.4; 1241.5; );
2016.04.07; 12:05:20.303; 38.12; 7; 38.13; );
2016.04.07; 13:22:20.005; 38.11; 38.12; );
2016.04.07; 13:50:00.205; 1238.6; 8; );
2016.04.07; 15:20:02.224; 1240.9; 38.53; );
2016.04.08; 15:00:05.051; 38.52; 6; 1241.f; );
2016.04.08; 10:53:00.002; 40.83; 40.84; 66; );
2016.04.08; 13:56:30.070; 40.54; 38.56; 58; );
2016.04.08; 15:20:02.000; 40.77; 26; 44; );
2016.04.08; 15:21:43.786; 40.76; 3; 28; );
 )
```

我们运行以下代码：

```
{
qt select from quotes where date=x;
Q.dpft[mydb;quotes];
delete qt from _;
each quotes[`date]
```

并获得以下目录结构：

```
- C:/data/mydb
- 2016.04.07
  - trd
    - .d
    - code
    - comments
    - comments
    - date
    - mktflag
    - price
    - time
    - volume
  - qt
    - .d
    - askprice
    - asksize
    - bidprice
    - bidsize
    - code
    - date
    - mktflag
    - time
- 2016.04.04
  - trd
    - .d
    - :
    - volume
  - qt
    - .d
    - :
    - time
- 2016.04.11
  - trd
    - .d
    - :
    - volume
- sym
```

要将分区表加载到 kdb+，你必须将包含它们的目录作为命令行参数传递给 q 可执行文件（我们在以此方式重启之前杀掉了已打开的实例）：

```
C: \q\w32>q "C:\data\mydb"
```

然而，我们遇到了惊喜：

```
\v
`date``sym``trd
```

### 拆分与分区表

是怎么回事？事实证明，虽然 `trd` 拥有 2016.04.07、2016.04.08 和 2016.04.11 分区，但 `qt` 只有 2016.04.07 和 2016.04.08。`mydb` 中的每个表分区几乎完全相同。我们通过重新创建 `quotes`（使用列表 6.1）然后将 `quotes` 存储为 `qt` 来解决这个问题：

```
`qt select from quotes where date=x;
.0pt:/mydb;x; code];
delete qt from :
```

### 展开与分区的表

我们可以通过重建 `quotes` 表（运行列表 6.1）来测试它，并使用我们现在追加到赋值（`set`）操作符末尾作为最后一个参数的新函数将其写入磁盘：

```
  qt = select from quotes where date=x;
  quantQ.io.dfpsAppend[mydbdir;x];`code`;`qt`;`sym];
  delete qt from quotes;
 2016.04.07 2016.04.08 2016.04.11
```

然后追加更多 `quotes`：

```
qt = morequotes;
quantQ.io.dfpsAppend[mydbdir;2016.04.07];`code`;`qt`;`sym];
delete qt from quotes;
```

这次我们实现了向 `qt` 中的分区追加数据的目标：在再次启动后：

```
C:\q\w32> "C:\data\mydb"
```

我们检查是否已向磁盘上的分区添加了数据：

select from

| date | code | time | bidprice | bidsize | askprice | asksize | mktflag |

| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |

| 2016.04.07 | CLM 16 | 15:00:00.010 | 38.32 | 16 | 38.35 | 3 | E |

| 2016.04.07 | CLM 12 | 12:05:00.303 | 38.12 | 7 | 38.13 | 13 | E |

| 2016.04.07 | CLM 12 | 22:02:48.856 | 38.11 | 16 | 38.12 | 8 | E |

| 2016.04.07 | CLM 15 | 11:02:19.663 | 38.52 | 0 | 38.53 | 18 | E |

| 2016.04.07 | GCM 12 | 12:04:126.4 | 1241.4 | 22 | 1241.5 | 1 | E |

| 2016.04.07 | GCM 16 | 13:00:21.147 | 1241.2 | 4 | 1241.3 | 1 | E |

| 2016.04.07 | GCM 15 | 20:50:22.224 | 1240.9 | 6 | 1241 | 1 | E |

| 2016.04.07 | GCM 16 | 13:33:04.535 | 1241.7 | 17 | 1241.6 | 2 | E |
