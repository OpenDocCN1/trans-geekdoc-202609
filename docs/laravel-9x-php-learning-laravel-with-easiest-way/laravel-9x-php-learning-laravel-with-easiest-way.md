# Laravel 9.x ｜ PHP 最简单的方式学习 Laravel
















破坏性变更。在从你的应用或扩展包引用 Laravel 系统或其任何部分时，你应该始终使用版本约束，例如 `^9.0`，因为 Laravel 的主要版本确实会引入破坏性变更。无论如何，我们努力始终确保你可以在一天或更短的时间内升级到新的主要版本。

# 命名参数

命名参数不受 Laravel 向后兼容规则的保护。为了进一步开发 Laravel 代码库，我们可能决定在必要时重命名方法参数。因此，在调用 Laravel 方法时使用命名参数应谨慎，并理解参数名称今后可能会改变。

# 支持策略

对于 LTS 版本，例如 Laravel 9，提供 2 年的错误修复和 3 年的安全修复。这些版本提供最长的帮助和支持窗口。对于一般版本，错误修复提供一年半，安全修复提供 2 年。对于所有其他库，包括 Lumen，最新的版本无疑会获得错误修复。此外，请查看 Laravel 支持的数据库版本。

Laravel 社区向我们的开发团队提出挑战，要求在不引入破坏性变更的情况下交付出色、健壮的新功能。因此，我们为 Laravel 8 提供了一系列健壮的功能，而没有破坏向后兼容性，例如并行测试支持、改进的 Breeze 入门套件、HTTP 客户端增强，以及令人惊讶的新 Eloquent 关系类型，例如 "has one of many"。因此，这种在当前版本中交付出色新功能的承诺，可能会导致未来的 "主要" 版本主要用于 "维护" 任务，例如升级上游依赖，这在版本说明中可以看到。Laravel 9 延续了 Laravel 8.x 的改进，引入了对 Symfony 6.0 组件、Symfony Mailer、Flysystem 3.0、改进的 route:list 输出、Laravel Scout 数据库驱动、新的 Eloquent 访问器/修改器语法、通过枚举的隐式路由绑定，以及其他各种错误修复和便利性增强的支持。

# 贡献指南

- 错误报告
- 支持问题
- 核心开发讨论
- 选择哪个分支？
- 编译后的资源
- 安全漏洞
- 编码风格
- PHPDoc
- StyleCI
- 行为准则

源代码托管在 GitHub 上，每个 Laravel 项目都有对应的仓库。

如果你在 Laravel 中发现安全漏洞，请发送电子邮件至 Taylor Otwell：taylor@laravel.com。所有安全漏洞都将得到及时处理。

# 编码风格

Laravel 遵循 PSR-2 编码标准和 PSR-4 自动加载标准。

# PHPDoc

下面是一个有效的 Laravel 文档块的示例。请注意，@param 属性后跟两个空格、参数类型、再两个空格，最后是变量名：

# StyleCI

如果你的代码风格有问题，你完全可以放心！StyleCI 会在拉取请求合并后自动将任何风格修复合并到 Laravel 仓库中。这使我们能够专注于贡献的内容，而不是代码风格。

# 行为准则

Laravel 的行为准则源自 Ruby 的行为准则。任何违反行为准则的行为都可以向 Taylor Otwell 举报。

- 参与者应容忍对立的观点。
- 参与者必须确保其言语和行为不包含人身攻击和贬低性言论。
- 在解读他人的言行时，参与者应始终假定其出于善意。
- 任何可合理视为骚扰的行为都不会被容忍。




# 安装

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

# 认识 Laravel

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


# Configuration
- 简介
- 环境配置
  - 环境变量类型
  - 获取环境配置
  - 确定当前环境
- 访问配置值
- 配置缓存
- 调试模式
- 维护模式

## 简介
所有 Laravel 应用的配置文件都存储在 config 目录中。每个选项都有文档说明，因此请随意浏览文件并熟悉可用的选项。这些配置文件允许你配置诸如数据库连接信息、邮件服务器设置以及各种其他核心配置值，例如应用程序时区和加密密钥。

## 环境配置
根据应用程序运行的环境拥有不同的配置值通常很有用。例如，你可能希望在本地使用与生产服务器不同的缓存驱动。为了方便这一点，Laravel 使用 DotEnv PHP 库。在新的 Laravel 安装中，应用程序的根目录将包含一个 .env.example 文件，其中定义了许多常见的环境变量。在 Laravel 安装过程中，此文件将自动复制为 .env。Laravel 默认的 .env 文件包含一些常见的配置值，这些值可能因应用程序是在本地运行还是在生产 Web 服务器上运行而异。然后，这些值会使用 Laravel 的 env 函数从 config 目录内的各种 Laravel 配置文件中检索。如果你与团队一起开发，你可能希望继续
包含 .env.example 文件与你的应用程序一起。通过在示例文件中放置占位符值，你团队中的不同开发人员可以清楚地看到运行应用程序所需的环境变量。

> {tip} .env 文件中的任何变量都可以通过外部环境变量（如服务器级或系统级环境变量）覆盖。

## 环境文件安全
你的 .env 文件不应提交到应用程序的源代码控制中，因为使用你的应用程序的每个开发人员/服务器可能需要不同的环境配置。此外，如果入侵者访问你的源代码控制仓库，这将是一个安全风险，因为任何敏感凭据都将被暴露。

## 附加环境文件
在加载应用程序的环境变量之前，Laravel 会确定 APP_ENV 环境变量是否已外部提供或是否指定了 --env CLI 参数。如果是这种情况，Laravel 将尝试加载一个 .env.[APP_ENV] 文件（如果存在）。如果不存在，则将加载默认的 .env 文件。

## 环境变量类型
事实上，你会看到许多选项已经在使用此助手：
```
'debug' => env('APP_DEBUG', false),
```
传递给 env 函数的第二个值是“默认值”。如果不存在给定键的环境变量，将返回此值。

## 确定当前环境
当前应用程序环境是通过 .env 文件中的 APP_ENV 变量确定的。

你可以通过 App 门面上的 environment 方法访问此值：
```
use Illuminate\Support\Facades\App;

$environment = App::environment();
```
你也可以向 environment 方法传递参数，以确定环境是否与给定值匹配。如果环境匹配任何给定值，该方法将返回 true：
```
if (App::environment('local')) {
    // The environment is local
}

if (App::environment(['local', 'staging'])) {
    // The environment is either local OR staging...
}
```
{tip} 当前应用程序环境检测可以通过定义服务器级的 APP_ENV 环境变量来覆盖。

## 访问配置值
你可以使用全局 config 辅助函数从应用程序的任何位置轻松访问配置值。配置值可以使用“点”符号访问，其中包括你想要访问的文件名和选项。也可以指定默认值，如果配置选项不存在，将返回该值：
```
$value = config('app.timezone');

// Retrieve a default value if the configuration value does not exist...
$value = config('app.timezone', 'Asia/Seoul');
```
要在运行时设置配置值，请向 config 辅助函数传递一个数组：
```
config(['app.timezone' => 'America/Chicago']);
```

## 配置缓存
为了给你的应用程序提速，你应该使用 config:cache Artisan 命令将所有配置文件缓存到单个文件中。这将把应用程序的所有配置选项合并到一个文件中，框架可以快速加载。你通常应该在生产部署流程中运行 php artisan config:cache 命令。在本地开发期间不应运行此命令，因为在应用程序开发过程中配置选项通常需要修改。

> {note} 如果你在部署过程中执行 config:cache 命令，你应确保仅在配置文件中调用 env 函数。一旦配置被缓存，.env 文件将不会被加载；因此，env 函数将仅返回外部、系统级环境变量。

## 调试模式
config/app.php 配置文件中的 debug 选项决定了向用户实际显示的错误信息的数量。默认情况下，此选项设置为尊重 APP_DEBUG 的值
```
php artisan down --refresh=15
```
你也可以为 down 命令提供 retry 选项，它将被设置为 Retry After HTTP 头的值，尽管浏览器通常会忽略此头：
```
php artisan down --retry=60
```

