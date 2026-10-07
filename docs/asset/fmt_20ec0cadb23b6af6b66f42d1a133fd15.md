
`49 var retrieved User`

`50 db.First(&retrieved)`

`51 fmt.Println("Retrieved", retrieved)`

`52 })`

```
/github.com/juanemuel-tirado/savetheworldwithgo/16_sql/gorm/transactions/example_02/main.go:24 UNIQUE constraint failed: users.id [0.04ms] [rows:0] INSERT INTO 'users' ('name', 'email', 'id') VALUES ('John','newemail',1) Retrieved (1 John newemail)
```

### 18.4 总结

本章引导读者理解如何在任何 Go 项目中使用 SQL 数据库。它详细解释了 Go 标准库提供的工具以及强大的对象关系映射库 `GORM`。本章提供的示例和解释，为那些熟悉 SQL 概念的读者在将其应用到自己的 SQL 解决方案时提供了坚实的背景支持。

## 第 19 章

### NoSQL 数据库

大数据解决方案的采用加速了对新数据库模型的探索。这种探索揭示了经典关系型数据库的局限性，并提出了超越标准查询语言（SQL）和实体-关系模型的新模型。Apache Cassandra 数据库是应用最广泛的 NoSQL 数据库之一。虽然它可能不是使用该数据库开发解决方案的最常用语言，但本章表明，Go 是任何基于 Cassandra 项目的完美候选语言。

## 19.1 CASSANDRA 与 GOQL

Apache Cassandra 数据库是一种 NoSQL 分布式数据库解决方案。它已被应用于对性能和可用性要求要求的场景，并在确保容错性的同时展示了可扩展性。本章的目的并不是解释 Cassandra 是如何工作的。如果读者完全不熟悉 Cassandra，请通过这些文字来说明该数据库与 MySQL 或 PostgreSQL 等经典关系型数据库之间的主要区别。

### 19.1.1 Cassandra 简介绍

从通俗来说，Cassandra 使用我们在经典数据库中可以找到的术语。然而，由于其独特性，Cassandra 用额外的概念扩展了读者可能不熟悉的术语。

- 密钥空间（Keyspaces）包含表，并定义了复制策略等多个属性。
- SQL 数据库中的表（Tables）存储条目集合。但从概念上讲，表只定义了存储的模式（schema）。这是因为表是在具有多个分区的物理节点上实例化的。
- SQL 数据库中的主键（Primary key）是区分表记录与其他目的唯一字段。然而，主键在 Cassandra 中特别重要，因为它们被用于定义表必须存储的位置。它可以由分区键（partition key）和一个聚类键（clustering key）组成。
- 分区键（Partition key）定义了所有行必须具有的主键强制部分。
- 聚类键（Clustering key）定义了如何根据一个或多列在节点中排序数据。
- SQL 数据库中的行是根据唯一主键标识的列的集合。
- 列（Column）是属于行的一种数据类型，由表的模式定义。

图 19.1 展示了键如何用于分布和排序内容。示例表包含了每个用户在一天中不同时间的警报级别历史信息。主键由 `user_id` 和 `time` 列组成。这使得为同一用户在不同时间存储多行成为可能。此外，我们将 `user_id` 定义为该表的分区键。Cassandra 将使用此列的值来决定哪个物理节点必须存储此行。

| user_id | time | level |
| --- | --- | --- |
| 10 | 10:01 | Normal |
| 10 | 11:11 | Warning |
| 10 | 11:13 | Normal |
| 163 | 09:27 | Error |
| 400 | 08:00 | Normal |

![](img/c7dcb))
**图 19.1:** 主键的组件。

在这个示例中，我们将 `user_id` 定义为该表的分区键。Cassandra 将使用此列的值来决定哪个物理节点必须存储此行。

## 19.1.2 建模

Cassandra 中的数据建模与传统的关系型数据库不同。使用传统数据库的建模概念可能会导致糟糕的结果。Cassandra 数据建模规则明确规定，建模数据时要实现的目标是：1) 数据分布在集群中 2) 区分区数量。在 Cassandra 中，写入是廉价的，磁盘空间通常不是问题。主要目标更多与当前的 Cassandra 架构以及它如何实现极其高效且可扩展的查询有关。建模必须考虑到数据将如何被处理。

本节展示了如何使用 Cassandra 对数据关系进行建模。这里提供的解决方案仅供讨论，并引入了在数据建模阶段需要提出的问题，同时邀请读者去探索 Cassandra 的特殊之处。

#### 一对一 (Has-one)

