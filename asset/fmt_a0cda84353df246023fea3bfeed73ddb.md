
## 定义分布式索引 `film_dist`

定义了一个分布式索引 `film_dist`，仅使用本地的 `film_main` 索引，但作为代理（通过 `searchd`）。这并不能真正展示分布式索引的全部优势，因为它仅用于单个代理。然而，“启动 Sphinx” 部分讨论了分布式索引。

```
index film_dist
{
    type = distributed
    agent = localhost:9312:film_main
}
```

## 指定 Indexer 选项

对于此安装，`indexer` 的选项 `mem_limit` 设置为 32 兆字节。这是 `indexer` 允许使用的最大内存量。

```
indexer
{
    mem_limit = 32M
}
```

## 指定 searchd 选项

`searchd` 选项也已定义：

- `address`：`127.0.0.1`，将使用 localhost 地址。
- `port`：`searchd` 端口 `9312`（`searchd` 的默认端口）。
- `searchd_log`：显示对本地 `searchd` 实例请求的日志。
- `query_log`：显示对索引运行了哪些查询。
- `max_children`：可以运行的最大搜索进程数。
- `pid_file`：`searchd` 使用的 pid 文件。
- `max_matches`：返回的最大匹配数（1000）。
- `seamless_rotate`：将此设置为 1。这意味着 `searchd` 可以在不影响使用 `searchd` 的应用程序的情况下重启。

```
searchd
{
    listen          = 127.0.0.1
    port            = 9312
    log             = /usr/local/sphinx/var/log/searchd.log
    query_log       = /usr/local/sphinx/var/log/query.log
    read_timeout    = 5
    max_children    = 30
    pid_file        = /usr/local/sphinx/var/log/searchd.pid
    max_matches     = 1000
    seamless_rotate = 1
}
```

## 启动 Sphinx

现在 `sphinx.conf` 已设置，并且你拥有一个运行中的 Sphinx 系统，你需要运行 `indexer` 并启动搜索守护进程 `searchd`。

### 运行 Indexer

此时，你尚未运行 `indexer`。当你运行它时，`indexer` 会运行你为数据源指定的查询，然后构建你指定的本地索引。由于它们是分布式索引，分布式索引不会也不可能由 `indexer` 构建。

第一次从主 Sphinx 目录（本示例中为 `sphinx` 用户主目录，`/usr/local/sphinx`）运行索引器，请使用以下代码：

```
./bin/indexer --all
Sphinx 0.9.9-id64-release (r2117)
Copyright (c) 2001-2009, Andrew Aksyonoff

using config file '/usr/local/sphinx/etc/sphinx.conf'...
indexing index 'film_main'...
collected 1000 docs, 0.1 MB
sorted 0.0 Mhits, 100.0% done
total 1000 docs, 108056 bytes
total 0.046 sec, 2339583 bytes/sec, 21651.58 docs/sec
indexing index 'film_main_stemmed'...
collected 1000 docs, 0.1 MB
sorted 0.0 Mhits, 100.0% done
total 1000 docs, 108056 bytes
total 0.039 sec, 2746162 bytes/sec, 25414.25 docs/sec
distributed index 'film_dist' can not be directly indexed; skipping.
total 2 reads, 0.000 sec, 111.3 kb/call avg, 0.1 msec/call avg
total 10 writes, 0.000 sec, 55.6 kb/call avg, 0.0 msec/call avg
```

行“distributed index 'film_dist' can not be directly indexed” simply means 指定的分布式索引 `film_dist` 不能作为本地文件进行索引。

### 启动搜索守护进程

要对索引执行查询并使用分布式索引，需要让搜索守护进程 `searchd` 运行。

启动 `searchd`：

```
./bin/searchd
Sphinx 0.9.9-id64-release (r2117)
Copyright (c) 2001-2009, Andrew Aksyonoff

using config file '/usr/local/sphinx/etc/sphinx.conf'...
listening on all interfaces, port=9312
```

你无需显式地将 `searchd` 置于后台运行，因为它会自动在后台作为守护进程运行。

现在索引已准备好进行搜索！测试搜索（仅针对本地索引）可以使用搜索工具进行。你也可以使用 `SphinxAPI`（通过 PHP）或 `SphinxQL`（有关更多信息，请参阅“Searching Sphinx”部分）进行测试。

