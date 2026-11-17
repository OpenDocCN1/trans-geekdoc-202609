
最佳文章列表和最新文章列表。这段代码非常适合作为 partial，如图 7-2 所示。

## 图 7-2 - 在模板中重用 partials

![](img/0f886a7f4cbcc3939be96e985ca35ff4_103_0.png)

和模板一样，partials 是位于 templates/ 目录下的文件，包含嵌入 PHP 的 HTML 代码。partial 文件名始终以下划线 (_) 开头，这有助于将 partials 与模板区分开来，因为它们位于同一个 templates/ 文件夹中。

模板可以包含 partials，无论它们位于同一模块、另一个模块还是全局 templates/ 目录中。使用 include_partial() 辅助函数来包含 partial，并将模块名和 partial 名作为参数指定（但省略前导下划线和尾部 .php），如清单 7-7 所示。

### 清单 7-7 - 在 mymodule 模块的模板中包含 Partial

```php
// Include the frontend/modules/mymodule/templates/_mypartial1.php partial
// As the template and the partial are in the same module,
// you can omit the module name
<?php include_partial('mypartial1') ?>

// Include the frontend/modules/foobar/templates/_mypartial2.php partial
// The module name is compulsory in that case
<?php include_partial('foobar/mypartial2') ?>

// Include the frontend/templates/_mypartial3.php partial
// It is considered as part of the 'global' module
<?php include_partial('global/mypartial3') ?>
```

partials 可以访问常见的 symfony 辅助函数和模板快捷方式。但是，由于 partials 可以从应用程序的任何地方调用，它们无法自动访问在调用包含它们的模板的动作中定义的变量，除非显式地作为参数传递。例如，如果您希望 partial 可以访问 $total 变量，动作必须将其传递给模板，然后由模板将其作为 include_partial() 调用的第二个参数传递给辅助函数，如清单 7-8、7-9 和 7-10 所示。

### 清单 7-8 - 动作定义变量，位于 mymodule/actions/actions.class.php

```php
class mymoduleActions extends sfActions
{
  public function executeIndex()
  {
    $this->total = 100;
  }
}
```

### 清单 7-9 - 模板将变量传递给 Partial，位于 mymodule/templates/indexSuccess.php

```php
<p>Hello, world!</p>
<?php include_partial('mypartial', array('mytotal' => $total)) ?>
```

### 清单 7-10 - Partial 现在可以使用该变量，位于 mymodule/templates/_mypartial.php

```php
<p>Total: <?php echo $mytotal ?></p>
```

目前为止所有辅助函数都通过 <?php echo functionName() ?> 调用。但是 partial 辅助函数只是通过 <?php include_partial() ?> 调用，不带 echo，以便其行为类似于常规的 PHP include() 语句。如果您需要一个返回 partial 内容但不实际显示它的函数，请改用 get_partial()。本章中描述的所有 include_helpers 都有对应的 get_counterpart，可以与 echo 语句一起调用。

提示：动作不仅可以生成模板，还可以返回 partial 或 component。动作类的 renderPartial() 和 renderComponent() 方法有助于提高代码可重用性。此外，它们利用了 partials 的缓存功能（参见第 12 章）。动作中定义的变量将自动传递给 partial/component，除非您将变量关联数组作为方法的第二个参数定义。

```php
public function executeFoo()
{
 // do things
 $this->foo = 1234;
 $this->bar = 4567;

 return $this->renderPartial('mymodule/mypartial');
}
```

在此示例中，partial 将可以访问 $foo 和 $bar。如果动作以以下行结尾：

```php
return $this->renderPartial('mymodule/mypartial', array('foo' =>
$this->foo));
```

那么 partial 将只能访问 $foo。

## 组件

在第 2 章中，第一个示例脚本被分成两部分，以将逻辑与表示分开。就像 MVC 模式适用于动作和模板一样，您可能需要将 partial 分为逻辑部分和表示部分。在这种情况下，您应该使用组件。

