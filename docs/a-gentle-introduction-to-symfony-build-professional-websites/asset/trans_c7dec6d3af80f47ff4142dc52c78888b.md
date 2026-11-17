

在此配置中，共有六个部分。其中四个表示视图（list、filter、new 和 edit），另外两个是“虚拟部分”（fields 和 form），仅用于配置目的。
以下各部分将详细说明此配置文件中可用的所有参数。

## 生成器配置

生成器配置文件非常强大，可让你以多种方式修改生成的管理界面。但这种功能需要付出代价：整体语法描述冗长，需要阅读和学习，使得本章成为本书中篇幅最长的章节之一。
本节的示例将基于 BlogComment 类定义，对文章管理模块和评论管理模块进行调整。通过运行 propel:generate-admin 任务来创建后者：

```
Listing 14-13
$ php symfony propel:generate-admin backend BlogComment --module=comment
```

### 图 14-4 - 管理生成器速查表

![](img/0f886a7f4cbcc3939be96e985ca35ff4_237_0.png)

### 字段

默认情况下，列表视图的列是 schema.yml 中定义的列。新建和编辑视图的字段是与模型关联的表单（BlogArticleForm）中定义的字段。通过 generator.yml，你可以选择显示哪些字段、隐藏哪些字段，以及添加自己的字段——即使它们在对象模型中没有直接对应关系。

### 字段设置

管理生成器会为 schema.yml 文件中的每个列创建一个字段。在 fields 键下，你可以修改每个字段的显示、格式化等方式。例如，清单 14-5 中显示的字段设置为 title 字段定义了自定义标签类和输入类型，并为 content 字段定义了标签和提示。以下各部分将详细描述每个参数的工作方式。

### 清单 14-5 - 为列设置自定义标签

```
config:
  fields:
    title:
      label: Article Title
      attributes: { class: foo }
    content: { label: Body, help: Fill in the article body }
```

除了对所有视图的默认定义外，你还可以为特定视图（list、filter、form、new 和 edit）覆盖字段设置，如清单 14-6 所示。

### 清单 14-6 - 按视图覆盖全局设置

```
config:
  fields:
    title: { label: Article Title }
    content: { label: Body }

  list:
    fields:
      title: { label: Title }

  form:
    fields:
      content: { label: Body of the article }
```

这是一个一般原则：在 fields 键下为整个模块设置的任何设置，都可以被特定视图区域覆盖。覆盖规则如下：

- new 和 edit 继承自 form，而 form 继承自 fields
- list 继承自 fields
- filter 继承自 fields

### 将字段添加到显示中

你在 fields 部分中定义的字段，可以在每个视图中以多种方式显示、隐藏、排序和分组。display 键用于此目的。例如，要安排评论模块的字段，请使用清单 14-7 的代码。

### 清单 14-7 - 选择要显示的字段，在 modules/comment/config/generator.yml 中

```
config:
  fields:
    article_id: { label: Article }
    created_at: { label: Published on }
    content: { label: Body }

  list:
    display: [id, blog_article_id, content]

  form:
    display:
      NONE: [blog_article_id]
      Editable: [author, content, created_at]
```

列表随后将显示三列，如图 14-5 所示，而新建和编辑表单将显示四个字段，组合成两组，如图 14-6 所示。

### 图 14-5 - 评论模块列表视图中的自定义列设置

| | Id | 博客文章 | 内容 | 操作 |
|---|---|---|---|---|
| ☐ | 1 | 1 | First！ | 编辑 删除 |
| ☐ | 2 | 1 | 哎太遗憾了，我想抢个第一！ | 编辑 删除 |
| ☐ | 3 | 1 | 这是一个非常棒的博客。 | 编辑 删除 |
| ☐ | 4 | 2 | 精彩故事！ | 编辑 删除 |
| ☐ | 5 | 2 | 你好 Fabien | 编辑 删除 |
| **5 条结果** | | | | |
| 选择操作 ▼ | 执行 | + 新建 | | |

### 图 14-6 - 评论模块编辑视图中的字段分组

### 编辑评论

| 字段 | 值 |
|---|---|
| 博客文章 | 欢迎来到 symfony 博客！▼ |

### 可编辑

| 作者 | Benoît |
| 内容 | 这是一个非常棒的博客。 |

| 发布于 | 04 ▼ / 01 ▼ / 2010 ▼ 17 ▼ : 10 ▼ |