想象一个用户数据库，每个用户有一台笔记本电脑。在关系型数据库中，我们可以有两个不同的实体 `user` 和 `laptop`，并将每台笔记本与其用户关联起来。但在 Cassandra 中，情况并非如此。解决方案取决于这些实体的最终用途。假设我们已经定义了笔记本表和用户表：

# 示例 19.2: 用户和笔记本实体。

```sql
CREATE TABLE users (
  user_id int PRIMARY KEY,
  name text,
  email text);
CREATE TABLE laptops (
  sn int PRIMARY KEY,
  model text,
  memory int);
```

一种解决方案是创建一个额外的表来存储用户与其笔记本电脑之间的关系。下方的 `user_laptop` 表将 `user_id` 设置为主键，这样一个用户只能出现一次。

# 示例 19.3: 使用额外表实现“一对一”关系。

```sql
CREATE TABLE user_laptop (
  user_id int PRIMARY KEY,
```

如果我们想定期获取用户及其笔记本电脑的列表，上述方案是适用的。然而，它允许一台笔记本关联到多个用户。此外，它假设笔记本条目本身重要到可以独立存在。但是，如果笔记本条目始终与用户关联，我们可以定义一种笔记本类型并与用户关联。

## 示例 19.4：使用笔记本类型实现用户与笔记本的关系。

```
CREATE TYPE laptop (
  sn int,
  model text,
  memory int
);
CREATE TABLE users (
  user_id int PRIMARY KEY,
  name text,
  email text,
  laptop frozen<laptop>);
```

现在笔记本是以类型形式与用户关联的，而不是通过表。包含的信息是相同的，但它将成为用户的属性。我们使用 `frozen` 修饰符来表示笔记本的各个字段不能被独立修改。实际上，笔记本字段必须作为一个整体实体重新插入。然而，这种解决方案并不能保证某台笔记本仅由一个用户拥有。如果我们从数据库的角度保证这一点，我们可以维护笔记本表并包含一个 user_id。

## 示例 19.5：保证每台笔记本都有一个唯一的用户。

```
CREATE TABLE users (
  user_id int PRIMARY KEY,
  name text,
  email text);
CREATE TABLE laptop (
  sn int PRIMARY KEY,
  model text,
  memory int,
  user_id int);
```

## 多对 (Has-many)

扩展我们之前关于用户和笔记本的示例，假设现在每个用户可以拥有多台笔记本。使用笔记本类型，我们可以设置每个用户拥有一组笔记本。

## 示例 19.6：使用集合实现用户拥有多台笔记本。

```
CREATE TABLE users (
  user_id int PRIMARY KEY,
  name text,
  email text,
  laptops set<frozen<laptop>>;
```

使用 `set` 集合保证了同一台笔记本不会在同一个用户中出现两次，查询每个用户的笔记本将非常直接。然而，同一台笔记本可以出现在不同的用户中。为了保证每台笔记本只有一个用户，我们可以维护一个带有 `user_id` 的笔记本表。

## 示例 19.7：保证每台笔记本都有一个唯一的用户。

```
CREATE TABLE laptops (
 sn int PRIMARY KEY,
 model text,
 memory int,
 user_id int);
```

注意，主键用于跨节点对表进行分区。如果我们查询该用户的所有笔记本，该查询可以跨集群节点扩展并返回几记录。然而，这将是查找某台笔记本所有者的良好解决方案。

#### 多对多 (Many-to-many)

现在假设笔记本可以被多个用户共享，我们有两个潜在的查询：获取用户的笔记本和获取笔记本的用户。我们创建了两个表来方便这两种操作。

## 示例 19.8：多对多关系中的用户和笔记本。

```
CREATE TABLE user_laptops (
 user_id int,
 sn int,
 PRIMARY KEY (user_id, sn));
 CREATE TABLE laptops_user (
 sn int,
 user_id int,
 PRIMARY KEY (sn, user_id));
```

使用复合主键 (`user_id, sn`) 通过 `user_id` 对表进行分区，然后在分区内部，行按笔记本序列号 `sn` 排序。使用 `SELECT * from user_laptops where user_id=?` 查询用户的笔记本，旨在通过命中单个分区来实现特别的效率。

## 19.1.3 数据库连接

GoCQL 驱动为开发者提供了一个管理 Cassandra 数据库并为官方支持的版本执行 CQL 语句的简单解决方案。本节所示示例假设有一个监听在 `localhost:9042` 的开箱可用 Cassandra 实例。大多数示例假设示例键空间（keyspace）已经可用。

> GoCQL 项目非常动态，在你执行这些示例时，它们可能与你当前使用的 Cassandra 版本不兼容。希望读者能在这些示例中找到足够的信息来克服可能的执行错误。

