
## 表 10-1（续）

| 组件 | 描述 |
|---|---|
| NaradaInsert.php | 该 worker 首先由 fetch worker（NaradaFetch.php）调用，或在通过索引页面 index.php 插入 URL 时被调用。 |
| NaradaIndex.php | 当被请求时，该 worker 检查频率计数器的值，该计数器对应于已存储的网页数量，如果频率计数器超过你在 NaradaConf.php 中指定的数量，它会调用 Sphinx 索引程序重新为包含检索到的网页的表建立 Sphinx 索引。 |
| NaradaSearch.php | 该 worker 由索引页面 index.php 传入搜索词调用。然后它从 Sphinx 获取搜索结果，并从缓存（如果已缓存）或 MySQL 获取内容，并将结果作为 JSON 对象返回给索引页面。 |
| NaradaIndexTimer.php | 根据来自 NaradaConf.php 的全局设置，如果指定的时间量已被超过，该 worker 仅请求索引 worker NaradaIndex.php。这是为了确保索引在某个给定间隔内重新生成。 |
| MySQL | 三个表：元数据表、blob/text 表和 sphinx 计数器表。 |
| 元数据表 url | 用于存储有关网页的信息，例如其 URL、唯一 id、日期等。 |
| blob/text 表 url_content | 与元数据表具有 1:1 关系，存储特定 URL 的网页的实际内容和标题，存储在 TEXT 列中。 |
| Sphinx 全文索引 | 由包含网页的 blob/text 表构建。 |
| memcached | 用于缓存搜索，以便后续搜索使用 memcached 获取内容而不是从数据库检索内容。搜索词越流行，被缓存的可能性越大！ |

内容如何从网页获取、解析、存储然后被索引的流程如下：

- 1. 用户在索引页面的 URL 输入字段中输入 URL 值，并且 URL 值存储在 url 表中。索引页面调用 Narada 类的 insert() 方法，该方法进而通过 Gearman 客户端 API 请求由 insert、NaradaInsert.php 存储 URL。
- 2. insert worker NaradaInsert.php 检查指定 URL 的有效性，然后调用 Narada 方法 store()，该方法进而将 URL 插入 url 表并返回 insert_id（从 insert 返回的 auto_increment id 列的值）。这是 URL 的 ID。如果返回了 ID，insert worker 然后调用 Narada 方法 fetch()，进而导致向 Gearman 请求获取该 URL，由 fetch worker NaradaFetch.php 提供。
- 3. fetch worker `NaradaFetch.php` 获取指定 URL 的网页，然后继续解析页面内容中的任何 URL。对于找到的任何 URL，它使用 Narada 方法 `insert()` 请求插入 URL，进而导致 insert worker 插入 URL 并对该 URL 调用 fetch——因此可以很快看出 insert worker 和 fetch worker 互相喂养并无休止地继续抓取和解析网页！最后，在请求插入找到的任何 URL 之后，是通过调用 Narada 方法 `index()` 请求运行索引器，进而通过 gearmand 请求索引 worker `NaradaIndex.php`。
- 4. 索引 worker `NaradaIndex.php` 如果用于索引的计数达到全局变量 `$GLOBALS['NaradaIndexFrequency']` 确定的值，则运行 Sphinx 索引器。
- 5. 索引计时器不是 worker，而是一个永久运行的程序，它会休眠全局 `$GLOBALS['NaradaIndexTimer']` 的值所持续的时间，然后请求运行索引器。这确保即使活动量低且没有因文档获取而产生的事件驱动索引，索引器也会运行。

搜索功能可以描述如下：

- 1. 用户在主索引页面 `index.php` 上输入搜索词，这会导致通过 Narada 方法 `search()` 请求搜索 worker。这是一个同步方法，它将搜索结果作为 JSON 返回，`index.php` 将其反序列化为 PHP 搜索结果对象。
- 2. 搜索 worker 通过调用 Narada 方法 `searchIndex()` 对 Sphinx 索引执行搜索，然后从 memcached（如果已缓存）或 MySQL 获取文档 ID（指向 `url_content` 表的 id）的内容。然后通过调用 Narada 方法 `getContent()` 将结果缓存以供后续对该词的搜索。然后将结果作为 JSON 返回给调用者，本例中为 `index.php`。

## 搜索引擎应用的数据库表

在构建搜索引擎时，首先要考虑的是如何存储数据。对于此应用，如表 10-1 所示，将有四个数据库表如下：

```
CREATE TABLE url (
  id int NOT NULL auto_increment,
  url_md5 varbinary(32) NOT NULL,
  url varchar(255) NOT NULL,
  created date default NULL,
  last_updated timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,
  PRIMARY KEY  (id),
  UNIQUE KEY url_md5_idx (url_md5)
) ENGINE=InnoDB ;
```

`url` 表将存储检索到的网页的元数据信息。这包括列如页面本身的 URL `url`、URL 的唯一 MD5 值 `url_md5`、最后更新 `last_updated` 和创建日期 `created`，但不包括实际的网页内容。最好将 BLOB 或文本数据保存在单独的表中，这样对元数据类型值的任何查询都不必从包含 TEXT 或 BLOB 的表中检索；合并表会使这些查询性能变慢并需要更多内存。

```
CREATE TABLE url_content (
    id int NOT NULL,
    title varchar(255) NOT NULL default '',
    content blob NOT NULL,
    PRIMARY KEY  (id)
) ENGINE=InnoDB;
```

url_content 表存储标题和实际网页内容。它还具有主键 id，该 id 与 url 表的 id 列直接相关：

```
create table urls_queue (
    url_md5 char(32) NOT NULL default '',
    url     varchar(128) NOT NULL default '',
    last_updated timestamp,
    primary key url_md5 (url_md5)
) ENGINE=InnoDB;
```

sphinx_counter 表用于跟踪索引的最大 ID 值。该表中的 ID（id）值由索引器用于在查询 MySQL 以获取用于索引的内容时提供 SQL 查询的 ID 值。

```
CREATE TABLE sphinx_counter (
    id int NOT NULL,
    max_id int NOT NULL,
    index_name varchar(32) NOT NULL,
    PRIMARY KEY  (id),
    KEY index_name (index_name)
) ENGINE=InnoDB
```

## Sphinx 设置

要使用 Sphinx 全文索引对存储在 MySQL 中的网页进行索引，还必须设置 Sphinx。此示例使用简单的 Sphinx 设置，具有单个分布式索引，该索引有两个 sphinx 代理：一个用于主索引 url，一个用于增量索引 url_delta。

你有两个索引——一个主大索引和一个较小的增量索引——是有原因的：你不想太频繁地对不断增长的大型数据集进行整体重新索引并向其添加更改或增量。由于 Sphinx 具有分布式索引功能，你可以将这两个索引视为单个索引，并且只需要更新较小的增量索引。然后在某个间隔，将增量索引合并到主索引中。

首先要审查的是将包含主索引和增量索引位置的 MySQL 表。索引器使用 sphinx_counter 表中的此位置信息来获取索引所具有的记录的限制或范围。索引器使用此信息来确定索引时应选择哪些数据。

主 url 索引将包含其 id 值小于 sphinx_counter 表中列 max_id 的值的全部记录。增量索引 url_delta 将包含其 id 值从列 sphinx_counter.max_id 的值开始且没有上限的记录。
