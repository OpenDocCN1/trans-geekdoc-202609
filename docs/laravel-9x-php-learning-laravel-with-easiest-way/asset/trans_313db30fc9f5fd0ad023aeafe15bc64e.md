
## 安装

- 认识 Laravel
- 为什么选择 Laravel？
- 你的第一个 Laravel 项目
- 在 macOS 上开始
- 在 Windows 上开始
- 在 Linux 上开始
- 选择你的 Sail 服务
- 通过 Composer 安装
- 初始配置
- 基于环境的配置
- 目录配置
- 下一步
- Laravel 全栈框架
- Laravel 作为 API 后端

## 认识 Laravel

Laravel 是一个拥有富有表现力、简洁优雅语法的 Web 应用程序框架。Web 框架为构建你的应用提供了一个起点，让你专注于创造伟大的东西，而由我们来处理繁琐的任务。Laravel 致力于提供令人惊叹的开发者体验，同时提供诸如优雅的依赖注入、富有表现力的数据库抽象层、队列和定时任务、单元测试和集成测试等强大功能。无论你是 PHP 或 Web 框架的新手，还是拥有多年经验，Laravel 都是一个能与你一同成长的框架。我们将帮助你迈出作为 Web 开发者的第一步，或者在你将技能提升到新水平时提供助力。我们迫不及待想看看你将构建出什么。

## 为什么选择 Laravel？

构建 Web 应用时，你有多种工具和框架可供选择。

然而，我们相信 Laravel 是构建现代全栈 Web 应用的最佳选择。

### 一个渐进式框架

我们喜欢将 Laravel 视为一个“渐进式”框架。意思是 Laravel 会随着你一起成长。如果你刚刚开始 Web 开发，Laravel 丰富的文档、教程和视频录屏库将帮助你快速上手而不至于不知所措。如果你是一位资深开发者，Laravel 为你提供了强大的工具，用于依赖注入、单元测试、队列、实时事件等等。Laravel 旨在构建专业的 Web 应用，并准备好应对企业级任务。

### 可扩展的框架

Laravel 具有令人难以置信的可扩展性。得益于 PHP 对扩展友好的特性，以及 Laravel 内置对 Redis 等快速分布式缓存系统的支持，使用 Laravel 进行水平扩展变得轻而易举。事实上，Laravel 应用已经成功扩展至每月处理数百万次请求。需要极端扩展？像 Laravel Vapor 这样的平台允许你在 AWS 最新的无服务器技术上以几乎无限规模运行你的 Laravel 应用。

### 社区驱动的框架

Laravel 汇集了 PHP 生态中最优秀的软件包，提供最强大且对开发者最友好的框架。此外，来自世界各地的数千名优秀开发者已经为这个框架做出了贡献。谁知道呢，也许你甚至会成为一名 Laravel 贡献者。

## 你的第一个 Laravel 项目

我们相信，开始使用 Laravel 应该尽可能简单。在你自己的计算机上开发和运行 Laravel 项目有多种选择。虽然你可能想在将来探索这些选项，但 Laravel 提供了 Sail，这是一个官方解决方案，用于通过 Docker 运行你的 Laravel 项目。Docker 是一种在小型、轻量级“容器”中运行应用程序和服务的工具，这些容器不会干扰你本地计算机上已安装的软件或配置。这意味着你不必担心在计算机上配置或设置诸如 Web 服务器和数据库之类的复杂开发工具。要开始使用，你只需安装 Docker Desktop。Laravel Sail 是一个轻量级的命令行界面，用于与 Laravel 的默认 Docker 配置进行交互。Sail 为使用 PHP、MySQL 和 Redis 构建 Laravel 应用提供了一个很好的起点，而无需具备 Docker 经验。

{tip} 已经是 Docker 专家了？别担心！Sail 的一切都可以使用 Laravel 附带的 docker-compose.yml 文件进行自定义。

### 在 macOS 上开始