与其他任何数据库驱动一样，GoCQL 通过会话（sessions）工作，为用户提供发送查询和操作数据所需的连接。`Session` 可以通过 `ClusterConfig` 类型通过 `CreateSession` 方法生成。`ClusterConfig` 类型表示在与集群实例化新实例时使用的配置。

示例 19.9 显示了如何为本地集群实例化一个新的会话`NewCluster` 函数返回一个可以自定义的 `Session`。检查文档以查看所有可能的选项。在示例中，我们设置了使用的键空间、一致性级别和一个分钟的连接超时。可以通过参数传递多个主机，其余节点将自动发现。注意，会话的可能会失败，并且必须关闭以释放资源。

## 示例 19.9：GoCQL 数据库连接。

```go
package main

import (
	"github.com/gocql/gocql"
	"time"
)

const CREATE_TABLE='CREATE TABLE user (
	id int PRIMARY KEY,
	name text,
	email text
)'

func main() {
	cluster := gocql.NewCluster("127.0.0.1:9042")
	cluster.Keyspace = "example"
	cluster.Consistency = gocql.Quorum
	cluster.Timeout = time.Minute
	session, err := cluster.CreateSession()
	if err != nil {
	panic(err)
	}
	defer session.Close()
}
```

## 19.1.4 操作数据

数据操作（创建、更新和删除）使用 `Exec` 方法执行。为了演示，我们创建了一个表并插入了单行。

## 示例 19.10：GoCQL 数据操作。

```go
package main

import (
	"context"
	"github.com/gocql/gocql"
)

const CREATE_TABLE='CREATE TABLE users (
	id int PRIMARY KEY,
	name text,
	email text
)'

const INSERT_QUERY='INSERT INTO users
(id,name,email) VALUES(?,?)'

func main() {
	cluster := gocql.NewCluster("127.0.0.1:9042")
	cluster.Keyspace = "example"
	session, err := cluster.CreateSession()
	if err != nil {
		panic(err)
	}
	defer session.Close()
	ctx := context.Background()
	err = session.Query(CREATE_TABLE).WithContext(ctx).Exec()
	if err != nil {
		panic(err)
	}
	err = session.Query(INSERT_QUERY, "John", "john@gmail.com").WithContext(ctx).Exec()
	if err != nil {
		panic(err)
	}
}
```

## 19.1.5 使用批的 GoCQL 数据管理

CQL 可以批量执行插入、更新和删除查询。批量可以保证原子性并提高性能。19.11 使用批插入了一个新用户并修改了她的邮箱。`Batch` 类型通过 `NewBatch` 方法从当前会话结合上下文获取。该批包含一组表示查询的 `BatchEntry`。该查询集合通过当前会话的 `ExecuteBatch` 作为一个整体执行。

## 示例 19.11：使用批的 GoCQL 数据管理。

```go
package main

import (
	"context"
	"github.com/gocql/gocql"
)

const CREATE_TABLE='CREATE TABLE users (
	id int PRIMARY KEY,
	name text,
	email text
)'

const INSERT_QUERY='INSERT INTO users
(id,name,email) VALUES(?,?)'

const UPDATE_QUERY='UPDATE users SET email=? WHERE id=?'

func main() {
	cluster := gocql.NewCluster("127.0.0.1:9042")
	cluster.Keyspace = "example"
	session, err := cluster.CreateSession()
	if err != nil {
		panic(err)
	}
	defer session.Close()
	ctx := context.Background()
	batch := session.NewBatch(gocql.LoggedBatch)
	batch.Query(INSERT_QUERY, 1, "Jane", "jane@gmail.com")
	batch.Query(UPDATE_QUERY, "jane.new@gmail.com", 1)
	err = session.ExecuteBatch(batch, ctx)
	if err != nil {
		panic(err)
	}
}
```

```go
func main() {
	cluster := gocql.NewCluster("127.0.0.1:9042")
	cluster.Keyspace = "example"
	session, err := cluster.CreateSession()
	if err != nil {
		panic(err)
	}
	defer session.Close()
	ctx := context.Background()
	err := session.Query("CREATE_TABLE").WithContext(ctx).Exec()
	if err != nil {
		panic(err)
	}
	b := session.NewBatch(gocql.UnloggedBatch).WithContext(ctx)
	b.Entries = append(b.Entries, gocql.BatchEntry{
		Stmt: "INSERT_QUERY",
		Args: []interface{}{1, "John", "john@gmail.com"},
	})
	gocql.BatchEntry{
		Stmt: "UPDATE_QUERY",
		Args: []interface{}{"otheremail@email.com", 1},
	})
	err = session.ExecuteBatch(b)
	if err != nil {
		panic(err)
	}
}
```
