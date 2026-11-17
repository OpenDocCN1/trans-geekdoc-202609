

- $comment->getArticle(): 获取相关 Article 对象
- $comment->getArticleId(): 获取相关 Article 对象的 ID
- $comment->setArticle($article): 定义相关 Article 对象
- $comment->setArticleId($id): 通过 ID 定义相关 Article 对象
- $article->getComments(): 获取相关 Comment 对象

getArticleId() 和 setArticleId() 方法表明，你可以将 article_id 列视为常规列并手动设置关系，但它们并不十分有趣。面向对象方法的优势在其他三个方法中更为明显。清单 8-9 展示了如何使用生成的设置器。

## 清单 8-9 - 外键被翻译为特殊设置器

```
$comment = new Comment();
$comment->setAuthor('Steve');
$comment->setContent('Gee, dude, you rock: best article ever!');

// Attach this comment to the previous $article object
$comment->setArticle($article);

// Alternative syntax
// Only makes sense if the object is already saved in the database
// $comment->setArticleId($article->getId());
```

清单 8-10 展示了如何使用生成的获取器。它还演示了如何在模型对象上链式调用方法。

## 清单 8-10 - 外键被翻译为特殊获取器

```
// Many to one relationship
echo $comment->getArticle()->getTitle();
=> My first article
echo $comment->getArticle()->getContent();
=> This is my very first article.
Hope you enjoy it!

// One to many relationship
$comments = $article->getComments();
```

getArticle() 方法返回一个 Article 类的对象，该对象可使用 getTitle() 访问器。这比自己执行连接要好得多，后者可能需要几行代码（从 $comment->getArticleId() 调用开始）。

清单 8-10 中的 $comments 变量包含一个 Comment 类对象的数组。你可以使用 $comments[0] 显示第一个，或者使用 foreach ($comments as $comment) 遍历集合。

## 保存和删除数据

通过调用 new 构造函数，你创建了一个新对象，但不是 blog_article 表中的实际记录。修改对象对数据库也没有影响。为了将数据保存到数据库，你需要调用对象的 save() 方法。

```
$article->save();
```

ORM 足够智能，能够检测对象之间的关系，因此保存 $article 对象也会保存相关的 $comment 对象。它还知道保存的对象是否在数据库中有现有的对应项，因此对 save() 的调用有时会被翻译为 SQL 中的 INSERT，有时则是 UPDATE。主键由 save() 方法自动设置，因此保存后，你可以使用 $article->getId() 检索新主键。

你可以通过调用 isNew() 检查对象是否为新对象。如果你想知道对象是否已修改并值得保存，请调用其 isModified() 方法。

如果你读到关于文章的评论，可能会改变对在互联网上发表文章的看法。如果你不欣赏文章评论者的反讽，可以使用 delete() 方法轻松删除评论，如清单 8-11 所示。

## 清单 8-11 - 使用相关对象上的 delete() 方法从数据库中删除记录

```
foreach ($article->getComments() as $comment)
{
    $comment->delete();
}
```

## 按主键检索记录

如果知道特定记录的主键，请使用表类的 find() 类方法获取相关对象。

```
$article = Doctrine_Core::getTable('Article')->find(7);
```

schema.yml 文件将 id 字段定义为 blog_article 表的主键，因此此语句实际将返回 id 为 7 的文章。由于你使用了主键，你知道只会返回一条记录；$article 变量包含一个 Article 类的对象。

在某些情况下，主键可能包含多个列。在这种情况下，find() 方法接受多个参数，每个主键列对应一个参数。

## 使用 Doctrine_Query 检索记录

当你想要检索多条记录时，需要调用要检索对象所对应表类的 createQuery() 方法。例如，要检索 Article 类的对象，请调用 Doctrine_Core::getTable('Article')->createQuery()->execute()。

execute() 方法的第一个参数是一个参数数组，即用于替换查询中找到的任何占位符的值数组。

空的 Doctrine_Query 返回该类的所有对象。例如，清单 8-12 所示的代码检索所有文章。

## 清单 8-12 - 使用 createQuery() 的空查询通过 Doctrine_Query 检索记录

```
$q = Doctrine_Core::getTable('Article')->createQuery();
$articles = $q->execute();
```

```
// Will result in the following SQL query
SELECT b.id AS b__id, b.title AS b__title, b.content AS b__content,
b.created_at AS b__created_at, b.updated_at AS b__updated_at FROM
blog_article b
```

## 水合

对 ->execute() 的调用实际上比简单的 SQL 查询强大得多。首先，SQL 针对你选择的 DBMS 进行了优化。其次，传递给 Doctrine_Query 的任何值在集成到 SQL 代码之前都会被转义，从而防止 SQL 注入风险。第三，该方法返回对象数组，而不是结果集。ORM 会根据数据库结果集自动创建并填充对象。此过程称为水合（hydrating）。

