

## 调试

无论你的编程技巧多么娴熟，最终都会犯错，即使使用 symfony。检测和理解错误是快速应用开发的关键之一。幸运的是，symfony 为开发者提供了多种调试工具。

### Symfony 调试模式

Symfony 具有一种调试模式，有助于简化应用程序的开发和调试。启用后，会发生以下情况：

- 每次请求都会检查配置，因此对任何配置文件的更改都会立即生效，无需清除配置缓存。
- 错误消息以清晰且有用的方式显示完整的堆栈跟踪，以便您可以更高效地找到出错的元素。
- 提供了更多调试工具（例如数据库查询的详细信息）。
- Propel/Doctrine 调试模式也会被激活，因此在调用 Propel/Doctrine 对象时出现的任何错误都将显示通过 Propel/Doctrine 架构的详细调用链。

另一方面，当调试模式关闭时，处理过程如下：

- YAML 配置文件仅被解析一次，然后转换为存储在 `cache/config/` 文件夹中的 PHP 文件。第一次请求之后的每个请求都会忽略 YAML 文件，而改用缓存的配置。因此，请求的处理速度大大加快。
- 如需重新处理配置，必须手动清除配置缓存。
- 请求处理期间发生错误时，将返回代码为 500（Internal Server Error）的响应，不解释问题的内部原因。

调试模式在前端控制器中按应用程序激活。它由传递给 `getApplicationConfiguration()` 方法调用的第三个参数的值控制，如清单 16-8 所示。

*清单 16-8 - 启用调试模式的示例前端控制器，位于 web/frontend_dev.php*

```php
<?php

require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');

$configuration = ProjectConfiguration::getApplicationConfiguration('frontend', 'dev', true);
sfContext::createInstance($configuration)->dispatch();
```

> 在生产服务器上，您不应启用调试模式，也不应保留任何启用了调试模式的前端控制器。调试模式不仅会减慢页面交付速度，还可能泄露应用程序的内部机制。尽管调试工具永远不会泄露数据库连接信息，但异常的堆栈跟踪中包含大量对任何有恶意访问者而言危险的信息。

### Symfony 异常

在调试模式下发生异常时，symfony 会显示一个有用的异常通知，其中包含查找问题原因所需的所有信息。

异常消息编写清晰，并指向问题最可能的原因。它们通常提供修复问题的可能解决方案，对于大多数常见问题，异常页面甚至包含指向 symfony 网站页面的链接，以获取有关异常的更多详细信息。异常页面显示错误发生在 PHP 代码中的位置（带语法高亮显示），并列出完整的方法调用堆栈，如图 16-1 所示。您可以沿着跟踪找到导致问题的第一个调用。传递给方法的参数也会显示。

Symfony 非常依赖 PHP 异常进行错误报告。例如，404 错误可以由 sfError404Exception 触发。

图 16-1 - symfony 应用程序的示例异常消息

![](img/0f886a7f4cbcc3939be96e985ca35ff4_287_0.png)

在开发阶段，symfony 异常在调试应用程序时将非常有用。

### Xdebug 扩展

Xdebug PHP 扩展允许扩展 Web 服务器记录的信息量。Symfony 在其自身的调试反馈中集成了 Xdebug 消息，因此在调试应用程序时激活此扩展是个好主意。扩展安装在很大程度上取决于您的平台；有关详细安装指南，请参阅 Xdebug 网站。

56. http://xdebug.org/

安装 Xdebug 后，需要在 php.ini 文件中手动激活它。对于 *nix 平台，可以通过添加以下行来完成：

```ini
zend_extension="/usr/local/lib/php/extensions/no-debug-non-zts-20041030/xdebug.so"
```

对于 Windows 平台，Xdebug 激活是由以下行触发的：

```ini
extension=php_xdebug.dll
```

清单 16-9 提供了一个 Xdebug 配置示例，也必须添加到 php.ini 文件中。

清单 16-9 - Xdebug 配置示例

```ini
;xdebug.profiler_enable=1
;xdebug.profiler_output_dir="/tmp/xdebug"
xdebug.auto_trace=1          ; enable tracing
xdebug.trace_format=0
;xdebug.show_mem_delta=0     ; memory difference
;xdebug.show_local_vars=1
;xdebug.max_nesting_level=100
```

必须重新启动 Web 服务器才能激活 Xdebug 模式。

> 不要忘记在生产平台上禁用 Xdebug 模式。不这样做会大大减慢每个页面的执行速度。

### Web 调试工具栏

日志文件包含有趣的信息，但不太易读。最基本的任务（即查找针对特定请求记录的行）可能颇为棘手，特别是当多个用户同时使用应用程序且事件历史记录悠久时。这时您就需要一个 Web 调试工具栏了。

该工具栏以半透明盒子的形式叠加在浏览器正常内容上方，位于窗口右上角，如图 16-2 所示。它提供对 symfony 日志事件、当前配置、请求和响应对象的属性、请求发出的数据库查询详细信息以及与请求相关的处理时间图表的访问权限。

图 16-2 - Web 调试工具栏出现在窗口右上角

![](img/0f886a7f4cbcc3939be96e985ca35ff4_288_0.png)

调试工具栏背景的颜色取决于请求期间发出的日志消息的最高级别。如果没有消息超过调试级别，工具栏具有灰色背景。如果单条消息达到 err 级别，工具栏具有红色背景。

不要将调试模式与 Web 调试工具栏混淆。即使调试模式关闭，也可以显示调试工具栏，但在这种情况下，它显示的信息要少得多。

要为应用程序激活 Web 调试工具栏，请打开 settings.yml 文件并查找 web_debug 键。在 prod 和 test 环境中，web_debug 的默认值为 false，因此如果您需要它，必须手动激活。在 dev 环境中，默认配置已将其设置为 true，如清单 16-10 所示。

清单 16-10 - Web 调试工具栏激活，位于 frontend/config/settings.yml

```yaml
dev:
  .settings:
    web_debug: true
```

显示时，Web 调试工具栏提供大量信息/交互：

- 单击 symfony 标志以切换工具栏的可见性。当工具栏缩减时，它不会隐藏页面顶部的元素。
- 单击“config”部分以显示请求、响应、设置、全局变量和 PHP 属性的详细信息，如图 16-3 所示。顶部行总结了重要的配置设置，例如调试模式、缓存以及 PHP 加速器的存在（如果禁用则显示为红色，如果启用则显示为绿色）。

图 16-3 - “config”部分显示请求的所有变量和常量

![](img/0f886a7f4cbcc3939be96e985ca35ff4_289_0.png)

- 启用缓存时，工具栏中会出现一个绿色箭头。单击此箭头可以重新处理页面，无论缓存中存储了什么（但不会清除缓存）。
- 单击“logs”部分以显示当前请求的日志消息，如图 16-4 所示。根据事件的重要性，它们以灰色、黄色或红色行显示。您可以使用列表顶部显示的链接按类别过滤显示的事件。

图 16-4 - “logs”部分显示当前请求的日志消息