如果你在 Mac 上进行开发，并且已经安装了 Docker Desktop，你可以使用一个简单的终端命令来创建新的 Laravel 项目。例如，要在名为“example-app”的目录中创建一个新的 Laravel 应用，你可以在终端中运行以下命令：

```
curl -s "https://laravel.build/example-app" | bash
```

显然，你可以将 URL 中的“example-app”改为你喜欢的任何名称。Laravel 应用的文件将在你运行命令的目录内创建。项目创建后，你可以导航到应用目录并启动 Laravel Sail。Laravel Sail 提供了一个简单的命令行界面，用于与 Laravel 的默认 Docker 配置进行交互：

```
cd example-app
```

```
./vendor/bin/sail up
```

第一次运行 Sail up 命令时，Sail 的应用容器将在你的机器上构建。

### 在 Windows 上开始

在 Windows 机器上创建新的 Laravel 应用之前，请确保已安装 Docker Desktop。然后，你应该确保已安装并启用适用于 Linux 的 Windows 子系统 2（WSL2）。WSL 允许你在 Windows 10 上原生运行 Linux 二进制可执行文件。有关如何安装和启用 WSL2 的信息，可以在 Microsoft 的开发环境文档中找到。

{tip} 在安装并启用 WSL2 后，你应该确保 Docker Desktop 是

```
cd example-app
```

```
php artisan serve
```

## Laravel 安装器

或者，你也可以将 Laravel 安装器作为一个全局的 Composer 依赖来安装：

```
composer global require laravel/installer
laravel new example-app
cd example-app
php artisan serve
```

确保将 Composer 的系统级 vendor bin 目录放入你的 $PATH 中，以便系统能够找到 Laravel 可执行文件。该目录根据操作系统的不同而位于不同的位置；不过，一些常见的位置包括：

- macOS: $HOME/.composer/vendor/bin
- Windows:
  %USERPROFILE%\AppData\Roaming\Composer\vendor\bin
- GNU / Linux 发行版：$HOME/.config/composer/vendor/bin
  或
  $HOME/.composer/vendor/bin

为方便起见，Laravel 安装器还可以为你的新项目创建一个 Git 仓库。要指示你想要创建 Git 仓库，

## 目录配置

Laravel 应始终从为你的 Web 服务器配置的“Web 目录”的根目录提供服务。你不应尝试从“Web 目录”的子目录提供 Laravel 应用服务。尝试这样做可能会暴露应用中存在的敏感文件。

## 下一步

既然你已经创建了 Laravel 项目，你可能会想知道接下来该学什么。首先，我们强烈建议你通过阅读以下文档来熟悉 Laravel 的工作原理：

- **请求生命周期**
- **配置**
- **目录结构**
- **服务容器**
- **门面**

你想如何使用 Laravel 也将引导你旅程的下一步。Laravel 有多种使用方式，下面我们将探讨框架的两种基本用例。

## Laravel 全栈框架

Laravel 可以作为一个全栈框架。所谓的“全栈”，指的是你将使用 Laravel 将请求路由到你的应用，并通过 Blade 模板或使用类似 Inertia.js 的单页应用混合技术来渲染前端。这是使用 Laravel 框架最常见的方式。如果你打算这样使用 Laravel，你可能想查看我们关于路由、视图或 Eloquent ORM 的文档。此外，你可能还会有兴趣了解社区包，如 Livewire 和 Inertia.js。这些包允许你将 Laravel 用作全栈框架，同时享受单页 JavaScript 应用提供的许多 UI 优势。如果你将 Laravel 作为全栈框架使用，我们还强烈建议你学习如何使用 Laravel Mix 配置应用的 CSS 和 JavaScript。

{tip} 如果你想抢先一步构建应用，可以查看我们的官方应用启动套件之一。

## Laravel 作为 API 后端

Laravel 也可以作为 JavaScript 单页应用或移动应用的 API 后端。例如，你可以将 Laravel 作为 Next.js 应用的 API 后端。在这种情况下，你可以使用 Laravel 来提供身份验证和数据

