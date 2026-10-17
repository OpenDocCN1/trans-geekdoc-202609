

运行上述命令后，你应该会发现一个 `.so` 文件（在我们的示例中为 `pcntl.so`）已被编译并放置在 PHP 的扩展目录中。最后一步是通过在 `php.ini` 文件的某处添加以下行来告诉 PHP 它：

```
extension=pcntl.so
```

如果你不确定 `php.ini` 文件的位置，可以在命令行运行 `php -i | grep "Loaded Configuration File"` 来查找。你也可以使用 `php -i` 检查你的扩展是否已正确安装并可供使用。

### 安装多个版本的 PHP

有时（特别是在开发机器上）你可能希望同时安装多个版本的 PHP，例如，如果你要部署给已经安装了 PHP 但可能使用不同版本的最终用户。实现这一点的一种简单方法是创建一组虚拟机（我使用 VirtualBox），每个虚拟机中安装不同版本的 PHP。在这种情况下，你始终可以确定正在运行哪个版本，并且一个版本的安装和配置不会干扰另一个版本。缺点是启动和关闭不同的虚拟机可能很慢（或者同时运行它们会占用资源），如果你使用 Windows 等专有操作系统，可能会产生额外的许可费用。正如我在前一节中提到的，可以在同一台机器上直接安装和运行多个版本。但是，如果不小心，要保持版本及其依赖项分离，并始终确定自己正在使用哪个版本，可能会成为一场噩梦。因此，我不会在本书中深入探讨这一点。但是，下面是两篇由受人尊敬的 PHP 社区成员撰写的文章，他们已经做到了这一点，可能会给你一些关于该做什么以及涉及哪些陷阱的指导。我建议在尝试之前，你要熟悉编译和安装 PHP、PHP 使用的文件和目录结构及位置，以及如何检查正在运行的 PHP 和扩展的版本。

下面还列出了几个相关工具。第一个是 `php-build`，它可以自动从源代码构建多个版本的 PHP，尽管你仍然需要小心地同时安装和使用它们。第二个是 `3v4l.org`，一个 Web 服务，允许你同时在 90 多个版本的 PHP 中测试代码片段。这可能完全避免安装多个版本的需要。最后一个工具是一个库，它模拟了较新版本的许多函数，以便与较旧版本一起使用。

| ![information](Images/image00248.jpeg) || 进一步阅读 |
| --- | --- |
| | 使用 SVN 安装多个版本 |
| | [http://derickrethans.nl/multiple-php-version-setup.html](http://derickrethans.nl/multiple-php-version-setup.html) |
| | 使用 GIT 安装多个版本 |
| | [http://mark-story.com/posts/view/installing-multiple-versions-of-php-from-source](http://mark-story.com/posts/view/installing-multiple-versions-of-php-from-source) |

| ![](Images/image00249.gif) || `php-build` |
| --- | --- |
| | |
| | `php-build` 自动从源代码构建多个 PHP 版本 |
| | |
| | 主网站及文档：[http://www.christophh.net/php-build/](http://www.christophh.net/php-build/) |

| ![](Images/image00249.gif) || `3v4l.org` |
| --- | --- |
| | |
| | Web 服务，允许你点击 1 次按钮即可在 90 多个版本的 PHP 中测试代码片段。 |
| | |
| | 主网站：[http://3v4l.org/](http://3v4l.org/) |

| ![](Images/image00249.gif) || `upgrade.php` |
| --- | --- |
| | |
| | 用于为旧版本的 PHP 模拟较新函数的库。 |
| | |
| | 主网站：[http://include-once.org/p/upgradephp/](http://include-once.org/p/upgradephp/) |

### PEAR 和 PECL

PEAR（PHP 扩展和应用程序仓库）是一个用 PHP 编写的代码和扩展库，带有易于使用的打包和分发系统。PECL（PHP 扩展社区库）本质上是相同的，但用于用 C 编写的扩展。

PECL 和 PEAR 的工作方式与 Debian 的 `apt-get` 等包管理器类似。例如，要从 PECL 安装 Cairo 图形扩展，只需在命令行执行 `sudo pecl install cairo`。这将为你下载、编译并安装 Cairo，然后你可以在 PHP 脚本中开始使用它。同样，要从 PEAR 安装 RDF 扩展，请使用 `pear install rdf`。

`pear` 和 `pecl` 命令随 PHP 标准包含，但某些包管理器将它们放在可选的 `php-dev` 或 `php-pear` 包中。例如，在 Ubuntu 上，使用 `sudo apt-get install php-pear` 进行安装。

有关两者以及数百个可用扩展和库的更多信息，可以分别在 [http://pear.php.net](http://pear.php.net) 和 [http://pecl.php.net](http://pecl.php.net) 上找到。

### Composer

Composer 是一个依赖管理器。虽然它处理包，但它不像 PEAR 那样是包管理器。它不是集中安装包，而是按项目处理它们，确保为该项目自动安装相关包及其依赖项的适当版本。

基本的 Composer 工作流程如下：

*   你安装 Composer。
*   在项目的基目录中，你创建一个名为 `composer.json` 的 JSON 格式文件，指定你的项目需要哪些包（和版本）
*   在该目录中，你运行 Composer。它将获取并安装指定的包，并自动安装你指定的包所依赖的任何其他包（以此类推，直到所有依赖项都满足）
*   在你的 PHP 代码中，只需添加函数 `require 'vendor/autoload.php';`，当你使用库时，它们将自动可用。

面向初学者和高级用户的全面文档可在 Composer 网站上找到。Composer 本身不托管任何包，这是包仓库的工作。Packagist 是主要的，也是目前唯一的全面公共仓库，并且是 Composer 默认使用的仓库。你可以在 Packagist 网站上浏览数千个可用的包。如果你需要，当然可以指定不同的仓库，甚至创建和使用你自己的私有包。

| ![](Images/image00249.gif) || Composer 依赖管理器 |
| --- | --- |
| | |
| | 按项目保持库一致且最新的简便方法。 |
| | |
| | 主网站：[http://getcomposer.org/](http://getcomposer.org/) |
| | |
| | 包仓库：[https://packagist.org/](https://packagist.org/) |
| | |
| | 安装信息：[http://getcomposer.org/doc/00-intro.md#installation-nix](http://getcomposer.org/doc/00-intro.md#installation-nix) |
| | |
| | 主要文档：[http://getcomposer.org/doc/](http://getcomposer.org/doc/) |
| | |
| | 教程：[http://code.tutsplus.com/tutorials/easy-package-management-with-composer--net-25530](http://code.tutsplus.com/tutorials/easy-package-management-with-composer--net-25530) |

### Symfony2 bundles

如果你使用 Symfony2 框架，可以从 knpbundles 下载超过一千个有用的代码包。这些包可以手动安装，或通常使用 Composer 依赖系统（见上一节）。访问 [http://knpbundles.com/](http://knpbundles.com/) 以获取更多信息并浏览可用代码。

## 附录 B：PHP 的文件和数据格式库