## 搜索 Sphinx

Sphinx 有自己的查询语言，类似于 MySQL FULLTEXT 索引，但它也提供了搜索文本的选项。

### 搜索模式

Sphinx 有不同的搜索模式，这些模式在程序中指定，也可通过 Sphinx API 设置。搜索模式如表 9-6 所示：

表 9-6：Sphinx 搜索模式

| 搜索模式 | 描述 |
|---|---|
| `SPH_MATCH_ALL` | 匹配所有查询词。此模式为默认值。 |
| `SPH_MATCH_ANY` | 匹配任一查询词。 |
| `SPH_MATCH_PHRASE` | 将查询作为短语匹配，要求完全匹配。 |
| `SPH_MATCH_BOOLEAN` | 将查询作为布尔表达式匹配。 |
| `SPH_MATCH_EXTENDED` | `SPH_MATCH_EXTENDED2` 的别名。 |
| `SPH_MATCH_EXTENDED2` | 使用扩展匹配模式的第二个版本（截至 0.9.9 版）匹配查询。将查询作为 Sphinx 内部查询语言中的表达式匹配。 |
| `SPH_MATCH_FULLSCAN` | 强制使用全扫描模式匹配查询，这意味着所有已索引文档都被视为匹配。此类查询仍会应用过滤、排序和分组，但不执行任何全文搜索。 |

### 排序模式

Sphinx 还允许你查看不同的排序模式。这些模式设置 Sphinx 在对搜索结果排序时使用的排序机制类型。

表 9-7：Sphinx 排序模式

| 排序模式 | 描述 |
|---|---|
| `SPH_SORT_RELEVANCE` | 按相关性降序排序，最佳匹配在前。 |
| `SPH_SORT_ATTR_DESC` | 按属性降序排序，属性值最大的在前。 |
| `SPH_SORT_ATTR_ASC` | 按属性升序排序，属性值最小的在前。 |
| `SPH_SORT_TIME_SEGMENTS` | 按时间段排序——最近一小时、一日、一周等——降序，然后按相关性降序。 |
| `SPH_SORT_EXTENDED` | 按 SQL 类似的列组合升序或降序排序。据 Sphinx 创建者 Andrew 称，这是“王者”，允许你做传统排序模式允许的任何事情。 |
| `SPH_SORT_EXPR` | 按算术表达式排序。 |

### 布尔查询语法

布尔查询语法如下：

- **与：** 两个词都必须找到，可在源的任何位置出现。可以以空格（隐式 AND）或与号（`&`）指定。例如，两个词 *technical* 和 *writer*。

  ```
  technical writer
  technical & writer
  ```

- **或：** 一个或两个词。*technical* 或 *writer*，或两者皆有。

  ```
  technical | writer
  ```

- **非：**（连字符）对词进行否定。在此示例中，词必须包含 *technical*，但不能包含 *writer*。

  ```
  technical -writer
  ```

- **分组**，以便可以指定多个词：在此示例中，你将指定 *technical* 和 *writer* 或 *database* 和 *administrator*。

  ```
  (technical writer) | (database administrator)
  ```

### 扩展查询语法

布尔查询语法还允许你进行邻近搜索以及指定要搜索的字段。

- **与：** 仅在 `title` 列中搜索 *technical* 和 *writer*。

  ```
  @title technical writer
  ```

- **显式 AND：** 这将在 `title` 中搜索 *technical* 和 *writer*，并在 `description` 字段中搜索 *bhagavad*：

  ```
  @title technical writer & @description bhagavad
  ```

- **字段位置限制修饰符：** 指定在 *description* 列的前 30 个字符中搜索词 *monty*。

  ```
  @description[30] monty
  ```

- **多字段搜索运算符：** 下例将在 description 和 title 两列中搜索词 *andrew*。

  ```
  @(title,description) andrew
  ```

- **全字段搜索运算符：** 在此示例中，词 *Andrew* 将在所有列中搜索。

  ```
  @* andrew
  ```

- **EXACT 短语：** 仅引号内的完全短语才会返回结果。

  ```
  "technical writer"
  ```