## 绕过维护模式
即使在维护模式下，你也可以使用 secret 选项指定维护模式绕过令牌：
```
php artisan down --secret="1630542a-246b-4b66-afa1-dd72a4c43515"
```
将应用程序置于维护模式后，你可以导航到与此令牌匹配的应用程序 URL，Laravel 将向你的浏览器发放维护模式绕过 cookie：
```
https://example.com/1630542a-246b-4b66-afa1-dd72a4c43515
```
访问此隐藏路由时，你将被重定向到应用程序的 / 路由。一旦 cookie 已发放给你的浏览器，你将能够像未处于维护模式一样正常浏览应用程序。

{tip} 你的维护模式 secret 通常应由字母数字字符组成

# 目录结构
## 简介
## 根目录
- app 目录
- bootstrap 目录
- config 目录
- database 目录
- public 目录
- resources 目录
- routes 目录
- storage 目录
- tests 目录
- vendor 目录

## App 目录
- 广播目录
- 控制台目录
- 事件目录
- 异常目录
- Http 目录
- 任务目录
- 监听器目录
- 邮件目录
- 模型目录
- 通知目录
- 策略目录

config 目录，如其名称所示，包含应用程序的所有配置文件。阅读这些文件并熟悉所有可用的选项是个好主意。

## 数据库目录
resources 目录包含你的视图以及原始的未编译资源，如 CSS 和 JavaScript。该目录还存放所有语言文件。

## 公共目录
public 目录包含 index.php 文件，它是进入应用程序的所有请求入口点并配置自动加载。该目录还存放你的资源，如图像、JavaScript 和 CSS。

## 资源目录
resources 目录包含你的视图以及原始的未编译资源，如 CSS 和 JavaScript。该目录同样存放所有语言文件。

## 路由目录
route 目录包含应用程序的所有路由定义。自然地，几个

Laravel 包含以下路由文件：web.php、api.php、console.php 和 channels.php。web.php 文件包含 RouteServiceProvider 放置在 web 中间件组中的路由，该组提供会话状态、CSRF 保护和 Cookie 加密。如果你的应用程序不提供无状态的 RESTful API，那么几乎可以肯定你的所有路由都将在 web.php 文件中定义。api.php 文件包含 RouteServiceProvider 放置在 API 中间件组中的路由。这些路由旨在无状态，因此通过这些路由进入应用程序的请求旨在通过令牌进行身份验证，并且不会访问会话状态。console.php 文件是你定义所有基于闭包的控制台命令的地方。每个闭包都绑定到一个命令实例，提供了一种简单的方式与每个命令的 IO 方法交互。尽管该文件不定义 HTTP 路由，但它确实在你的应用程序中定义了基于控制台的入口点（命令）。channels.php 文件是你注册应用程序支持的所有事件广播频道的地方。

## 存储目录
storage 目录包含你的日志、编译后的 Blade 视图、基于文件的会话以及框架生成的文件。该目录分为 app、framework 和 logs 三个目录。

app 目录可用于存储应用程序创建的任何文件。framework 目录用于存储框架生成的文件和缓存。最后，logs 目录包含应用程序的日志文件。

storage/app/public 目录可用于存储应公开访问的用户生成文件，例如个人资料头像。你应该在 public/storage 创建一个指向此目录的符号链接。你可以使用 php artisan storage:link Artisan 命令创建链接。

## 测试目录
tests 目录包含你的自动化测试。开箱即用提供了示例 PHPUnit 单元测试和功能测试。每个测试类应以单词 "Test" 作为后缀。你可以使用 phpunit 或 php vendor/bin/phpunit 命令运行测试。或者，如果你想要更精确、更美观的测试结果展示，可以使用 php artisan test Artisan 命令运行测试。

## 供应商目录
vendor 目录包含你的 Composer 依赖项。

### 应用目录

### 广播目录
Broadcasting 目录包含应用程序的所有广播频道类。这些类使用 make:channel 命令创建。该目录默认不存在。但是，在你创建第一个频道时它会被为你创建。要了解有关频道的信息，请查阅事件广播文档。

### 控制台目录
Console 目录包含应用程序的所有自定义 Artisan 命令。这些命令可以使用 make:command 命令创建。该目录还包含你的控制台内核，在此注册自定义 Artisan 命令并定义计划任务。

### 事件目录
该目录默认不存在，但会被 event:generate 和 make:event Artisan 命令为你创建。Events 目录存放事件类。Events can be used

你可以使用它来提醒应用程序的不同部分某个操作已发生，提供很大的灵活性和解耦。

### 异常目录
Exceptions 目录包含应用程序的异常处理器，也是放置应用程序抛出的任何异常的好地方。如果你想更改异常的记录或渲染方式，应修改此目录中的 Handler 类。

### Http 目录
Http 目录包含你的控制器、中间件和表单请求。处理进入应用程序的请求的大部分逻辑都将放在此目录中。

### 任务目录
该目录默认不存在，但如果执行 make:job Artisan 命令，它会被为你创建。Jobs 目录存放应用程序的可队列任务。任务可以由应用程序排队，也可以同步在当前请求生命周期内运行。在当前请求期间同步运行的任务有时被称为 "commands"，因为它们是命令模式的实现。

### 监听器目录
该目录默认不存在，但如果执行 event:generate 或 make:listener Artisan 命令，它会被为你创建。Listeners 目录包含处理事件的类。事件监听器接收事件实例并在事件触发时执行逻辑。例如，UserRegistered 事件可能由 SendWelcomeEmail 监听器处理。

### 邮件目录
该目录默认不存在，但如果执行 make:mail Artisan 命令，它会被为你创建。Mail 目录包含所有

### 策略目录
该目录默认不存在，但如果执行 make:policy Artisan 命令，它会被为你创建。Policies 目录包含应用程序的授权策略类。策略用于确定用户是否可以对资源执行给定操作。

### 提供者目录
Providers 目录包含应用程序的所有服务提供者。服务提供者通过在服务容器中绑定服务、注册事件或执行其他任务来引导应用程序，以便为传入请求做好准备。在新的 Laravel 应用程序中，该目录目前将包含一些提供者。你可以根据具体情况在此目录中添加自己的提供者。

### 规则目录
默认情况下没有此目录。但是，如果执行 make:rule Artisan 命令，将会为你创建该目录。Rules 目录包含应用程序的自定义验证规则对象。规则用于将复杂的验证逻辑封装在简单的对象中。

有关更多信息，请查阅验证文档。

Breeze 将其所有代码分发到你的应用程序中，以便你完全控制并查看其功能和性能。安装 Breeze 后，你还应编译资源，以便应用程序的 CSS 文件可用：

```
php artisan breeze:install
npm install
npm run dev
php artisan migrate
```

接下来，你可以在 Web 浏览器中导航到应用程序的 /login 或 /register URL。Breeze 的所有路由都在 routes/auth.php 文件中定义。

{tip} 要了解有关编译应用程序 CSS 和 JavaScript 的更多信息，请查阅 Laravel Mix 文档。

## Breeze & Inertia
Laravel Breeze 还提供由 Vue 或 React 驱动的 Inertia.js 前端实现。要使用 Inertia 栈，请在执行 breeze:install Artisan 命令时指定 vue 或 react 作为所需栈：

```
php artisan breeze:install vue

// or...

php artisan breeze:install react

npm install
npm run dev
php artisan migrate
```

## Breeze & Next.js / API
Laravel Breeze 还可以生成一个身份验证 API，该 API 可用于身份验证由 Next、Nuxt 等驱动的现代 JavaScript 应用程序。要开始使用，请在执行 breeze:install Artisan 命令时指定 api 栈作为所需栈：


```bash
php artisan breeze:install api

php artisan migrate
```

