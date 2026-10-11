

| @ inheritDoc |
| --- |

如果一个类继承自另一个类并将使用相同的元数据，提供它是使用相同文档的一种简单方法。如果多个类继承自一个基类，则只需更改基类即可影响子类。

![](Image01587.jpg)

![](Image01588.jpg)

# 第 90 章：设计模式

本主题提供了在 PHP 中实现的知名设计模式示例。

## 第 90.1 节：PHP 中的方法链

方法链是 [Martin Fowler 的书](http://rads.stackoverflow.com/amzn/click/0321712943) [Domain Specific Languages](http://rads.stackoverflow.com/amzn/click/0321712943) 中解释的一种技术。方法链总结如下：

![](Image01589.jpg) [让修饰方法返回宿主对象，以便可以在单个表达式中调用多个修饰符](http://martinfowler.com/dslCatalog/methodChaining.html)。

请看这段非链式/常规代码（从上述书籍移植到 PHP）：

![](Image01590.jpg)

方法链将允许您以更紧凑的方式编写上述语句：

![](Image01591.jpg)

| return $this |
| --- |

要使其工作，您只需在想要链式调用的方法中 `return $this`：

![](Image01592.jpg)

### 何时使用

利用方法链的主要用例是在构建内部领域特定语言时。方法链是 [Expression Builders](http://martinfowler.com/bliki/ExpressionBuilder.html)（表达式构建器）和 [Fluent Interfaces](http://martinfowler.com/bliki/FluentInterface.html)（流式接口）的基础构建块。[但它并不等同于它们](http://stackoverflow.com/a/17940086/208809)。方法链仅仅是启用了它们。引用 Fowler 的话：

![](Image01593.jpg)

![](Image01594.jpg) 我还注意到一个常见的误解——许多人似乎将流式接口等同于方法链。当然，链式调用是流式接口常用的技术，但真正的流畅性远不止于此。

话虽如此，仅为了避免书写宿主对象而使用方法链，被许多人视为一种 [code](http://martinfowler.com/bliki/CodeSmell.html) [smell](http://martinfowler.com/bliki/CodeSmell.html)（代码异味）。它会导致不明显的 API，特别是在与非链式 API 混合使用时。

### 附加说明

#### 命令查询分离

[命令查询分离是由 Bertrand Meyer 提出的设计原则](http://martinfowler.com/bliki/CommandQuerySeparation.html)。它规定：改变状态的方法（命令）不应返回任何内容，而返回内容的方法（查询）不应改变状态。这使得系统更易于推理。方法链违反了这一原则，因为我们在改变状态的同时返回了值。

#### Getter 方法

当使用实现了方法链的类时，调用 getter 方法（即返回 `$this` 以外内容的方法）时要特别注意。由于 getter 必须返回除 `$this` 以外的值，因此在 getter 后链式调用额外的方法会使该调用作用于获取到的值，而不是原始对象。虽然链式 getter 有一些用例，但它们可能会降低代码的可读性。

#### 迪米特法则及对测试的影响

如上所述的方法链不违反 [迪米特法则](https://en.wikipedia.org/wiki/Law_of_Demeter)。也不影响测试。这是因为我们返回的是宿主实例，而不是某个协作者。这是一个常见的误解，源于人们将单纯的方法链与流式接口和表达式构建器混淆。只有当方法链返回除宿主对象以外的其他对象时，才会违反迪米特法则，并导致测试中出现大量 Mock 对象。

# 第 91 章：编译 PHP 扩展

## 第 91.1 节：在 Linux 上编译

要在典型的 Linux 环境中编译 PHP 扩展，需要满足一些先决条件：

*   基本的 Unix 技能（能够操作 `make` 和 C 编译器）
*   ANSI C 编译器
*   您想要编译的 PHP 扩展的源代码

通常有两种编译 PHP 扩展的方法。您可以将扩展静态编译到 PHP 二进制文件中，或者将其编译为由 PHP 二进制文件在启动时加载的共享模块。共享模块更常见，因为它们允许您在不重新构建整个 PHP 二进制文件的情况下添加或删除扩展。本示例侧重于共享模块选项。

```
apt-get install php5-dev or php7-dev
```

如果您通过包管理器安装了 PHP（apt, yum install 等），您将需要安装 PHP 的开发包，其中将包含构建环境所需的 PHP 头文件和 `phpize` 脚本。该包可能命名为 `php5-dev` 之类，但请务必使用您的包管理器搜索您发行版仓库中合适的名称。它们可能有所不同。

```
/usr/include
```

如果您从源代码构建了 PHP，则头文件很可能已经存在于您的系统上（通常在 `/usr/include` 或 `/usr/local/include`）。

### 编译步骤

在检查确认您具备编译所需的所有先决条件后，您可以前往 [pecl.php.net](http://pecl.php.net/)，选择您想要编译的扩展，并下载压缩包。

```
tar xfvz yaml-2.0.0RC8.tgz
```

1.  解压压缩包（例如 `tar xfvz yaml-2.0.0RC8.tgz`）
2.  进入解压后的目录并运行 `phpize`
3.  如果一切顺利，您现在应该会看到一个新创建的 `configure` 脚本，运行它 `./configure`
4.  现在您需要运行 `make`，这将编译扩展
5.  最后，`make install` 会将编译好的扩展二进制文件复制到您的扩展目录中

```
/usr/lib/, 例如它可能类似于 /usr/lib/php5/20131226/yaml.so
```

```
--with-prefix
```

`make install` 步骤通常会为您提供扩展被复制到的安装路径。这通常在 `/usr/lib/` 中。但这取决于您的 PHP 配置（即 `--with-prefix`）和特定的 API 版本。API 编号包含在路径中，以将为不同 API 版本构建的扩展保存在单独的位置。

### 在 PHP 中加载扩展

```
extension=yaml.so
```

要在 PHP 中加载扩展，请找到适用于相应 SAPI 的已加载 `php.ini` 文件，并添加行 `extension=yaml.so`（当然，请将 `yaml.so` 更改为您实际安装的扩展名称）。

对于 Zend 扩展，您确实需要提供共享对象文件的完整路径。但是，对于普通的 PHP 扩展，此路径源自您加载的配置中的 `extension_dir` 指令，或初始设置期间的 `$PATH` 环境变量。

# 第 92 章：常见错误

## 第 92.1 节：在布尔值上调用 fetch_assoc

如果您遇到如下错误：

![](Image01596.jpg) Fatal error: Call to a member function `fetch_assoc()` on boolean in `C:\xampp\htdocs\stack\index.php` on line 7

![](Image01597.jpg) 其他变体包括类似：`mysql_fetch_assoc()` expects parameter 1 to be resource, boolean given ...

这些错误意味着您的查询（这是一个 PHP/MySQL 错误）或您的引用出了问题。上述错误由以下代码产生：

![](Image01598.jpg)

为了“修复”此错误，建议让 mysql 抛出异常：

![](Image01599.jpg)

这将抛出一个异常，并显示更有帮助的消息：