**邻近：** 允许两个词之间最多有五个词。这意味着短语 *technical writer* 和短语 *technical expertise, database administration, novel writer* 都将被找到。

```
"technical writer"~5
```

**严格顺序运算符：** 这仅匹配完全按顺序的词。此示例仅在完全按顺序时匹配 *patram pushpam toyam phalam*。

```
patram << pushpam << toyam << phalam
```

**精确形式修饰符：** 这使得只有当词的形式完全如指定时才匹配。在下面的片段中，任何匹配的顺序都要求 *Sphinx, fulltext, and index* 完全按该顺序出现。

```
=Sphinx is a =fulltext =index
```

**字段开始和字段结束修饰符：** 第一个示例将匹配 hello world 字段中的任何内容，但不匹配 Patrick says hello 字段。第二个示例将搜索“*Andrews Field*”或甚至“*Andrews!!! Field!!*”，但不会搜索字段“*Andrews football field*”

```
^hello
^Andrews field$
```

### 搜索工具

无论你的索引是否正常工作，`search` 工具都是调试的有用工具——具体来说，如果你试图确定 Sphinx 是否存在问题以及你如何生成索引，或你的应用程序是否存在问题。它绕过你的应用程序以及 `searchd` 直接搜索索引。

> `search` 工具不适用于分布式索引，因为它在文件级别搜索索引，而不是通过 `searchd` 执行搜索。测试索引的其他方法包括使用 PHP 程序（使用 `SphinxAPI`）或 `SphinxQL`。

`search` 有以下选项：

```
./bin/search
Sphinx 0.9.9-id64-release (r2117)
Copyright (c) 2001-2009, Andrew Aksyonoff

Usage: search [OPTIONS] <word1 [word2 [word3 [...] ] ]>

Options are:
-c, --config <file> use given config file instead of defaults
-i, --index <index> search given index only (default: all indexes)
-a, --any           match any query word (default: match all words)
-b, --boolean        match in boolean mode
```

```
-p, --phrase          match exact phrase
-e, --extended         match in extended mode
-f, --filter <attr> <v> only match if attribute attr value is v
-s, --sortby <CLAUSE>  sort matches by 'CLAUSE' in sort_extended mode
-S, --sortexpr <EXPR>  sort matches by 'EXPR' DESC in sort_expr mode
-o, --offset <offset>  print matches starting from this offset (default: 0)
-l, --limit <count>    print this many matches (default: 20)
-q, --noinfo           don't print document info from SQL database
-g, --group <attr>     group by attribute named attr
-gs,--groupsort <expr> sort groups by <expr>
--sort=date            sort by date, descending
--rsort=date           sort by date, ascending
--sort=ts              sort by time segments
--stdin                read query from stdin
```

此程序（CLI `search`）仅用于测试和调试目的；它不 intended 用于生产环境。

例如，要搜索词 technical 和 writer，并将结果限制为仅三个，`search` 以以下选项运行：

```
./bin/search -i film_main -e 'technical writer' -l 3
Sphinx 0.9.9-id64-release (r2117)
Copyright (c) 2001-2009, Andrew Aksyonoff

using config file '/usr/local/sphinx/etc/sphinx.conf'...
index 'film_main': query 'technical writer':
returned 76 matches of 76 total in 0.007 sec

displaying matches:
1. document=19, weight=2582
   film_id=19
   title=AMADEUS HOLY
   description=A Emotional Display of a Pioneer And a Technical Writer who must Battle a Man in A Baloon
2. document=43, weight=2582
   film_id=43
   title=ATLANTIS CAUSE
   description=A Thrilling Yarn of a Feminist And a Hunter who must Fight a Technical Writer in A Shark Tank
3. document=44, weight=2582
   film_id=44
   title=ATTACKS HATE
   description=A Fast-Paced Panorama of a Technical Writer And a Mad Scientist who must Find a Feminist in An Abandoned Mine Shaft

words:
1. 'technical': 76 documents, 76 hits
2. 'writer': 76 documents, 76 hits
```

如你所见，Sphinx 不仅找到结果，还提供有关搜索的信息，例如找到内容的权重，以及所有找到结果的摘要。

或者，假设你只想在标题列中搜索确切短语 *攻击仇恨*，且不对结果数量设限：