在安装过程中，Breeze 会在你的应用 `.env` 文件中添加一个 `FRONTEND_URL` 环境变量。这个 URL 应该是你的 JavaScript 应用的地址。在本地开发时，通常是 `http://localhost:3000`。此外，你应确保 `APP_URL` 设置为 `http://localhost:8000`，这是 `serve` Artisan 命令使用的默认 URL。

## Next.js 参考实现

最后，你可以将此后端与你选择的前端配对。Breeze 前端的 Next 参考实现可在 GitHub 上获取。该前端由 Laravel 维护，包含与 Breeze 提供的传统 Blade 和 Inertia 技术栈相同的用户界面。

## Laravel Jetstream

尽管 Laravel Breeze 为构建 Laravel 应用程序提供了一个简单且最小的起点，但 Jetstream 通过更强大的功能和额外的前端技术栈增强了该功能。对于刚接触 Laravel 的开发者，我们建议先通过 Laravel Breeze 学习基础知识，然后再升级到 Laravel Jetstream。Jetstream 为 Laravel 提供了设计精美的应用程序脚手架，包括登录、注册、电子邮件验证、双因素认证、会话管理、通过 Laravel Sanctum 提供的 API 支持，以及可选的团队管理。Jetstream 使用 Tailwind CSS 设计，并为你提供基于 Livewire 或 Inertia.js 驱动的前端脚手架。有关安装 Laravel Jetstream 的完整文档，可以在官方 Jetstream 文档中找到。

当配置被缓存时，`.env` 文件将不会被加载，所有针对 `.env` 变量的 `env` 函数调用都将返回 `null`。

## 优化路由加载

```bash
php artisan route:cache
```

该命令会将你所有的路由注册减少为缓存文件中的一次方法调用，从而在注册数百条路由时提高路由注册的性能。

## 优化视图加载

```bash
php artisan view:cache
```

该命令会预编译所有 Blade 视图，使它们不会被按需编译，从而提高每个返回视图的请求的性能。

## 调试模式

如果你想要一个完全无服务器、自动扩展且为 Laravel 调优的部署平台，请查看 Laravel Vapor。Laravel Vapor 是一个由 AWS 驱动的 Laravel 无服务器部署平台。在 Vapor 上启动你的 Laravel 基础设施，并爱上无服务器的可扩展简洁性。Laravel Vapor 由 Laravel 的创造者校准，确保与框架完美配合，因此你可以继续像往常一样构建你的 Laravel 应用程序。

# 请求生命周期

- 简介
- 生命周期概述
  - 第一步
  - HTTP / 控制台内核
  - 服务提供者
  - 路由
  - 收尾
- 专注于服务提供者

## 简介

在“现实世界”中使用任何工具时，如果你了解该工具的工作原理，你会更有信心。应用程序开发也不例外。当你了解开发工具如何运作时，你会更舒适、更有信心地使用它们。本文档的目标是让你对 Laravel 框架的工作原理有一个很好的高层概述。通过更好地了解整个框架，一切都会变得不那么“神奇”，你会更有信心构建你的应用程序。如果你不能马上理解所有术语，请不要灰心！只需试着基本掌握正在发生的事情，随着你探索文档的其他部分，你的知识会不断增长。

## 生命周期概述

### 第一步

所有请求进入 Laravel 应用程序的入口点是 `public/index.php` 文件。所有请求都由你的 Web 服务器（Apache / Nginx）配置指向该文件。`index.php` 文件包含的代码不多。相反，它是加载框架其余部分的起点。

`index.php` 文件加载 Composer 生成的自动加载器定义，然后从 `bootstrap/app.php` 获取 Laravel 应用程序实例。Laravel 自己做的第一件事是创建应用程序/服务容器的实例。

### HTTP / 控制台内核

### 路由

你的应用程序中最重要的服务提供者之一是 `App\Providers\RouteServiceProvider`。这个服务提供者加载应用程序目录中包含的路由文件。来吧，打开代码看看它是如何工作的！

一旦应用程序已经引导并且所有服务提供者都已注册，请求将被交给路由器进行分发。路由器会将请求分发到路由或控制器，并运行任何特定于路由的中间件。

中间件提供了一种方便的机制来过滤或检查进入你的应用程序的 HTTP 请求。例如，Laravel 包含一个中间件，用于验证你的应用程序用户是否已认证。如果用户未通过认证，中间件会将用户重定向到登录界面。然而，如果用户已认证，中间件将允许请求进一步进行到应用程序中。一些中间件被分配给应用程序中的所有路由，比如那些在你的 HTTP 内核属性中定义的中间件，而另一些则仅分配给特定的路由或路由组。你可以通过阅读完整的中间件文档来了解更多关于中间件的信息。如果请求通过了所有匹配路由的

服务提供者存储在 `app/Providers` 目录中。默认情况下，`AppServiceProvider` 相当空。这个提供者是一个很好的地方，可以添加你自己的引导和服务容器绑定。对于大型应用程序，你可能希望创建多个服务提供者，每个服务提供者为你的应用程序使用的特定服务提供更细粒度的引导。

# 服务容器

## 简介

- 零配置解析
- 何时使用容器

## 绑定

- 绑定基础
- 将接口绑定到实现
- 上下文绑定
- 绑定原始值
- 绑定类型化可变参数
- 标签
- 扩展绑定

## 解析

- 使用 Make 方法

```php
<?php

namespace App\Http\Controllers;

use App\Http\Controllers\Controller;
use App\Repositories\UserRepository;
use App\Models\User;

class UserController extends Controller
{
    /**
     * The user repository implementation.
     *
     * @var UserRepository
     */
    protected $users;

    /**
     * Create a new controller instance.
     *
     * @param UserRepository $users
     * @return void
     */
    public function __construct(UserRepository $users)
    {
        $this->users = $users;
    }

    /**
     * Show the profile for the given user.
     *
     * @param int $id
     * @return Response
     */
    public function show($id)
    {
        $user = $this->users->find($id);

        return view('user.profile', ['user' => $user]);
    }
}
```

在这个例子中，`UserController` 需要从数据源中检索用户。因此，我们将注入一个能够检索用户的服务。在这种情况下，我们的 `UserRepository` 很可能使用 Eloquent 从数据库中检索用户信息。然而，由于仓库是被注入的，我们可以轻松地用另一个实现替换它。在测试应用程序时，我们还可以轻松地“模拟”或创建 `UserRepository` 的虚拟实现。

深入了解 Laravel 服务容器对于构建强大、大型的应用程序以及为 Laravel 核心本身做出贡献至关重要。

## 零配置解析

如果一个类没有依赖，或者只依赖于其他具体类（而不是接口），容器不需要被指示如何解析该类。例如，你可以将以下代码放在你的 `routes/web.php` 文件中：


```
<?php

class Service
{
    //
}

Route::get('/', function (Service $service) {
    die(get_class($service));
});
```

在此示例中，访问应用程序的 / 路由时，将自动解析 Service 类并将其注入到路由的处理程序中。这是一个颠覆性的变化。这意味着你可以开发应用程序并利用依赖注入，而无需担心臃肿的配置文件。值得庆幸的是，在构建 Laravel 应用程序时，你编写的许多类会自动通过容器接收它们的依赖项，包括控制器、事件监听器、中间件等。此外，你可以在队列任务的 handle 方法中为依赖项添加类型提示。一旦你体验到自动且零配置依赖注入的强大功能，就很难想象没有它进行开发。

## 何时使用容器

由于零配置解析，你经常会在路由、控制器、事件监听器等地方为依赖项添加类型提示，而无需手动与容器交互。例如，你可以在路由定义上为 Illuminate\Http\Request 对象添加类型提示，以便轻松访问当前请求。即使我们编写此代码时无需与容器交互，它也在幕后管理这些依赖项的注入：

```
use Illuminate\Http\Request;

Route::get('/', function (Request $request) {
    // ...
});
```

在许多情况下，由于自动依赖注入和门面的存在，你可以构建 Laravel 应用程序，而无需手动从容器绑定或解析任何内容。那么，你会在什么时候手动与容器交互呢？让我们来看看两种情况。首先，如果你编写了一个实现接口的类，并且希望在路由或类构造函数上为该接口添加类型提示，你必须告诉容器如何解析该接口。其次，如果