对于更复杂的对象选择，你需要 WHERE、ORDER BY、GROUP BY 等 SQL 语句的等价物。Doctrine_Query 对象针对所有这些条件都有相应的方法和参数。例如，要获取 Steve 撰写的所有评论并按日期排序，请按清单 8-13 所示构建 Doctrine_Query。

## 清单 8-13 - 使用 createQuery() 的带条件 Doctrine_Query 通过 Doctrine_Query 检索记录

```
$q = Doctrine_Core::getTable('Comment')
->createQuery('c')
->where('c.author = ?', 'Steve')
->orderBy('c.created_at ASC');
$comments = $q->execute();

// Will result in the following SQL query
SELECT b.id AS b_id, b.article_id AS b__article_id, b.author AS b__author, b.content AS b__content, b.created_at AS b__created_at,
b.updated_at AS b__updated_at FROM blog_comment b WHERE (b.author = ?)
ORDER BY b.created_at ASC
```

表 8-1 比较了 SQL 语法与 Doctrine_Query 对象语法。

## 表 8-1 - SQL 和 Criteria 对象语法

| SQL | Criteria |
|---|---|
| WHERE column = value | ->where('acolumn = ?', 'value') |
| **其他 SQL 关键字** | |
| ORDER BY column ASC | ->orderBy('acolumn ASC') |
| ORDER BY column DESC | ->addOrderBy('acolumn DESC') |
| LIMIT limit | ->limit(limit) |
| OFFSET offset | ->offset(offset) |
| FROM table1 LEFT JOIN table2 ON table1.coll = table2.col2 | ->leftJoin('a.Model2 m') |
| FROM table1 INNER JOIN table2 ON table1.coll = table2.col2 | ->innerJoin('a.Model2 m') |

清单 8-14 展示了另一个带有多个条件的 Doctrine_Query 示例。它检索 Steve 在包含单词“enjoy”的文章上发表的所有评论，并按日期排序。

## 清单 8-14 - 使用 createQuery() 的带条件 Doctrine_Query 通过 Doctrine_Query 检索记录的另一个示例

```
$q = Doctrine_Core::getTable('Comment')
 ->createQuery('c')
 ->where('c.author = ?', 'Steve')
 ->leftJoin('c.Article a')
 ->andWhere('a.content LIKE ?', '%enjoy%')
 ->orderBy('c.created_at ASC');
$comments = $q->execute();
```

```
// Will result in the following SQL query
SELECT b.id AS b__id, b.article_id AS b__article_id, b.author AS
b__author, b.content AS b__content, b.created_at AS b__created_at,
b.updated_at AS b__updated_at, b2.id AS b2__id, b2.title AS b2__title,
b2.content AS b2__content, b2.created_at AS b2__created_at, b2.updated_at
AS b2__updated_at FROM blog_comment b LEFT JOIN blog_article b2 ON
b.article_id = b2.id WHERE (b.author = ? AND b2.content LIKE ?) ORDER BY
b.created_at ASC
```

正如 SQL 是一种允许你构建非常复杂查询的简单语言一样，Doctrine_Query 对象可以处理任何复杂程度的条件。但由于许多开发人员首先用 SQL 思考，然后再将条件转换为面向对象逻辑，因此 Doctrine_Query 对象起初可能难以理解。理解它的最佳方式是从示例和示例应用程序中学习。例如，symfony 项目网站充满了 Doctrine_Query 构建示例，将从多个方面启发你。

每个 Doctrine_Query 实例都有一个 count() 方法，它只计算查询的记录数并返回一个整数。由于没有对象可返回，在这种情况下不会发生水合过程，且 count() 方法比 execute() 更快。

表类还提供 findAll()、findBy*() 和 findOneBy*() 方法，它们是构建 Doctrine_Query 实例、执行它们并返回结果的快捷方式。

最后，如果你只想要返回的第一个对象，请用 fetchOne() 调用替换 execute()。当你知道 Doctrine_Query 只会返回一个结果时可能会出现这种情况，其优势在于该方法返回一个对象而不是对象数组。

> 当 execute() 查询返回大量结果时，你可能希望在响应中只显示其中一个子集。Symfony 提供了一个名为 sfDoctrinePager 的分页类，它自动化了结果的分页。

## 使用原始 SQL 查询

有时，你不想检索对象，而只想获取数据库计算的合成结果。例如，要获取所有文章的最新创建日期，检索所有文章并循环遍历数组没有意义。你更愿意让数据库只返回结果，因为它会跳过对象水合过程。

另一方面，你不想直接调用 PHP 的数据库管理命令，因为那样会失去数据库抽象的好处。这意味着你需要绕过 ORM（Doctrine），但不能绕过数据库抽象（PDO）。

使用 PHP 数据对象查询数据库需要执行以下步骤：

- 1. 获取数据库连接。
- 2. 构建查询字符串。
- 3. 由此创建语句。
- 4. 遍历语句执行产生的结果集。

如果这对你来说像天书一样，清单 8-15 中的代码可能会更明确。

