

# 为我们的命名空间命名。

它变成了 `PageController.php`。我们确实需要遵守 `.php` 强制性文件扩展名，但由于我想我很长一段时间以来在野外没有见过除了 `.php` 以外的其他东西，所以这没什么好提的。

正如你所看到的，Composer 为了满足 PSR-4 标准对我们施加的最低要求是非常容易实现的。不仅如此，它们也非常合理！剩下的唯一工作就是告诉 Composer 的自动加载器（autoloader）如何找到正确命名的类。

这是通过在 Composer 的配置文件 `composer.json` 中添加一个 autoload 条目来实现的。我们上面的简单示例将产生一个看起来像这样的条目。

```json
{
  "require": {
    ...
  },
  "autoloader": {
    "psr-4": {
      "Vanguard\\": "src/"
    }
  }
}
```

我们在这里所做的只是提供了一个简单的键值对，告诉符合 PSR-4 标准的自动加载器：以 "Vanguard" 命名空间开头的类可以在相对于 `composer.json` 文件本身的 "src/" 目录下找到。

然而，我们的工作还没有完全结束。我们只是告诉了 Composer 我们的 vendor（供应商）命名空间。为了保持合规性（以及功能性！）我们仍然需要考虑在删除 vendor 前缀后剩余的任何子命名空间。在我们上面的示例中，我们的命名空间是 "VanguardController"。一旦我们从列表中删除了 "Vanguard" 前缀，剩下的就只有一个子命名空间，即 "Controller"。PSR-4 告诉我们，它应该直接映射到我们在 `composer.json` 中映射到前缀的目录下的子目录。再次，拼写和大小写在这里是非常重要的。

这引导我们得到了类似这样的文件系统布局。

```text
$PROJECT_ROOT/
composer.json
src/
// 此目录映射到 "Vanguard" 前缀
Controller/
Interface/
ControllerInterface.php
PageController.php
Service/
BlogService.php
Auth/
Strategy/
Acl.php
```

正如你所看到的，即使是遵循 PSR-4 标准的最基本应用，也能得到一个既整洁又又非常有逻辑性的文件系统布局。为了进一步说明，我还包含了一个被称为 "VanguardAuthStrategyAcl" 的类的路径，仅仅是为了展示这里的每个命名空间（"Auth" 和 "Strategy"）如何对应于同名的目录。采用这种方案意味着类的自动加载问题已经得到解决。一如既常，永不重复造轮子是非常非常明智的事。

> 你可以通过其 `composer.json` 文件向 Composer 提供许多选项，但我们将在书的后部分介绍这些内容。

虽然我在这里只展示了一个非常简单的策略，但更常见的情况是“扩展”我们使用的命名空间前缀，以提供项目层面的隔离。如果说 vendor 命名空间代表你（或你的公司），那么第一个子命名空间可以用来指示你正在工作的特定项目。

对上面的示例进行微小的修改，结果将如下所示。

为我们的命名空间命名。

```php
<?php
namespace Vanguard\MyApplication\Controller;

use Vanguard\MyApplication\Service\BlogService;
use Vanguard\MyApplication\Controller\ControllerInterface;
```

```php
class PageController implements ControllerInterface
{
}
```

那里唯一的变化是我在命名空间声明中插入了 “MyApplication”。我们是否应该将所有代码移动到一个新的 “MyApplication” 文件夹中？嗯，如果我们愿意的话可以这样做。如果我们预见到这个特定的项目目录最终将包含多个子项目，那么这样做是有意义的。否则，没有重新组织项目的文件系统布局，我们只需要告诉 Composer 命名空间前缀已经更改。

```json
{
  "require": {
  },

  "autoloader": {
    "psr-4": {
      "Vanguard\\MyApplication\\": "src",
      "Vanguard\\MyPackage\\": "lib/mypackage/"
    }
  }
}
```

为了说明如何适应一个新的子项目，我在自动加载规范中添加了第二个条目；它将命名空间 “VanguardMyPackage”映射到一个新目录。即使你不使用 Composer 来引入和管理外部依赖，只需对自己的代码遵循这些命名空间指南并对 `composer.json` 进行适当修改，自动加载就会变得简单且完全无忧。

既然项目已经有了免费且简单的自动加载解决方案，只需遵循它要求的标准，就能让我们的项目在通往高度清洁和逻辑分离道路道路良好开始，非常就像一个组织良好的 mp3 集合。显然，我无法自动为我们提供“正确”的目录及其相应的子命名空间，但我们对框架的接触极有可能意味着我们已经知道了大多数流行的选择。

# 结论

如果我能把这一章浓缩为五个词，那就是“命名空间一切”。