请注意，我们将容器本身作为参数传递给解析器。然后我们可以使用容器来解析我们正在构建的对象的子依赖项。如前所述，你通常会在服务提供者中与容器交互；然而，如果你想在服务提供者之外与容器交互，可以通过 App 门面进行：

```php
use App\Services\Transistor;
use Illuminate\Support\Facades\App;

App::bind(Transistor::class, function ($app) {
    // ...
});
```

> {tip} 如果类不依赖于任何接口，则无需将其绑定到容器中。容器无需被告知如何构建这些对象，因为它可以使用反射自动解析这些对象。

## 绑定单例

singleton 方法将一个类或接口绑定到容器中，该类或接口只应解析一次。一旦单例绑定被解析，后续对容器的调用将返回相同的对象实例：

```php
use App\Services\Transistor;
use App\Services\PodcastParser;

$this->app->singleton(Transistor::class, function ($app) {
    return new Transistor($app->make(PodcastParser::class));
});
```

你可以轻松地注入带有该标签的所有容器绑定：

```
$this->app->when(ReportAggregator::class)
    ->needs('$reports')
    ->giveTagged('reports');
```

如果需要从应用程序的配置文件中注入一个值，可以使用 giveConfig 方法：

```
$this->app->when(ReportAggregator::class)
    ->needs('$timezone')
    ->giveConfig('app.timezone');
```

## 绑定类型化可变参数

有时，你可能有一个类使用可变参数构造函数参数接收一组类型化对象：

```
<?php

use App\Models\Filter;
use App\Services\Logger;

class Firewall
{
    /**
     * The logger instance.
     *
     * @var \App\Services\Logger
     */
    protected $logger;

    /**
     * The filter instances.
     *
     * @var array
     */
    protected $filters;

    /**
     * Create a new class instance.
```

```
$this->app->when(Firewall::class)
    ->needs(Filter::class)
    ->give([
        NullFilter::class,
        ProfanityFilter::class,
        TooLongFilter::class,
    ]);
```

## 可变参数标签依赖

有时，一个类可能具有可变参数依赖项，其类型提示为给定类（ Report ...$reports ）。使用 needs 和 giveTagged 方法，你可以轻松地为给定依赖项注入带有该标签的所有容器绑定。

```
$this->app->when(ReportAggregator::class)
    ->needs(Report::class)
    ->giveTagged('reports');
```

## 标签

有时，你可能需要解析某一类绑定中的所有内容。例如，也许

接受一个闭包作为其唯一参数，该闭包应返回修改后的服务。闭包接收正在解析的服务和容器实例：

```
$this->app->extend(Service::class, function ($service, $app) {
    return new DecoratedService($service);
});
```

## 解析

### make 方法

你可以使用 make 方法从容器中解析类实例。make 方法接受你希望解析的类或接口的名称：

```
use App\Services\Transistor;

$transistor = $this->app->make(Transistor::class);
```

如果你的某些类依赖项无法通过容器解析，你可以通过将它们作为关联数组传递给 makeWith 方法来注入它们。例如，我们可以手动传递 Transistor 服务所需的 $id 构造函数参数：

```
use App\Services\Transistor;

$transistor = $this->app->makeWith(Transistor::class, ['id' => 1]);
```

如果你在服务提供者之外，代码中的位置无法访问 $app 变量，可以使用 App 门面从容器中解析类实例：

```
use App\Services\Transistor;
use Illuminate\Support\Facades\App;

$transistor = App::make(Transistor::class);
```

如果你希望将 Laravel 容器实例本身注入到由容器解析的类中，可以在类的构造函数上为 Illuminate\Container\Container 类添加类型提示：

```
use Illuminate\Container\Container;

/**
 * Create a new class instance.
 *
 * @param \Illuminate\Container\Container $container
 * @return void
 */
public function __construct(Container $container)
{
    $this->container = $container;
}
```

## 自动注入

另外，重要的是，你可以在由容器解析的类的构造函数中为依赖项添加类型提示，包括控制器、事件监听器、中间件等。

此外，你可以在队列任务的 handle 方法中为依赖项添加类型提示。在实践中，这应该是大多数对象由容器解析的方式。

例如，你可以在控制器的构造函数中为应用程序定义的存储库添加类型提示。存储库将被自动解析并注入到类中：

```
<?php

namespace App\Http\Controllers;

use App\Repositories\UserRepository;

class UserController extends Controller
{
    /**
     * The user repository instance.
     *
     * @var \App\Repositories\UserRepository
     */
    protected $users;

    /**
     * Create a new controller instance.
     *
     * @param \App\Repositories\UserRepository $users
     * @return void
     */
    public function __construct(UserRepository $users)
    {
```

```
$this->users = $users;
}

/**
 * Show the user with the given ID.
 *
 * @param int $id
 * @return \Illuminate\Http\Response
 */
public function show($id)
{
    //
}
}
```

## 方法调用与注入

有时，你可能希望在对象实例上调用方法，同时允许容器自动注入该方法的依赖项。

例如，给定以下类：

在自动注入其依赖的同时调用闭包：

```php
use App\Repositories\UserRepository;
use Illuminate\Support\Facades\App;

$result = App::call(function (UserRepository $repository) {
    // ...
});
```

## 容器事件

服务容器在每次解析对象时都会触发一个事件。您可以使用 resolving 方法监听此事件：

```php
use App\Services\Transistor;

$this->app->resolving(Transistor::class, function ($transistor, $app) {
    // Called when container resolves objects of type "Transistor"...
});

$this->app->resolving(function ($object, $app) {
    // Called when container resolves object of any type...
});
```

如您所见，被解析的对象将被传递给回调，从而允许您在对象交付给其使用者之前设置任何附加属性。

## 编写服务提供者

所有服务提供者都扩展 Illuminate\Support\ServiceProvider 类。

大多数服务提供者包含 register 和 boot 方法。在 register 方法中，您应该只将事物绑定到服务容器中。您绝不应尝试在 register 方法中注册任何事件监听器、路由或任何其他功能。

Artisan CLI 可以通过 make:provider 命令生成新的提供者：

```
php artisan make:provider RiakServiceProvider
```

## Register 方法

如前所述，在 register 方法中，您应该只将事物绑定到服务容器中。您绝不应尝试在 register 方法中注册任何事件监听器、路由或任何其他功能。否则，您可能会意外使用尚未加载的服务提供者提供的服务。让我们看一个基本的服务提供者。在您的任何服务提供者方法中，您始终可以访问 $app 属性，它提供了对服务容器的访问：

```php
<?php

namespace App\Providers;

use App\Services\Riak\Connection;
use Illuminate\Support\ServiceProvider;

class RiakServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     *
     * @return void
     */
    public function register()
    {
        $this->app->singleton(Connection::class, function ($app) {
            return new Connection(config('riak'));
        });
    }
}
```

此服务提供者仅定义了 register 方法，并使用该方法在服务容器中定义 App\Services\Riak\Connection 的实现。如果您尚未熟悉 Laravel 的服务容器，请查看其文档。

## bindings 和 singletons 属性

如果您的服务提供者注册了许多简单的绑定，您可能希望使用 bindings 和 singletons 属性，而不是手动注册每个容器绑定。当框架加载服务提供者时，它会自动检查这些属性并注册其绑定：

```php
<?php

namespace App\Providers;

use App\Contracts\DowntimeNotifier;
use App\Contracts\ServerProvider;
use App\Services\DigitalOceanServerProvider;
use App\Services\PingdomDowntimeNotifier;
use App\Services\ServerToolsProvider;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    /**
     * All of the container bindings that should be registered.
     *
     * @var array
     */
    public $bindings = [
        ServerProvider::class => DigitalOceanServerProvider::class,
    ];

    /**
```

```php
<?php

namespace App\Providers;

use Illuminate\Support\Facades\View;
use Illuminate\Support\ServiceProvider;

class ComposerServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        View::composer('view', function () {
            //
        });
    }
}
```

