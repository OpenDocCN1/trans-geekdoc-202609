

使用自定义 phar 格式，你可以指定 PHP “stub” 代码。这段 stub 代码允许你直接执行 phar 文件，就像它只是一个标准的 PHP 文件一样。这意味着在命令行中，你可以执行类似 `php mybundle.phar -x something -l something-else` 的操作来运行你的应用程序。它还允许 PHP 将该文件识别为标准 PHP 文件，从而无需 phar 扩展可用。只要设置好文件关联，你甚至可以将 phar 文件设置为自执行（参见第 2 章），方式与标准 PHP 脚本相同。Stub 代码仅作为 PHP 的入口点，告诉它从哪里开始，通常只是针对捆绑包中主 PHP 脚本的 `require()` 语句。即使有 stub 代码，phar 文件仍可通过外部脚本中的 `phar://` 流包装器访问，因此它既可以作为可执行捆绑包，也可以作为简单的文件集合。自定义 phar 格式唯一的真正缺点是，它只能使用 PHP 本身（具体来说是使用 phar 扩展）来创建。zip 和 tar 格式可以使用大多数第三方归档工具创建。

| ![information](Images/image00248.jpeg) || **Further Reading**“Phar: PHP libraries included with a single file” tutorial by Giorgio Sironi  

[http://css.dzone.com/articles/phar-php-libraries-single-file](http://css.dzone.com/articles/phar-php-libraries-single-file)Phar documentation in the PHP Manual  

[http://www.php.net/manual/en/intro.phar.php](http://www.php.net/manual/en/intro.phar.php) |

| --- | --- |

### 10.5 Generic installers

以下是几个值得注意的开源通用安装程序。它们可用于安装 PHP 本身以及与你的 PHP 应用程序一起的其他软件，当然也可以用于部署和运行 phar 捆绑包（参见上一节）。

| ![](Images/image00249.gif) || `WiX Toolset` |

| --- | --- |

|   ||   |

|   || 用于为 Windows 创建 .msi 和 .exe 安装程序的全面工具集 |

|   ||   |

|   || `Main website` : [http://wixtoolset.org/](http://wixtoolset.org/) |

|   ||   |

|   || `Main documentation & Installation info` : [http://wixtoolset.org/documentation/manual/](http://wixtoolset.org/documentation/manual/) |

| ![](Images/image00249.gif) || `fpm` |

| --- | --- |

|   ||   |

|   || 易于使用的工具，用于创建 .deb、.rpm、solaris 和 puppet 包/模块。 |

|   ||   |

|   || `Main website` : [https://github.com/jordansissel/fpm](https://github.com/jordansissel/fpm) |

|   ||   |

|   || `Installation info` : [https://github.com/jordansissel/fpm#get-with-the-download](https://github.com/jordansissel/fpm#get-with-the-download) |

|   ||   |

|   || `Main documentation` : [https://github.com/jordansissel/fpm/wiki](https://github.com/jordansissel/fpm/wiki) |

### 10.6 Controlling the (PHP) environment

当你在自己的服务器或 PC 上部署脚本时，可以控制其部署环境。但是，如果你更广泛地分发软件，你会突然发现外部机器上的环境因素可能导致你的 PHP 脚本表现异常，甚至完全停止工作。你需要考虑的一些 PHP 特定环境因素包括：

*   Installed PHP version : 检查当前版本（在脚本中使用 `phpversion()`）以确保你的脚本兼容。考虑随安装程序一起部署 PHP 本身，如果这样做，可能值得将其安装在非标准位置，使用非标准名称，且不设置 `php` 环境变量，以避免与任何现有版本混淆。

*   Installed Extension version : 与上述主 PHP 安装一样，你可以使用 `phpversion('extension_name')` 检查关键扩展的版本，并相应地采取行动。

*   `php.ini` settings : 这些设置可能与你机器上的不同。理想情况下，你会提供自己的自定义 `php.ini` 文件并使用它（例如，调用 `php --php-ini my-php.ini myfile.php`，参见第 2 章）以确保一切设置符合你的要求。你也可以在脚本中使用 `ini_set()` 设置重要设置，但请注意，这可能会在现有的 `php.ini` 文件中被禁用。

*   Location of common paths : Linux 上的系统临时目录通常是 `/tmp`。但并非总是如此。尽可能使用 `sys_get_temp_dir()` 和 `get_env('PATH')` 等函数来查找系统上的相关文件夹，或者至少允许用户在配置文件中指定它们。

你还需要检查可能存在的任何其他非 PHP 依赖项，评估是否有适当级别的硬件资源（内存、磁盘空间）可用，并检查是否需要任何网络/互联网连接。

| ![](Images/image00249.gif) || `3v4l.org` |

| --- | --- |

|   ||   |

|   || Web 服务，允许你单击 1 次即可在 100 多个 PHP 版本（包括 HHVM）中测试代码片段。有助于确定你的代码可以支持哪些 PHP 版本。 |

|   ||   |

|   || `Main website` : [http://3v4l.org/](http://3v4l.org/) |

### 10.7 Extending your application with plug-ins

在开发自己的网站或软件时，如果需要额外功能，通常会直接将其添加到软件中。分发软件时，允许用户提供他们自己的额外功能通常很有用，特别是那些仅与其特定需求相关的功能。通常的做法是通过插件/扩展/附加组件类型系统来实现。实现插件的方法有千百种，下面由 Anthony Ferrara 撰写的文章概述了一些常见的插件设计模式以及如何在 PHP 中实现它们的示例。你也可以实现一个 API（应用程序编程接口），就像你对网站所做的那样，使用书中前面概述的方法之一（网络守护进程、共享内存、消息队列等）与“插件”进程进行通信。

| ![information](Images/image00248.jpeg) || **Further Reading**“Handling Plugins In PHP” by Anthony Ferrara  

[http://blog.ircmaxell.com/2012/03/handling-plugins-in-php.html](http://blog.ircmaxell.com/2012/03/handling-plugins-in-php.html)“Build APIs You Won’t Hate” by Phil Sturgeon  

[https://leanpub.com/build-apis-you-wont-hate](https://leanpub.com/build-apis-you-wont-hate?a=0_YKAEBrn4BvyagDZlmBZy&subID=b) |

| --- | --- |

### 10.8 Documentation

理想情况下，你的应用程序会非常易于使用，以至于用户不需要任何文档，对吧？笑完之后，我们继续。你可能熟悉在 Web 项目中提供最终用户文档和支持信息，但典型的软件项目需要更多。你还需要安装和升级文档、系统管理员信息、许可证文档等等。如果你允许/鼓励用户修改代码，你甚至可能需要包含代码文档和架构/设计文档。

你应该努力在两个位置提供所有文档：在线和随软件包含。随软件包含的副本允许用户在没有互联网连接时访问，或者在你的网站宕机（或你的公司破产……）时访问。在线文档提供了一个易于更新的来源，用于更正或补充信息，它还允许潜在用户/客户在不下载/购买软件的情况下评估软件。

最后，在广泛分发软件时，全面且高质量的文档可以减少你收到的技术/用户支持请求数量。这通常会比编写文档所花费的时间节省更多时间。

| ![information](Images/image00248.jpeg) || **Further Reading**Software Documentation on Wikipedia  

[http://en.wikipedia.org/wiki/Software\_documentation](http://en.wikipedia.org/wiki/Software_documentation) |

| --- | --- |

