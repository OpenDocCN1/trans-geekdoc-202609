
`composer.json` 文件中的 `require` 键指定了项目依赖哪些包。`require` 接受一个对象，该对象将包名（例如 `monolog/monolog`）映射到版本约束（例如 `1.0.*`）。

![](Image00946.jpg)

要安装已定义的依赖项，你需要运行 `composer install` 命令，它将查找符合所提供版本约束的已定义包，并将其下载到 `vendor` 目录中。将第三方代码放入名为 `vendor` 的目录中是一种惯例。

### `composer.lock`

你会注意到 install 命令还创建了一个 `composer.lock` 文件。

### `composer.lock`

`composer.lock` 文件由 Composer 自动生成。此文件用于跟踪当前安装的依赖项的版本和状态。运行 `composer install` 将把包安装到锁文件中存储的确切状态。

## 第 41.2 节：使用 Composer 进行自动加载

虽然 Composer 为 PHP 项目提供了一个管理依赖的系统（例如来自 [Packagist](https://packagist.org/)），但它也可以充当自动加载器，指定在哪里查找特定的命名空间或包含通用函数文件。

### `composer.json`

从 `composer.json` 文件开始：

![](Image00947.jpg)

### `functions.php`

此配置代码确保命名空间 `MyVendorName\MyProject` 中的所有类都映射到 `src` 目录，而 `MyVendorName\MyProject\Tests` 中的所有类映射到 `tests` 目录（相对于你的根目录）。它还将自动包含 `functions.php` 文件。

### `composer.json`

### `autoload.php`

### `composer install --no-dev`。`autoload.php`

### `composer.json`

将此内容放入 `composer.json` 文件后，在终端运行 `composer update`，让 Composer 更新依赖项、锁文件并生成 `autoload.php` 文件。部署到生产环境时，你应该使用 `composer install --no-dev`。`autoload.php` 文件位于 `vendor` 目录中，该目录应生成在 `composer.json` 所在的目录下。

你应该在应用程序生命周期的早期设置点通过类似下面的代码引入此文件。

![](Image00948.jpg)

### `autoload.php`

一旦包含，`autoload.php` 文件将负责加载你在 `composer.json` 文件中提供的所有依赖项。

类路径到目录映射的一些示例：

### `src/Shapes/Square.php`

### `tests/Shapes/Square.php`

![](Image00949.jpg)
`MyVendorName\MyProject\Shapes\Square` ➔ `src/Shapes/Square.php`。
`MyVendorName\MyProject\Tests\Shapes\Square` ➔ `tests/Shapes/Square.php`。

## 第 41.3 节：'composer install' 和 'composer update' 的区别

### `composer.json`

`composer update` `composer update` 将按照 `composer.json` 中的指定更新我们的依赖项。

例如，如果我们的项目使用此配置：

![](Image00950.jpg)

假设我们实际安装了该包的 `2.0.1` 版本，运行 `composer update` 将导致该包升级（例如升级到 `2.0.2`，如果已发布）。

详细来说 `composer update` 将：

### `composer.json`

### `composer.json`

### `composer.lock`

![](Image00951.jpg)
读取 `composer.json`
移除 `composer.json` 中不再需要的已安装包
检查所需包的最新版本的可用性
安装包的最新版本
更新 `composer.lock` 以存储已安装包的版本

### `composer.lock`

`composer install`

### `composer.lock`

`composer install` 将按照 `composer.lock` 文件中指定的版本（锁定版本）安装所有依赖项，而不更新任何内容。

详细来说：

### `composer.lock`

### `composer.lock`

![](Image00952.jpg)
读取 `composer.lock` 文件
安装 `composer.lock` 文件中指定的包

![](Image00953.jpg)

### 何时安装以及何时更新

`composer update` 主要用于“开发阶段”，以升级项目包。

### `composer.lock`

`composer install` 主要用于“部署阶段”，使用由 `composer update` 创建的 `composer.lock` 文件中存储的相同依赖项，在生产服务器或测试环境上安装应用程序。

## 第 41.4 节：Composer 可用命令

| 命令 | 用法 |
| --- | --- |
| about | Composer 的简短信息 |
| archive | 创建此 Composer 包的归档文件 |
| browse | 在浏览器中打开包的仓库 URL 或主页。 |
| clear-cache | 清除 Composer 的内部包缓存。 |
| clearcache | 清除 Composer 的内部包缓存。 |
| config | 设置配置选项 |
| create-project | 从包在给定目录中创建新项目。 |
| depends | 显示哪些包导致给定包被安装 |
| diagnose | 诊断系统以识别常见错误。 |
| dump-autoload | 转储自动加载器 |
| dumpautoload | 转储自动加载器 |
| exec | 执行供应商提供的二进制文件/脚本 |
| global | 允许在全局 Composer 目录 ($COMPOSER_HOME) 中运行命令。 |
| help | 显示命令的帮助 |
| home | 在浏览器中打开包的仓库 URL 或主页。 |
| info | 显示包的信息 |
| init | 在当前目录创建一个基本的 `composer.json` 文件。 |
| install | 如果存在 `composer.lock` 文件，则从中安装项目依赖项，否则回退到 `composer.json`。 |
| licenses | 显示依赖项的许可证信息 |
| list | 列出命令 |
| outdated | 显示有更新可用的已安装包列表，包括其最新版本。 |
| prohibits | 显示哪些包阻止给定包被安装 |
| remove | 从 require 或 require-dev 中移除包 |
| require | 将所需包添加到 `composer.json` 并安装它们 |
| run-script | 运行 `composer.json` 中定义的脚本。 |
| search | 搜索包 |
| self-update | 将 `composer.phar` 更新到最新版本。 |
| selfupdate | 将 `composer.phar` 更新到最新版本。 |
| show | 显示包的信息 |
| status | 显示本地修改过的包列表 |
| suggests | 显示包建议 |
| update | 根据 `composer.json` 将依赖项更新到最新版本，并更新 `composer.lock` 文件。 |
| validate | 验证 `composer.json` 和 `composer.lock` |
| why | 显示哪些包导致给定包被安装 |
| why-not | 显示哪些包阻止给定包被安装 |

## 第 41.5 节：使用 Composer 的好处

### `composer.lock`

Composer 在一个名为 `composer.lock` 的文件中跟踪你安装的包版本，该文件旨在提交到版本控制系统，以便将来克隆项目时，只需运行 `composer install` 即可下载并安装项目的所有依赖项。

Composer 按项目处理 PHP 依赖项。这使得在一台机器上拥有多个依赖于同一 PHP 包的不同版本的项目变得容易。

Composer 跟踪哪些依赖项仅用于开发环境

![](Image00954.jpg)

Composer 提供了一个自动加载器，使得开始使用任何包变得极其简单。例如，在使用 `composer require` 安装 [Goutte](https://github.com/FriendsOfPHP/Goutte) 后：

`composer require fabpot/goutte`

你可以立即在新项目中开始使用 Goutte：

![](Image00955.jpg)