## Boot 方法依赖注入

您可以在服务提供者的 boot 方法中为依赖项添加类型提示。服务容器将自动注入您需要的任何依赖项：

view、response、url、config 等。Laravel 提供的每个辅助函数都与其对应功能一起记录；不过，完整列表可在专门的辅助函数文档中找到。例如，与使用 Illuminate\Support\Facades\Response 门面生成 JSON 响应相比，我们可以简单地使用 response 函数。由于辅助函数是全局可用的，因此您无需导入任何类即可使用它们：

```php
use Illuminate\Support\Facades\Response;

Route::get('/users', function () {
    return Response::json([
        // ...
    ]);
});

Route::get('/users', function () {
    return response()->json([
        // ...
    ]);
});
```

## 何时使用门面

门面有很多好处。它们提供简洁、易记的语法，让您无需记住必须手动注入或配置的长类名即可使用 Laravel 的功能。此外，由于其对 PHP 动态方法的独特使用，它们易于测试。然而，使用门面时必须谨慎。门面的主要危险是类的“范围蔓延”。由于门面易于使用且不需要注入，很容易让您的类不断增长并在单个类中使用许多门面。使用依赖注入，这种可能性通过大型构造函数给出的视觉反馈得到缓解，表明您的类增长过大。因此，使用门面时，请特别注意类的大小，以保持其职责范围狭窄。如果您的类变得过大，请考虑将其拆分为多个较小的类。

## 门面与依赖注入

依赖注入的主要好处之一是可以交换注入类的实现。这在测试期间很有用，因为您可以注入 mock 或 stub 并断言 stub 上的各种方法已被调用。通常，不可能模拟或 stub 真正的静态类方法。然而，由于门面使用动态方法将方法调用代理到从服务容器解析的对象，我们实际上可以像测试注入的类实例一样测试门面。例如，给定以下路由：

```php
use Illuminate\Support\Facades\Cache;

Route::get('/cache', function () {
    return Cache::get('key');
});
```

使用 Laravel 的门面测试方法，我们可以编写以下测试来验证 Cache::get 方法是否使用我们期望的参数被调用：

```php
use Illuminate\Support\Facades\Cache;

/**
 * A basic functional test example.
 *
 */
```

```php
return Illuminate\Support\Facades\View::make('profile');

return view('profile');
```

门面和辅助函数之间绝对没有任何实际区别。使用辅助函数时，您仍然可以像测试相应的门面一样对其进行测试。例如，给定以下路由：

```php
Route::get('/cache', function () {
    return cache('key');
});
```

在内部，cache 辅助函数将调用 Cache 门面底层类的 get 方法。因此，即使我们使用的是辅助函数，我们也可以编写以下测试来验证方法是否使用我们期望的参数被调用：

```php
use Illuminate\Support\Facades\Cache;

/**
 * A basic functional test example.
 *
 * @return void
 */
public function testBasicExample()
{
    Cache::shouldReceive('get')
        ->with('key')
        ->andReturn('value');

    $response = $this->get('/cache');

    $response->assertSee('value');
}
```

## 门面如何工作

在 Laravel 应用程序中，门面是一个提供对容器中对象的访问的类。使这项工作得以实现的机制在 Facade 类中。Laravel 的门面以及您创建的任何自定义门面都将扩展

```php
<?php

namespace App\Http\Controllers;

use App\Http\Controllers\Controller;
use Illuminate\Support\Facades\Cache;

class UserController extends Controller
{
    /**
     * Show the profile for the given user.
     *
     * @param int $id
     * @return Response
     */
    public function showProfile($id)
    {
        $user = Cache::get('user:'.$id);

        return view('profile', ['user' => $user]);
    }
}
```

请注意，在文件顶部我们正在“导入”Cache 门面。此门面作为访问 Illuminate\Contracts\Cache\Factory 接口底层实现的代理。我们使用门面进行的任何调用都将传递给 Laravel 缓存服务的底层实例。

如果我们查看 Illuminate\Support\Facades\Cache 类，你会发现其中没有静态方法 get：

```php
class Cache extends Facade
{
    /**
     * Get the registered name of the component.
     *
     * @return string
     */
    protected static function getFacadeAccessor() { return 'cache'; }
}
```

相反，Cache 门面扩展了基础的 Facade 类并定义了 getFacadeAccessor() 方法。该方法的工作是返回服务容器绑定的名称。当用户在 Cache 门面上引用任何静态方法时，Laravel 会从服务容器中解析缓存绑定并在该对象上运行请求的方法（在本例中为 get）。

## 实时门面

使用实时门面，你可以将应用程序中的任何类视为门面。为了说明其用法，我们先来看一段不使用实时门面的代码。

例如，假设我们的 Podcast 模型有一个 publish 方法。然而，为了发布播客，我们需要注入一个 Publisher 实例：

```php
<?php

namespace App\Models;

use App\Contracts\Publisher;
use Illuminate\Database\Eloquent\Model;

class Podcast extends Model
{
    /**
     * Publish the podcast.
     *
     * @param Publisher $publisher
     * @return void
     */
    public function publish(Publisher $publisher)
    {
        $this->update(['publishing' => now()]);

        $publisher->publish($this);
    }
}
```

当使用实时门面时，publisher 实现将使用接口或类名中 Facades 前缀之后的部分从服务容器中解析出来。在测试时，我们可以使用 Laravel 内置的门面测试助手来模拟此方法调用：

```php
<?php

namespace Tests\Feature;

use App\Models\Podcast;
use Facades\App\Contracts\Publisher;
use Illuminate\Foundation\Testing\RefreshDatabase;
use Tests\TestCase;

class PodcastTest extends TestCase
{
    use RefreshDatabase;

    /**
     * A test example.
     *
     * @return void
     */
    public function test_podcast_can_be_published()
    {
        $podcast = Podcast::factory()->create();

        Publisher::shouldReceive('publish')->once()->with($podcast);

        $podcast->publish();
    }
}
```

## 门面类参考

下面你将找到每个门面及其底层类。这是一个有用的工具，可快速查阅给定门面根的 API 文档。服务容器绑定键也在适用时包含在内。

| 门面 | 类 | 服务容器绑定 |
|---|---|---|
| App | Illuminate\Foundation\Application | app |
| Artisan | Illuminate\Contracts\Console\Kernel | artisan |
| Auth | Illuminate\Auth\AuthManager | auth |
| Auth (Instance) | Illuminate\Contracts\Auth\Guard | auth.driver |
| Blade | Illuminate\View\Compilers\BladeCompiler | blade.compiler |
| Broadcast | Illuminate\Contracts\Broadcasting\Factory |  |
| Broadcast (Instance) | Illuminate\Contracts\Broadcasting\Broadcaster |  |
| Bus | Illuminate\Contracts\Bus\Dispatcher |  |
| Cache | Illuminate\Cache\CacheManager | cache |
| Cache (Instance) | Illuminate\Cache\Repository | cache.store |
| Config | Illuminate\Config\Repository | config |
| Cookie | Illuminate\Cookie\CookieJar | cookie |
| Crypt | Illuminate\Encryption\Encrypter | encrypter |
| Date | Illuminate\Support\DateFactory | date |
| DB | Illuminate\Database\DatabaseManager | db |
| DB (Instance) | Illuminate\Database\Connection | db.connection |
| Event | Illuminate\Events\Dispatcher | events |
| File | Illuminate\Filesystem\Filesystem | files |
| Gate | Illuminate\Contracts\Auth\Access\Gate |  |
| Hash | Illuminate\Contracts\Hashing\Hasher | hash |
| Http | Illuminate\Http\Client\Factory |  |
| Lang | Illuminate\Translation\Translator | translator |
| Log | Illuminate\Log\LogManager | log |
| Mail | Illuminate\Mail\Mailer | mailer |
| Notification | Illuminate\Notifications\ChannelManager |  |
| Password | Illuminate\Auth\Passwords\PasswordBrokerManager | auth.password |
| Password (Instance) | Illuminate\Auth\Passwords\PasswordBroker | auth.password.broker |
| Queue | Illuminate\Queue\QueueManager | queue |
| Queue | Illuminate\Contracts\Queue\Queue | queue.connection |

