

## 如果你不喜欢 YAML

YAML 只是一个用于定义 PHP 代码所用设置的接口，因此 YAML 文件中定义的配置最终会被转换为 PHP。浏览完一个应用程序后，检查其缓存的配置（例如，在 cache/frontend/dev/config/ 中）。你将看到与你的 YAML 配置对应的 PHP 文件。你将在本章后面了解更多关于配置缓存的内容。

好消息是，如果你不想使用 YAML 文件，仍然可以手动（使用 PHP 或通过其他格式，如 XML、INI 等）完成配置文件所做的事情。在本书中，你将遇到不使用 YAML 来定义配置的替代方法，甚至会学习如何替换 symfony 配置处理器（在第 19 章）。如果明智地使用这些技巧，它们将使你能够绕过配置文件或定义自己的配置格式。

## 救命，YAML 文件导致我的应用程序崩溃了！

YAML 文件会被解析为 PHP 哈希和数组，然后这些值在应用程序的各个部分中用于修改视图、控制器或模型的行为。很多时候，当 YAML 文件中存在问题时，直到实际需要使用该值时才会被发现。此外，此时抛出的错误或异常通常与 YAML 配置文件没有明显的关联。

如果你的应用程序在配置更改后突然停止工作，你应该检查自己是否犯了粗心的 YAML 编码人员常见的任何错误：

- 你在键和值之间漏掉了空格：

```
Listing 5-11
key1:value1   # A space is missing after the :
```

- 序列中的键缩进方式不一致：

```
Listing 5-12
all:
  key1: value1
  key2: value2   # Indentation is not the same as the other
sequence members
  key3: value3
```

- 键或值中包含保留的 YAML 字符，且没有字符串分隔符：

```
Listing 5-13
message: tell him: go way   # : , [ , ], { and } are reserved in YAML
message: 'tell him: go way'   # Correct syntax
```

- 你正在修改一行注释：

```
Listing 5-14
# key: value   # Will never be taken into account due to the
leading #
```

- 你在同一层级中两次设置了同名键的值：

```
Listing 5-15
key1: value1
key2: value2
key1: value3   # key1 is defined twice, the value is the last
one defined
```

- 你认为该设置采用特殊类型，但实际上它始终是字符串，直到你将其转换为止：

```
income: 12,345  # Until you convert it, this is still a string
```

## 配置文件概览

配置按主题分布在不同的文件中。这些文件包含参数定义或设置。其中一些参数可以在多个层级（项目、应用程序和模块）中被覆盖；有些则特定于某个层级。接下来的章节将讨论与其主题相关的配置文件，第 19 章将讨论高级配置。

## 项目配置

默认情况下有几个项目配置文件。以下是可在 myproject/config/ 目录中找到的文件：

- ProjectConfiguration.class.php：这是任何请求或命令包含的第一个文件。它包含框架文件的路径，你可以更改它以使用不同的安装。有关此文件的高级用法，请参见第 19 章。
- databases.yml：这是你定义数据库访问和连接设置（主机、登录名、密码、数据库名称等）的地方。第 8 章将告诉你更多相关信息。它也可以在应用程序级别被覆盖。
- properties.ini：此文件保存命令行工具使用的一些参数，包括项目名称和远程服务器的连接设置。有关使用此文件的功能概览，请参见第 16 章。
- rsync_exclude.txt, rsync_include.txt：此文件指定在服务器间同步时必须排除和/或包含的目录和文件。在第 16 章中讨论。
- schema.yml：这是 Propel 和 Doctrine（symfony 的 ORM 层）使用的数据访问配置文件。它用于使 ORM 库能够与 symfony 类和你的项目数据协同工作。schema.yml 包含项目关系数据模型的表示。对于 Doctrine，此文件在 config/doctrine/ 中创建。

这些文件主要由外部组件或命令行使用，或者在框架加载任何 YAML 解析程序之前就需要被处理。这就是为什么其中一些文件不使用 YAML 格式的原因。

## 应用程序配置

配置的主要部分是应用程序配置。它在前端控制器（web/ 目录中）中为主配置定义，在应用程序 config/ 目录中的 YAML 文件中定义，在 i18n/ 目录中为国际化文件定义，并在框架文件中为不可见——虽然有用——的附加应用程序配置定义。

## 前端控制器配置

实际上，最初的应用程序配置位于前端控制器中，即请求执行的第一个脚本。请查看清单 5-11 中的默认 web/index.php。

_清单 5-11 - 默认生产前端控制器_

清单 5-17

```php
<?php
require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');

$configuration = ProjectConfiguration::getApplicationConfiguration('frontend', 'prod', false);
sfContext::createInstance($configuration)->dispatch();
```

在定义应用程序名称（frontend）、环境（prod）和调试模式（false）后，在创建上下文和分发之前会调用应用程序配置。因此，应用程序配置类中提供了一些有用的方法：

- $configuration->getRootDir()：项目根目录（通常，应保持其默认值，除非你更改文件结构）。
- $configuration->getApplication()：项目中的应用程序名称。计算文件路径所必需。
- $configuration->getEnvironment()：环境名称（prod、dev、test 或你定义的任何其他特定于项目的环境）。将确定使用哪些配置设置。环境将在本章后面解释。
- $configuration->isDebug()：启用调试模式（详情请参见第 16 章）。

如果你想更改其中任何一个值，可能需要一个额外的前端控制器。下一章将告诉你更多关于前端控制器以及如何创建新控制器的信息。

## 主应用程序配置

主应用程序配置存储在 myproject/apps/frontend/config/ 目录中的文件中：

- app.yml：此文件应包含特定于应用程序的配置；也就是说，定义特定于应用程序的业务或应用逻辑的全局变量，这些变量无需存储在数据库中。税率、运费和电子邮件地址通常存储在此文件中。默认情况下为空。
- frontendConfiguration.class.php：此类引导应用程序，这意味着它执行所有非常基本的初始化以允许应用程序启动。你可以在这里自定义目录结构或添加特定于应用程序的常数（第 19 章提供更多详细信息）。它继承自 sfApplicationConfiguration 类。
- factories.yml：Symfony 定义了自己的类来处理视图、请求、响应、会话等。如果你想使用自己的类，可以在此处指定。第 17 章提供更多信息。
- filters.yml：过滤器是为每个请求执行的代码部分。此文件用于定义要处理哪些过滤器，并且可以针对每个模块进行覆盖。第 6 章更详细地讨论了过滤器。
- routing.yml：路由规则存储在此文件中，这些规则允许将不可读和不可加书签的 URL 转换为“智能”和明确的 URL。对于新应用程序，存在一些默认规则。第 9 章完全关于链接和路由。
- settings.yml：symfony 应用程序的主设置在此文件中定义。你可以在此处指定应用程序是否具有国际化、默认语言、请求超时以及是否启用缓存。通过在此文件中进行一行更改，你可以关闭应用程序以执行维护或升级其组件之一。常见设置及其用途在第 19 章中有描述。