组件类似于动作，但速度快得多。组件的逻辑保存在继承自 sfComponents 的类中，位于 actions/components.class.php 文件。其表示保存在 partial 中。sfComponents 类的方法以单词 execute 开头，与动作一样，它们可以以动作传递变量的相同方式将变量传递给其表示部分。用作组件表示的 partial 以组件命名（不带前导 execute，而是使用下划线）。表 7-1 比较了动作和组件的命名约定。

### 表 7-1 - 动作和组件命名约定

| 约定 | 动作 | 组件 |
| --- | --- | --- |
| 逻辑文件 | actions.class.php | components.class.php |
| 逻辑类继承 | sfActions | sfComponents |
| 方法命名 | executeMyAction() | executeMyComponent() |
| 表示文件命名 | myActionSuccess.php | _myComponent.php |

> 就像您可以拆分动作文件一样，sfComponents 类有 sfComponent 对应物，允许使用相同语法的单个组件文件。

例如，假设您有一个侧边栏，显示给定主题的最新新闻头条，具体取决于用户个人资料，并且在多个页面中重复使用。获取新闻头条所需的查询太复杂，无法出现在简单的 partial 中，因此需要将其移动到类似于动作的文件——组件中。图 7-3 说明了此示例。

对于此示例，如清单 7-11 和 7-12 所示，组件将保存在其自己的模块（称为 news）中，但如果从功能角度来看合理，您可以在单个模块中混合组件和动作。

### 图 7-3 - 在模板中使用组件

![](img/0f886a7f4cbcc3939be96e985ca35ff4_105_0.png)

### 清单 7-11 - 组件类，位于 modules/news/actions/components.class.php

```php
<?php

class newsComponents extends sfComponents
{
    public function executeHeadlines()
    {
        // Propel
        $c = new Criteria();
        $c->addDescendingOrderByColumn(NewsPeer::PUBLISHED_AT);
        $c->setLimit(5);
        $this->news = NewsPeer::doSelect($c);

        // Doctrine
        $query = Doctrine::getTable('News')
        ->createQuery()
        ->orderBy('published_at DESC')
        ->limit(5);

        $this->news = $query->execute();
    }
}
```

### 清单 7-12 - Partial，位于 modules/news/templates/_headlines.php

```php
<div>
<h1>Latest news</h1>
<ul>
<?php foreach($news as $headline): ?>
<li>
<?php echo $headline->getPublishedAt() ?>
<?php echo link_to($headline->getTitle(), 'news/show?id='.$headline->getId()) ?>
</li>
<?php endforeach ?>
</ul>
</div>
```

现在，每次在模板中需要组件时，只需调用此内容：

```php
<?php include_component('news', 'headlines') ?>
```

与 partials 一样，组件接受以关联数组形式的其他参数。参数按名称在 partial 中可用，并在组件中通过 $this 对象可用。请参见清单 7-13 获取示例。

### 清单 7-13 - 将参数传递给组件及其模板

```php
// Call to the component
<?php include_component('news', 'headlines', array('foo' => 'bar')) ?>

// In the component itself
echo $this->foo;
=> 'bar'

// In the _headlines.php partial
echo $foo;
=> 'bar'
```

您可以将组件包含在组件中，或在全局布局中，就像任何常规模板一样。与动作一样，组件的 execute 方法可以将变量传递给相关 partial 并可以访问相同的快捷方式。但是，相似之处到此为止。组件不处理安全性或验证，无法从 Internet 调用（只能从应用程序本身调用），并且没有各种返回可能性。这就是为什么组件的执行速度比动作快。

## 插槽

partials 和组件非常适合重用性。但是，在许多情况下，需要代码片段来填充布局中不止一个动态区域。例如，假设您想根据动作的内容在布局的 <head> 部分中添加一些自定义标签。或者，假设布局有一个主要动态区域，由动作的结果填充，还有许多其他较小的区域，它们在布局中定义了默认内容，但可以在模板级别被覆盖。

对于这些情况，解决方案是插槽。基本上，插槽是一个占位符，您可以将其放在任何视图元素中（在布局、模板或 partial 中）。填充此占位符就像设置变量一样。填充代码在响应中全局存储，因此您可以在任何地方定义它（在布局、模板或 partial 中）。只需确保在包含它之前定义插槽，并记住布局在模板之后执行（这是 the