保护。routes/api.php 中的路由是无状态的，并被分配了 api 中间件组。

对于大多数应用程序，你将首先在 routes/web.php 文件中定义路由。routes/web.php 中定义的路由可以通过在浏览器中输入定义的路由 URL 来访问。例如，你可以通过在浏览器中导航到 http://example.com/user 来访问以下路由：

```
use App\Http\Controllers\UserController;

Route::get('/user', [UserController::class, 'index']);
```

routes/api.php 文件中定义的路由由 RouteServiceProvider 嵌套在路由组中。在此组内，/api URI 前缀会自动应用，因此你无需手动将其应用于文件中的每条路由。你可以通过修改 RouteServiceProvider 类来修改前缀和其他路由组选项。

## 可用路由方法

路由器允许你注册响应任何 HTTP 动词的路由：

```
Route::get($uri, $callback);
Route::post($uri, $callback);
Route::put($uri, $callback);
Route::patch($uri, $callback);
Route::delete($uri, $callback);
Route::options($uri, $callback);
```

有时你可能需要注册一条响应多个 HTTP 动词的路由。你可以使用 match 方法来实现。或者，你甚至可以使用 any 方法注册一条响应所有 HTTP 动词的路由：

```
Route::match(['get', 'post'], '/', function () {
    //
});

Route::any('/', function () {
    //
});
```

> {tip} 当定义多个共享相同 URI 的路由时，使用 get、post、put、patch、delete 和 options 方法的路由应在使用 any、match 和 redirect 方法的路由之前定义。这可确保传入请求与正确的路由匹配。

## 依赖注入

你可以在路由的回调签名中为路由所需的任何依赖项添加类型提示。声明的依赖项将由 Laravel 服务容器自动解析并注入到回调中。例如，你可以为 Illuminate\Http\Request 类添加类型提示，以便将当前 HTTP 请求自动注入到路由回调中：

```php
use Illuminate\Http\Request;

Route::get('/users', function (Request $request) {
    // ...
});
```

## CSRF 保护

请记住，指向在 web 路由文件中定义的 POST、PUT、PATCH 或 DELETE 路由的任何 HTML 表单都应包含 CSRF 令牌字段。否则，请求将被拒绝。你可以在 CSRF 文档中阅读有关 CSRF 保护的更多信息：

```blade
<form method="POST" action="/profile">
    @csrf
    ...
</form>
```

## 重定向路由



```php
Route::get('/search/{search}', function ($search) {
    return $search;
})->where('search', '.*');
```

> {note} 编码的正斜杠仅在最后一个路由段中受支持。

## 命名路由

命名路由允许为特定路由方便地生成 URL 或重定向。您可以通过将 `name` 方法链式调用到路由定义上来为路由指定名称：

```php
Route::get('/user/profile', function () {
    //
})->name('profile');
```

您也可以为控制器操作指定路由名称：

```php
Route::get(
    '/user/profile',
    [UserProfileController::class, 'show']
)->name('profile');
```

> {note} 路由名称应始终唯一。

### 生成命名路由的 URL

一旦您为给定路由分配了名称，就可以使用路由的名称通过 Laravel 的 `route` 和 `redirect` 辅助函数生成 URL 或重定向：

```php
// Generating URLs...
$url = route('profile');

// Generating Redirects...
return redirect()->route('profile');
```

如果命名路由定义了参数，您可以将参数作为 `route` 函数的第二个参数传递。给定的参数将自动以正确的位置插入到生成的 URL 中：

```php
Route::get('/user/{id}/profile', function ($id) {
    //
})->name('profile');

$url = route('profile', ['id' => 1]);
```

如果您在数组中传递额外参数，这些键/值对将自动添加到生成的 URL 的查询字符串中：

```php
Route::get('/user/{id}/profile', function ($id) {
    //
})->name('profile');

$url = route('profile', ['id' => 1, 'photos' => 'yes']);

// /user/1/profile?photos=yes
```

> {tip} 有时，您可能希望为 URL 参数指定请求范围的默认值，例如当前语言环境。为此，您可以使用 `URL::defaults` 方法。

### 检查当前路由

如果您想确定当前请求是否路由到给定的命名路由，可以在 `Route` 实例上使用 `named` 方法。例如，您可以从路由中间件中检查当前路由名称：

## 路由组

前缀将被附加。命名空间分隔符和 URI 前缀中的斜杠会根据需要自动添加。

### 中间件

要为组内的所有路由分配中间件，可以在定义组之前使用 `middleware` 方法。中间件按其在数组中列出的顺序执行：

```php
Route::middleware(['first', 'second'])->group(function () {
    Route::get('/', function () {
        // Uses first & second middleware...
    });

    Route::get('/user/profile', function () {
        // Uses first & second middleware...
    });
});
```

### 控制器

如果一组路由都使用相同的控制器，可以使用 `controller` 方法为组内所有路由定义公共控制器。然后，在定义路由时，只需提供它们调用的控制器方法即可：

### 路由前缀

```php
Route::prefix('admin')->group(function () {
    Route::get('/users', function () {
        // Matches The "/admin/users" URL
    });
});
```

### 路由名称前缀

`name` 方法可用于为组中每个路由名称添加给定字符串作为前缀。例如，您可能希望将所有分组路由的名称都以 `admin` 为前缀。给定的字符串会按原样添加到路由名称前缀中，因此我们应确保在前缀中提供尾部的 `.` 字符：

```php
Route::name('admin.')->group(function () {
    Route::get('/users', function () {
        // Route assigned name "admin.users"...
    })->name('users');
});
```

## 路由模型绑定

具有与请求 URI 中对应值匹配的 ID。如果在数据库中找不到匹配的模型实例，将自动生成 404 HTTP 响应。

当然，使用控制器方法时也可能进行隐式绑定。再次注意，`{user}` URI 段与控制器中包含 `App\Models\User` 类型提示的 `$user` 变量匹配：

```php
use App\Http\Controllers\UserController;
use App\Models\User;

// Route definition...
Route::get('/users/{user}', [UserController::class, 'show']);

// Controller method definition...
public function show(User $user)
{
    return view('user.profile', ['user' => $user]);
}
```

### 软删除模型

通常，隐式模型绑定不会检索已被软删除的模型。但是，您可以通过将 `withTrashed` 方法链式调用到路由定义上来指示隐式绑定检索这些模型：

```php
use App\Models\User;

Route::get('/users/{user}', function (User $user) {
    return $user->email;
})->withTrashed();
```

### 自定义键

有时您可能希望使用 `id` 以外的列解析 Eloquent 模型。为此，您可以在路由参数定义中指定列：

```php
use App\Models\Post;

Route::get('/posts/{post:slug}', function (Post $post) {
    return $post;
});
```

如果您希望在检索给定模型类时模型绑定始终使用 `id` 以外的数据库列，可以重写 Eloquent 模型上的 `getRouteKeyName` 方法：

```php
/**
 * Get the route key for the model.
 *
 * @return string
 */
public function getRouteKeyName()
{
    return 'slug';
}
```

### 自定义键与作用域

在单个路由定义中隐式绑定多个 Eloquent 模型时，您可能希望将第二个 Eloquent 模型限定为必须是前一个 Eloquent 模型的子级。例如，考虑以下路由定义，它为特定用户按 slug 检索博客文章：

```php
use App\Models\Post;
use App\Models\User;

Route::get('/users/{user}/posts/{post:slug}', function (User $user, Post $post) {
    return $post;
});
```

使用自定义键的隐式绑定作为嵌套路由参数时，Laravel 将自动限定查询以按检索嵌套模型

