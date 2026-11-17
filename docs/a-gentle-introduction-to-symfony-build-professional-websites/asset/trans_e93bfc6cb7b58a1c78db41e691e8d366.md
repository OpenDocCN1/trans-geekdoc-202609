

## 对列表进行排序

在列表视图中，表格标题是超链接，可用于重新排序列表，如图 14-18 所示。这些标题在表格布局和堆叠布局中均会显示。单击这些链接会带排序参数重新加载页面，从而相应重新排列列表顺序。

图 14-14 - 列表视图的表格标题为排序控件

![](img/0f886a7f4cbcc3939be96e985ca35ff4_248_0.png)

你可以复用语法来指向按某一列直接排序的列表：

```
<?php echo link_to('Comment list by date',
'@blog_comment?sort=created_at&sort_type=desc' ) ?>
```

你还可以直接在 generator.yml 文件中为列表视图定义默认排序顺序。语法遵循清单 14-24 给出的示例。

清单 14-24 - 在列表视图中设置默认排序字段

```
config:
  list:
    sort: created_at
    # Alternative syntax, to specify a sort order
    sort: [created_at, desc]
```

> 仅对应实际列的字段才会转换为排序控件——而非自定义字段或部分字段。

## 自定义分页

生成的后台能够有效处理甚至大型表格，因为列表视图默认使用分页。当表格中实际行数超过每页最大行数时，分页控件会出现在列表底部。例如，图 14-19 显示了表格中包含六条测试评论但每页显示限制为五条评论的评论列表。分页确保了良好的性能，因为只有显示的行会从数据库中实际检索，也确保了良好的可用性，因为即使是包含数百万行的表格也可以由后台模块管理。

图 14-15 - 长列表上会出现分页控件

![](img/0f886a7f4cbcc3939be96e985ca35ff4_249_0.png)

你可以使用 max_per_page 参数自定义每页显示的记录数量：

```
Listing 14-34
config:
  list:
    max_per_page: 5
```

## 使用连接加速页面传递

默认情况下，后台生成器使用简单的 doSelect() 来检索记录列表。但是，如果在列表中使用关联对象，显示列表所需的数据库查询数量可能会迅速增加。例如，如果你想在评论列表中显示文章名称，则列表中的每篇文章都需要额外查询来检索关联的 BlogArticle 对象。因此，你可能希望强制分页器使用 doSelectJoinXXX() 方法来优化查询数量。这可以通过 peer_method 参数指定。

```
Listing 14-35
config:
  list:
    peer_method: doSelectJoinBlogArticle
```

第 18 章更详细地解释了连接的概念。

## 新建和编辑视图的特定自定义

在新建或编辑视图中，用户可以修改新记录或给定记录的每个列的值。默认情况下，后台生成器使用的表单是与模型关联的表单：BlogArticle 模型对应 BlogArticleForm。你可以通过在 form 条目下定义类（如清单 14-25 所示）来自定义要使用的类。

清单 14-25 - 自定义新建和编辑视图中使用的表单类

```
Listing 14-36
config:
  form:
    class: BackendBlogArticleForm
```

使用自定义表单类允许自定义后台生成器使用的所有小部件和验证器。然后可以使用默认表单类，并专门为前端应用程序对其进行自定义。

你还可以直接在 generator.yml 配置文件中自定义表单的标签、帮助消息和布局（如清单 14-26 所示）。

清单 14-26 - 自定义表单显示

```
config:
  form:
    display:
      NONE: [article_id]
      Editable: [author, content, created_at]
    fields:
      content: { label: body, help: "The content can be in the Markdown
format" }
```

## 处理部分字段

部分字段可以在新建和编辑视图中使用，就像在列表视图中一样。

## 处理外键

如果你的架构定义了表关系，生成的后台模块将利用此关系并提供更多自动化控件，从而大大简化关系管理。

## 一对多关系

后台生成器会处理 1-n 表关系。如前文图 14-1 所示，blog_comment 表通过 blog_article_id 字段与 blog_article 表相关联。如果你使用后台生成器初始化 BlogComment 类的模块，编辑视图将自动将 blog_article_id 显示为下拉列表，列出 blog_article 表中可用记录的 ID（再次查看图 14-9 以获取示意图）。

如果你需要在文章模块中显示与文章相关的评论列表（n-1 关系），也是如此。

## 多对多关系

Symfony 也开箱即用地处理 n-n 表关系，如图 14-16 所示。

图 14-16 - 多对多关系

![](img/0f886a7f4cbcc3939be96e985ca35ff4_250_0.png)

通过自定义用于渲染关系的小部件，你可以微调字段的渲染效果（如图 14-17 所示）：

图 14-17 - 多对多关系的可用控件

![](img/0f886a7f4cbcc3939be96e985ca35ff4_251_0.png)

## 添加交互操作

后台模块允许用户执行常规 CRUD 操作，但你也可以添加自己的交互操作或限制视图的可能交互操作。例如，清单 14-27 所示的交互定义授予对文章模块所有默认 CRUD 操作的访问权限。

清单 14-27 - 在 backend/modules/article/config/generator.yml 中为每个视图定义交互操作

```
Listing 14-38
config:
  list:
    title: List of Articles
    object_actions:
      _edit: ~
      _delete: ~
    batch_actions:
      _delete: ~
    actions:
      _new: ~

  edit:
    title: Body of article %%title%%
    actions:
      _delete: ~
      _list: ~
      _save: ~
      _save_and_add: ~
```

在列表视图中，有三个操作设置：每个对象可用的操作（object_actions）、对象选择可用的操作（batch_actions）以及整个页面可用的操作（actions）。清单 14-27 中定义的列表交互操作渲染效果如图 14-18 所示。每一行显示一个编辑记录的按钮和一个删除记录的按钮，此外每行还有一个复选框用于删除选定的记录。在列表底部，有一个按钮允许创建新记录。

图 14-18 - 列表视图中的交互操作

| Id | 博客文章 | 内容 | 操作 |
|---|---|---|---|
| 1 | 1 | 第一！ | 编辑 删除 |
| 2 | 1 | 哎，太糟糕了，我想当第一个！ | 编辑 删除 |
| 3 | 1 | 这是一个非常好的博客。 | 编辑 删除 |
| 4 | 2 | 好故事！ | 编辑 删除 |
| 5 | 2 | 你好 Fabien | 编辑 删除 |

5 条结果

选择操作 新建

在新建和编辑视图中，由于一次只编辑一条记录，因此只需要定义一组操作（在 actions 下）。清单 14-27 中定义的编辑交互操作渲染效果如图 14-23 所示。save 和 save_and_add 操作都会将当前编辑保存到记录中，区别在于 save 操作在保存后显示当前记录的编辑视图，而 save_and_add 操作显示一个新视图以添加另一条记录。save_and_add 操作是一个快捷方式，在快速连续添加多条记录时非常有用。至于删除操作的位置，它与其他按钮分开，以便用户不会误点。

以下划线（_）开头的交互名称告诉 symfony 使用与这些交互对应的默认图标和操作。后台生成器理解 _edit、_delete、_new、_list、_save、_save_and_add 和 _create。

图 14-19 - 编辑视图中的交互操作

文章正文 生活真美好

![](img/0f886a7f4cbcc3939be96e985ca35ff4_252_0.png)

但你也可以添加自定义交互操作，在此情况下，你必须指定一个不以下划线开头的名称，以及当前模块中的目标操作，如清单 14-28 所示。

清单 14-28 - 定义自定义交互操作

```
list:
  title: List of Articles
  object_actions:
    _edit: -
```