| ✖ 删除 | 返回列表 | 保存 |

你可以以两种方式使用 display 设置：

- 对于列表视图：将字段放入简单数组中，以选择要显示的列及其出现顺序。
- 对于表单、新建和编辑视图：使用关联数组将字段分组，组名作为键，或使用 `NONE` 表示无名称的组。值仍然是有序列名的数组。请务必列出表单类引用的所有必需字段，否则可能会出现一些意外的验证错误（参见第 10 章）。

### 自定义字段

事实上，在 generator.yml 中配置的字段甚至不需要对应 schema 中定义的实际列。如果相关类提供自定义 getter，则可以将其用作列表视图的字段；如果存在 getter 和/或 setter，则也可以在编辑视图中使用。例如，你可以用类似清单 14-8 中的 getNbComments() 方法来扩展 BlogArticle 模型。

*清单 14-8 - 在模型中添加自定义 Getter，在 lib/model/BlogArticle.php 中*

```
public function getNbComments()
{
    return $this->countBlogComments();
}
```

此后，nb_comments 将作为生成模块中的一个字段可用（注意，getter 使用字段名称的 camelCase 版本），如清单 14-9 所示。

*清单 14-9 - 自定义 Getter 为管理模块提供额外列，在 backend/modules/article/config/generator.yml 中*

```
config:
  list:
    display: [title, blog_author, blog_category, nb_comments]
```

文章模块的生成列表视图如图 14-07 所示。

*图 14-07 - 文章模块列表视图中的自定义字段*

![](img/0f886a7f4cbcc3939be96e985ca35ff4_240_0.png)

### 局部字段

模型中的代码必须与表现层独立。先前提到的 getArticleLink() 方法示例不遵循这一分层分离原则，因为一些视图代码出现在了模型层中。事实上，如果尝试使用此配置，链接将默认被转义并显示为 <a> 标签。为了以正确方式实现相同目标，最好将输出自定义字段 HTML 的代码放在一个局部模板中。幸运的是，如果你声明一个以下划线开头的字段名，管理生成器允许这样做。在这种情况下，应按照清单 14-12 的方式修改清单 14-11 中的 generator.yml 文件。

*清单 14-12 - 局部模板可用作额外列——使用 _ 前缀*

```
config:
  list:
    display: [id, _article_link, created_at]
```

要使其工作，必须在 modules/comment/templates/ 目录中创建 _article_link.php 局部模板，如清单 14-13 所示。

### 清单 14-13 - 列表视图的局部模板示例，在 modules/comment/templates/_article_link.php 中

```
<?php echo link_to($BlogComment->getBlogArticle()->getTitle(),
  'blog_article_edit', $BlogComment->getBlogArticle()) ?>
```

请注意，局部字段的局部模板可以通过以类命名的变量访问当前对象（本示例中为 $BlogComment）。

### 图 14-08 - 文章模块列表视图中的局部字段

| | Id | 文章链接 | 内容 | 操作 |
|---|---|---|---|---|
| | 1 | 欢迎来到 symfony 博客！ | First！ | 编辑 删除 |
| | 2 | 欢迎来到 symfony 博客！ | 哎太遗憾了，我想抢个第一！ | 编辑 删除 |
| | 3 | 欢迎来到 symfony 博客！ | 这是一个非常棒的博客。 | 编辑 删除 |
| | 4 | Life is beautiful | 精彩故事！ | 编辑 删除 |
| | 5 | Life is beautiful | 你好 Fabien | 编辑 删除 |

5 条结果

选择操作 执行 新建

已遵循分层分离。如果你习惯于遵循分层分离，最终将获得更易维护的应用程序。

如果需要自定义局部字段的参数，请像处理普通字段一样，在 field 键下进行操作。只是不要在键中包含前导下划线 (_)——示例请参见清单 14-14。

### 清单 14-14 - 局部字段属性可在 fields 键下自定义

```
config:
  fields:
    article_link: { label: Article }
```

如果你的局部模板中逻辑过于臃肿，可能希望将其替换为组件。将 _ 前缀更改为 ~，即可定义组件字段，如清单 14-15 所示。

### 清单 14-15 - 组件可用作额外列——使用 ~ 前缀

```
config:
  list:
    display: [id, ~article_link, created_at]
```

在生成的模板中，这将导致对当前模块的 articleLink 组件进行调用。