由于我们已将所有 `{user}` 参数绑定到 `App\Models\User` 模型，因此该类的实例将被注入到路由中。因此，例如，对 `users/1` 的请求将注入数据库中 ID 为 `1` 的 `User` 实例。如果在数据库中找不到匹配的模型实例，将自动生成 404 HTTP 响应。

### 自定义解析逻辑

如果您希望定义自己的模型绑定解析逻辑，可以使用 `Route::bind` 方法。传递给 `bind` 方法的闭包将接收 URI 段的值，并应返回应注入到路由中的类的实例。再次强调，此自定义应放在应用程序的 `RouteServiceProvider` 的 `boot` 方法中：

```php
use App\Models\User;
use Illuminate\Support\Facades\Route;

/**
 * Define your route model bindings, pattern filters, etc.
 *
 * @return void
 */
public function boot()
{
    Route::bind('user', function ($value) {
        return User::where('name', $value)->firstOrFail();
    });

    // ...
}
```

或者，您可以重写 Eloquent 模型上的 `resolveRouteBinding` 方法。此方法将接收 URI 段的值，并应返回应注入到路由中的类的实例：

```php
/**
 * Retrieve the model for a bound value.
 *
 * @param mixed $value
 * @param string|null $field
 * @return \Illuminate\Database\Eloquent\Model|null
 */
public function resolveRouteBinding($value, $field = null)
{
    return $this->where('name', $value)->firstOrFail();
}
```

如果路由使用隐式绑定作用域，则将使用 `resolveChildRouteBinding` 方法来解析父模型的子绑定：

```php
/**
 * Retrieve the child model for a bound value.
 *
 * @param string $childType
 * @param mixed $value
 * @param string|null $field
 * @return \Illuminate\Database\Eloquent\Model|null
 */
public function resolveChildRouteBinding($childType, $value, $field)
{
    return parent::resolveChildRouteBinding($childType, $value, $field);
}
```

## 回退路由



使用 `Route::fallback` 方法，你可以定义一条路由，当没有其他路由匹配传入请求时，该路由将被执行。通常，未处理的请求会通过应用程序的异常处理器自动渲染“404”页面。然而，由于你通常会在 `routes/web.php` 文件中定义回退路由，`web` 中间件组中的所有中间件都将应用于该路由。你可以根据需要向此路由添加额外的中间件：

```php
Route::fallback(function () {
    //
});
```

> {note} 回退路由应始终是应用程序注册的最后一个路由。

## 速率限制

### 定义速率限制器

Laravel 包含功能强大且可定制的速率限制服务，你可以利用它来限制给定路由或路由组的流量。为了开始，你应该定义满足应用程序需求的速率限制器配置。通常，这应该在应用程序的 `App\Providers\RouteServiceProvider` 类的 `configureRateLimiting` 方法中完成。速率限制器使用 `RateLimiter` 门面的 `for` 方法定义。

`for` 方法接受一个速率限制器名称和一个闭包，该闭包返回应应用于分配给速率限制器的路由的限制配置。限制配置是 `Illuminate\Cache\RateLimiting\Limit` 类的实例。该类包含有用的“builder”方法，以便你可以快速定义限制。速率限制器名称可以是你想要的任何字符串：

```php
use Illuminate\Cache\RateLimiting\Limit;
use Illuminate\Support\Facades\RateLimiter;

/**
 * Configure the rate limiters for the application.
 *
 * @return void
 */
protected function configureRateLimiting()
{
    RateLimiter::for('global', function (Request $request) {
        return Limit::perMinute(1000);
    });
}
```

如果传入请求超过指定的速率限制，Laravel 将自动返回带有 429 HTTP 状态码的响应。如果你想定义速率限制应返回的自定义响应，可以使用 `response` 方法：

```php
RateLimiter::for('global', function (Request $request) {
    return Limit::perMinute(1000)->response(function () {
        return response('Custom response...', 429);
    });
});
```

由于速率限制器回调接收传入的 HTTP 请求实例，你可以根据传入请求或已认证用户动态构建适当的速率限制：

```php
RateLimiter::for('uploads', function (Request $request) {
    return $request->user()->vipCustomer()
        ? Limit::none()
        : Limit::perMinute(100);
});
```

### 分段速率限制

有时你可能希望按某个任意值对速率限制进行分段。例如，你可能希望允许用户每分钟每个 IP 地址访问给定路由 100 次。为了实现这一点，你可以在构建速率限制时使用 `by` 方法：

```php
RateLimiter::for('uploads', function (Request $request) {
    return $request->user()->vipCustomer()
        ? Limit::none()
        : Limit::perMinute(100)->by($request->ip());
});
```

为了用另一个示例说明此功能，我们可以将路由访问限制为每个已认证用户 ID 每分钟 100 次，或访客每分钟每个 IP 地址 10 次：

```php
RateLimiter::for('uploads', function (Request $request) {
    return $request->user()
        ? Limit::perMinute(100)->by($request->user()->id)
        : Limit::perMinute(10)->by($request->ip());
});
```

### 多个速率限制

如果需要，你可以为给定的速率限制器配置返回一个速率限制数组。每个速率限制将根据其在数组中的顺序对路由进行评估：

```php
RateLimiter::for('login', function (Request $request) {
    return [
        Limit::perMinute(500),
        Limit::perMinute(3)->by($request->input('email')),
    ];
});
```

### 将速率限制器附加到路由

速率限制器可以使用 `throttle` 中间件附加到路由或路由组。`throttle` 中间件接受你希望分配给路由的速率限制器的名称：

```php
Route::middleware(['throttle:uploads'])->group(function () {
    Route::post('/audio', function () {
        //
    });

    Route::post('/video', function () {
        //
    });
});
```

### 使用 Redis 进行节流

通常，`throttle` 中间件映射到 `Illuminate\Routing\Middleware\ThrottleRequests` 类。此映射在应用程序的 HTTP 内核（`App\Http\Kernel`）中定义。然而，如果你使用 Redis 作为应用程序的缓存驱动程序，你可能希望更改此映射以使用 `Illuminate\Routing\Middleware\ThrottleRequestsWithRedis` 类。此类在利用 Redis 管理速率限制时更高效：

```php
'throttle' => \Illuminate\Routing\Middleware\ThrottleRequestsWithRedis::class,
```

## 表单方法伪装

HTML 表单不支持 PUT、PATCH 或 DELETE 操作。因此，当定义从 HTML 表单调用的 PUT、PATCH 或 DELETE 路由时，你需要在表单中添加一个隐藏的 `_method` 字段。随 `_method` 字段发送的值将用作 HTTP 请求方法：

```html
<form action="/example" method="POST">
    <input type="hidden" name="_method" value="PUT">
    <input type="hidden" name="_token" value="{{ csrf_token() }}">
</form>
```

为方便起见，你可以使用 `@method` Blade 指令生成 `_method` 输入字段：

```html
<form action="/example" method="POST">
    @method('PUT')
    @csrf
</form>
```

## 访问当前路由

你可以在 `Route` 门面上使用 `current`、`currentRouteName` 和 `currentRouteAction` 方法来访问处理传入请求的路由的信息：

```php
use Illuminate\Support\Facades\Route;

$route = Route::current(); // Illuminate\Routing\Route
$name = Route::currentRouteName(); // string
$action = Route::currentRouteAction(); // string
```

你可以参考 `Route` 门面底层类和 `Route` 实例的 API 文档，以查看路由器和路由类上可用的所有方法。

## 跨域资源共享（CORS）

Laravel 可以使用你配置的值自动响应 CORS OPTIONS HTTP 请求。所有 CORS 设置都可以在应用程序的 `config/cors.php` 配置文件中配置。OPTIONS 请求将自动由默认包含在全局中间件栈中的 `HandleCors` 中间件处理。你的全局中间件栈位于应用程序的 HTTP 内核（`App\Http\Kernel`）中。

## 中间件

- 介绍
- 定义中间件
- 注册中间件
  - 全局中间件
  - 排除中间件
  - 中间件组
  - 排序中间件
- 中间件参数
- 可终止中间件

### 介绍

