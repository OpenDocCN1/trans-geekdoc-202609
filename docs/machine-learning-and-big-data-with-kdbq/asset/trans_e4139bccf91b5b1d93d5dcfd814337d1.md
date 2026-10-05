

## Splayed.io 与分区的表

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

## 6.4 分区表 (PARTITIONED TABLES)

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

## 数据操作 (DATA OPERATIONS)

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

### 列表 6.1 一个 quotes 表示例

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

## 拆分与分区表

是怎么回事？事实证明，虽然 `trd` 拥有 2016.04.07、2016.04.08 和 2016.04.11 分区，但 `qt` 只有 2016.04.07 和 2016.04.08。`mydb` 中的每个表分区几乎完全相同。我们通过重新创建 `quotes`（使用列表 6.1）然后将 `quotes` 存储为 `qt` 来解决这个问题：

```
`qt select from quotes where date=x;
.0pt:/mydb;x; code];
delete qt from :
```

