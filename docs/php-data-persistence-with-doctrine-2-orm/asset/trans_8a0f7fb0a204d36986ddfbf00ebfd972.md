

上面所示的代码会对 ID 值为 `1` 的 `Post` 实体进行两次修改。在两次更改都应用后，`value` 列的值为 `3`。`$em->clear()` 语句在这里很重要：如果省略它，我们就会自己产生一个 `OptimisticLockException`。原因是，将标题更改为“New title”并刷新实体管理器会在数据库中将该实体的版本值加一。然而，RAM 中 `Post` 实体对象中存储的值仍然是旧值 `1`，因此现在已过时——它不会自动更新到最新的版本值。因此，再次尝试修改标题会因 `OptimisticLockException` 而失败。如果我们尝试持久化对实体的更改，而该实体在此期间已被其他人修改，情况也是如此。如何处理 `OptimisticLockException` 情况，完全取决于应用程序开发者。

## 8 Doctrine 查询语言

### 8.1 简介

在本书前面部分，我们学习了仓库，即特定类型实体的容器。它们用于根据特定条件查找实体、执行更新或删除等操作。它们借助查找器方法来完成工作，这些查找器方法是使用 Doctrine 自身的实体查询语言 DQL（Doctrine 查询语言）实现的。确切地说，DQL 不绑定于查找器方法或仓库，不过，通常人们主要希望将所有 DQL 语句都放在那里，以保持条理清晰。

DQL 本身是一种用于查询实体的语言。它看起来很像 SQL——这使得学习 DQL 更容易——但它不是 SQL。虽然 DQL 语句可以像这样写成字符串：

```
<?php
// [..]
$query = $em->createQuery(
	'SELECT u FROM Entity\User u WHERE u.lastName = "Mustermann"'
);

$users = $query->getResult();  
```

但使用 `query builder` 更加方便，尤其是在构建动态查询时：

```
<?php
// [..]
$qb = $this->_em->createQueryBuilder();

$qb->select('u')
	->from('Entity\User', 'u')
	->where($qb->expr()->eq('u.lastName', '?1'))
	->setParameter(1, "Mustermann");

$users = $qb->getQuery()->getResult();
```

我们假设 `$this->_em` 持有对实体管理器的引用（对于每个扩展 `Doctrine\ORM\EntityRepository` 的仓库都是如此）。实体管理器能够提供查询构建器，而查询构建器又可以用于以编程方式构建查询。得益于其流畅的接口，代码看起来非常优雅。与第一个示例相比，我们还使用了值参数和 `Expr` 类，我们将在一分钟后详细介绍。

### 8.2 检索结果

执行查询时，有多种检索结果的选项。在查询对象上调用 `getResult()` 时，会返回一个包含所有匹配实体对象的 PHP 数组。或者，可以使用 `getArrayResult()` 以数组形式获取所有数据。不会返回对象，只会返回一个容器数组中包含的所有实体数据数组。在处理较大数据集或不需要对象进行处理的简单显示任务时，这非常有用。`getScalarResult()` 会创建类似的结果，但完全是扁平的，完全不嵌套。当只需要单个结果时，调用 `getSingleResult()` 或 `getSingleScalarResult()` 即可。如果在未找到匹配项时希望返回 null，可以使用 `getOneOrNullResult()` 方法。

如果查询选择的不仅仅是实体，那么返回的结果集就是所谓的“混合”结果——它既包含对象，也包含标量值：

```
<?php
// [..]
$qb = $this->_em->createQueryBuilder();

$qb->select('u')
	->addSelect($qb->expr()->concat('u.firstName', 'u.lastName'))
	->from('Entity\User', 'u')
	->where($qb->expr()->eq('u.lastName', '?1'))
	->setParameter(1, "Mustermann");

$users = $qb->getQuery()->getResult();
```

在这个查询中，我们不仅检索实体，还将用户的名和姓连接起来。查询结果如下所示：

```
array 
	[0]
		[0] => Object
		[1] => "Max Mustermann"
	[1]
		// ..
```

通过 `setFirstResult($offset)` 和 `setMaxResults($limit)` 可以限制结果集，例如在构建分页功能时。

Doctrine 2 提供的另一个功能是检索部分对象，即仅从数据库部分重建的实体。要检索部分对象，需要使用特殊语法：

```
<?php
// [..]
$qb = $this->_em->createQueryBuilder();

$qb->select('partial u.{id, firstName}')
	->from('Entity\User', 'u')
	->where($qb->expr()->eq('u.lastName', '?1'))
	->setParameter(1, "Mustermann");

$users = $qb->getQuery()->getResult();
```

这样，我们会得到 `User` 对象，它们是从数据库部分重建的。如果省略 `partial` 语法而仅列出单个字段，否则结果将是一个不含对象的普通数组：

```
array(1) { 
	[0]=> 
		array(2) { 
			["id"]=> int(1) 
			["firstName"]=> string(3) "Max" 
		} 
}
```

在部分对象定义中始终包含标识符（本例中为 `id`）非常重要。否则会抛出异常。

虽然部分对象非常有用，例如在调整应用程序性能时，但也可能带来问题。处理部分对象的代码需要意识到，返回的不是“真实”实体，某些字段或关联可能不可用。必须小心使用部分对象。

### 8.3 构建基本查询

查询构建器为查询的不同部分提供了方法，例如上面所示的方法：

*   `public function select($select = null);`
*   `public function delete($delete = null, $alias = null);`
*   `public function update($update = null, $alias = null);`
*   `public function set($key, $value);`
*   `public function from($from, $alias = null);`
*   `public function where($where);`
*   `public function andWhere($where);`
*   `public function orWhere($where);`
*   `public function groupBy($groupBy);`
*   `public function addGroupBy($groupBy);`
*   `public function having($having);`
*   `public function andHaving($having);`
*   `public function orHaving($having);`
*   `public function orderBy($sort, $order = null);`
*   `public function addOrderBy($sort, $order = null);`

像上面所示的表达式是使用 `Expr` 对象构建的，该对象在调用查询构建器的 `expr()` 方法时提供。`Expr` 对象提供多种方法来构建表达式：

*   `public function andX($x = null);`
*   `public function orX($x = null);`
*   `public function eq($x, $y);`
*   `public function neq($x, $y);`
*   `public function lt($x, $y);`
*   `public function lte($x, $y);`
*   `public function gt($x, $y);`
*   `public function gte($x, $y);`
*   `public function isNull($x);`
*   `public function isNotNull($x);`
*   `public function prod($x, $y);`
*   `public function diff($x, $y);`
*   `public function sum($x, $y);`
*   `public function quot($x, $y);`
*   `public function exists($subquery);`
*   `public function all($subquery);`
*   `public function some($subquery);`
*   `public function any($subquery);`
*   `public function not($restriction);`
*   `public function in($x, $y);`
*   `public function notIn($x, $y);`
*   `public function like($x, $y);`
*   `public function between($val, $x, $y);`
*   `public function trim($x);`
*   `public function concat($x, $y);`
*   `public function substr($x, $from, $len);`
*   `public function lower($x);`
*   `public function upper($x);`
*   `public function length($x);`
*   `public function avg($x);`
*   `public function max($x);`
*   `public function min($x);`
*   `public function abs($x);`
*   `public function sqrt($x);`
*   `public function count($x);`
*   `public function countDistinct($x);`