中间件为检查和过滤进入应用程序的 HTTP 请求提供了一种便捷的机制。例如，Laravel 包含一个中间件，用于验证应用程序用户的身份是否已认证。如果用户未通过身份验证，中间件将把用户重定向到应用程序的登录屏幕。但是，如果用户已通过身份验证，中间件将允许请求进一步进入应用程序。除了身份验证之外，还可以编写额外的中间件来执行各种任务。例如，日志中间件可能会记录应用程序收到的所有传入请求。Laravel 框架中包含了一些中间件，包括用于身份验证和 CSRF 保护的中间件。所有这些中间件都位于 `app/Http/Middleware` 目录中。

### 定义中间件

要创建新的中间件，请使用 `make:middleware` Artisan 命令：

```bash
php artisan make:middleware EnsureTokenIsValid
```

此命令将在你的 `app/Http/Middleware` 目录中放置一个新的 `EnsureTokenIsValid` 类。在此中间件中，我们仅在提供的 `token` 输入匹配指定值时才允许访问路由。否则，我们将把用户重定向回主页 URI：

```php
<?php

namespace App\Http\Middleware;

use Closure;

class EnsureTokenIsValid
{
    /**
     * Handle an incoming request.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  \Closure  $next
     * @return mixed
     */
    public function handle($request, Closure $next)
    {
        if ($request->input('token') !== 'my-secret-token') {
            return redirect('home');
        }

        return $next($request);
    }
}
```

正如你所见，如果给定的令牌与我们的 secret token 不匹配，中间件将向客户端返回一个 HTTP 重定向；否则，请求将被传递到应用程序的更深处。要将请求传递到应用程序的更深处（允许中间件“放行”），你应该使用 $request 调用 $next 回调。最好将中间件想象成一系列“层”，HTTP 请求必须穿过这些层才能到达你的应用程序。每一层都可以检查请求，甚至完全拒绝它。

> {tip} 所有中间件都通过服务容器解析，因此你可以在中间件的构造函数中为所需的任何依赖项进行类型提示。

## 中间件与响应

当然，中间件可以在将请求传递到应用程序的更深处之前或之后执行任务。例如，以下中间件将在请求由应用程序处理之前执行某些任务：

```php
\Illuminate\Routing\Middleware\SubstituteBindings::class,
\Illuminate\Auth\Middleware\Authorize::class,
];
```

## 中间件参数

中间件还可以接收额外的参数。例如，如果你的应用程序需要在执行某个操作之前验证已认证用户是否具有给定的“角色”，你可以创建一个 EnsureUserHasRole 中间件，使其接收角色名称作为额外参数。

额外的中间件参数将在 $next 参数之后传递给中间件：

app/Http/Kernel.php 文件。当在中间件上调用 terminate 方法时，Laravel 将从服务容器解析中间件的新实例。如果你希望在调用 handle 和 terminate 方法时使用同一个中间件实例，请使用容器的 singleton 方法将中间件注册到容器中。通常这应该在你的 AppServiceProvider 的 register 方法中完成：

```php
use App\Http\Middleware\TerminatingMiddleware;

/**
 * Register any application services.
 *
 * @return void
 */
public function register()
{
    $this->app->singleton(TerminatingMiddleware::class);
}
```

email 输入字段用于包含用户希望开始使用的电子邮件地址。如果没有 CSRF 保护，恶意网站可以创建一个指向你应用程序 /user/email 路由的 HTML 表单并提交恶意用户自己的电子邮件地址：

```html
<form action="https://your-application.com/user/email" method="POST">
    <input type="email" value="malicious-email@example.com">
</form>

<script>
    document.forms[0].submit();
</script>
```

如果恶意网站在页面加载时自动提交表单，恶意用户只需诱骗你应用程序的某个毫无防备的用户访问其网站，其电子邮件地址就会在你的应用程序中被更改。

为了防止此漏洞，我们需要检查每个传入的 POST、PUT、PATCH 或 DELETE 请求，以查找恶意应用程序无法访问的 secret 会话值。

## 防止 CSRF 请求

Laravel 会为应用程序管理的每个活动用户会话自动生成一个 CSRF “token”。此令牌用于验证已认证用户确实是向应用程序发出请求的人。由于此令牌存储在用户的会话中，并且在会话每次重新生成时都会更改，恶意应用程序无法访问它。当前会话的 CSRF 令牌可以通过请求的会话或通过 csrf_token 辅助函数访问：

```php
use Illuminate\Http\Request;

Route::get('/token', function (Request $request) {
    $token = $request->session()->token();
    
    $token = csrf_token();
    
    // ...
});
```

只要你在应用程序中定义“POST”、“PUT”、“PATCH”或“DELETE” HTML 表单，你都应该在表单中包含一个隐藏的 CSRF _token 字段，以便 CSRF 保护中间件可以验证请求。为了方便，你可以使用 @csrf Blade 指令生成隐藏的令牌输入字段：

```html
<form method="POST" action="/profile">
    @csrf

    <!-- Equivalent to... -->
    <input type="hidden" name="_token" value="{{ csrf_token() }}" />
</form>
```

App\Http\Middleware\VerifyCsrfToken 中间件默认包含在 web 中间件组中，将自动验证请求输入中的令牌是否与存储在会话中的令牌匹配。当这两个令牌匹配时，我们就知道已认证用户是发起请求的人。

## CSRF 令牌与 SPA

如果你正在构建一个使用 Laravel 作为 API 后端的 SPA，你应该查阅 Laravel Sanctum 文档，了解有关使用 API 进行身份验证以及防止 CSRF 漏洞的信息。

## 从 CSRF 保护中排除 URI

有时你可能希望从 CSRF 保护中排除一组 URI。

例如，如果你使用 Stripe 处理付款并使用其 webhook 系统，你需要将 Stripe webhook 处理程序路由从 CSRF 保护中排除，因为 Stripe 不会知道向你的路由发送什么 CSRF 令牌。

通常，你应该将这类路由放在 App\Providers\RouteServiceProvider 应用于 routes/web.php 文件中所有路由的 web 中间件组之外。

然而，你也可以通过将它们的 URI 添加到 VerifyCsrfToken 中间件的 $except 属性来排除这些路由：

```php
<?php

namespace App\Http\Middleware;

use Illuminate\Foundation\Http\Middleware\VerifyCsrfToken as Middleware;

class VerifyCsrfToken extends Middleware
{
    /**
     * The URIs that should be excluded from CSRF verification.
     *
     * @var array
     */
    protected $except = [
        'stripe/*',
        'http://example.com/foo/bar',
        'http://example.com/foo/*',
    ];
}
```

> {tip} 为了方便，在运行测试时，CSRF 中间件会自动为所有路由禁用。

## X-CSRF-TOKEN

除了将 CSRF 令牌作为 POST 参数进行检查外，App\Http\Middleware\VerifyCsrfToken 中间件还会检查 X-CSRF-TOKEN 请求头。例如，你可以将令牌存储在 HTML meta 标签中

```html
<meta name="csrf-token" content="{{ csrf_token() }}">
```

然后，你可以指示像 jQuery 这样的库自动将令牌添加到所有请求头中。

这为使用传统 JavaScript 技术构建的基于 AJAX 的应用程序提供了简单便捷的 CSRF 保护：

```js
$.ajaxSetup({
    headers: {
        'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
    }
});
```

## X-XSRF-TOKEN

Laravel 将正在进行的 CSRF 令牌存储在框架创建的每个响应中都包含的编码 XSRF-TOKEN cookie 中。你可以使用 cookie 的值来设置 X-XSRF-TOKEN 请求头。

此 cookie 主要作为开发人员便利而发送，因为某些 JavaScript 框架和库（如 Angular 和 Axios）会在同源请求上自动将其值放在 X-XSRF-TOKEN 头中。

> {tip} 默认情况下，resources/js/bootstrap.js 文件包含 Axios HTTP 库，它会自动为你发送 X-XSRF-TOKEN 头。


<!-- no content -->