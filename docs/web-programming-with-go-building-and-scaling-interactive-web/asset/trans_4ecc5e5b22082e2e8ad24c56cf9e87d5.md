

# 项目目录结构

## 1. cmd/server
包含启动服务器的主函数，是 Web 应用程序的入口点。

## 2. pkg 目录
用于存放库和包的位置。包含可能不专属于 Web 应用程序的共享逻辑和组件，未来可能用于命令行工具或其他应用程序。

*   `pkg/models`: 必要的数据结构，如 `book.go` 或 `user.go`。
*   `pkg/utils`: 实用函数，如用于身份验证机制的 `auth.go` 或各种辅助函数的 `helpers.go`。

## 3. api 目录
鉴于现代 Web 应用中清晰 API 定义的重要性：

*   `api/definitions`: 潜在的 OpenAPI 或 gRPC 定义，详细说明服务器提供的契约。

## 4. web 目录
所有前端相关内容：

*   `web/static`: 静态资产，包括 CSS、JS、图片，甚至第三方库。
*   `web/templates`: Go HTML 模板，允许动态内容渲染。

## 5. internal 目录
仅供此应用程序使用，不供外部使用的代码：

*   `internal/handlers`: HTTP 处理程序，如用于提供书籍相关请求的 `bookHandler.go` 或用于用户操作的 `userHandler.go`。
*   `internal/middleware`: 必要的中间件函数，用于日志记录、CORS 或身份验证等任务。
*   `internal/config`: 配置相关逻辑，可能是 `config.go`，用于获取和解析配置详细信息。

## 6. scripts 目录
任何有助于开发、部署或其他操作的脚本：

*   `scripts/deploy.sh`: 用于处理部署的潜在脚本。
*   `scripts/test.sh`: 在整个项目中运行测试或 linter。

## 7. database 目录
用于数据库相关文件和脚本：

*   `database/migrations`: SQL 脚本或其他迁移工具，以确保数据库结构一致性。
*   `database/seeds`: 脚本或数据文件，用于将初始数据种子到数据库中。

## 8. docs 目录
用于全面文档，除主 README 之外：

*   `docs/setup.md`: 设置和安装说明。
*   `docs/api.md`: API 端点、请求-响应示例和其他 API 相关文档。

# 创建目录结构

要设置此结构，可以使用简单的终端命令：

```
mkdir gitforgits-bookstore && cd gitforgits-bookstore
mkdir cmd pkg api web internal scripts database docs
mkdir cmd/server pkg/models pkg/utils api/definitions web/static web/templates internal/handlers internal/middleware internal/config database/migrations database/seeds
touch go.mod README.md LICENSE
```

所概述的目录结构既符合 Go 最佳实践，又针对 GitforGits Bookstore Web App 的特定需求进行了定制。目标是确保任何熟悉 Go 或对项目新手的开发人员都能快速理解应用程序的布局，并确切知道在哪里查找特定功能。随着我们在后续章节中深入探讨使用 Go 进行 Web 应用程序开发的复杂性，此结构将成为我们的指南地图，确保每段代码都能找到其逻辑归属。

# 包管理和 Vendoring

无论编程环境如何，都会使用包或库来增强核心语言的功能。这使开发人员能够使用已经编写好的代码。以有条理的方式导入、管理和使用这些外部包的过程，就是所谓的包管理的本质。在 Go 编程语言中，这指的是添加、更新或删除这些外部代码片段的过程，以保证与主应用程序的平滑集成。

![](image/image-0-5.jpg)

Fig 2.1 Package Management in Go

## 为什么包管理很重要？

在现代软件开发中，包管理是一个基本组成部分。它能够确保所有开发人员环境的一致性，隔离项目依赖项，并得益于其功能实现可重复构建。这些功能为软件项目在其整个生命周期中提供可扩展性和可维护性的基本基础。

### 环境间的一致性

包管理器允许项目中的所有开发人员使用完全相同版本的外部库和模块。这种一致性消除了当一些工程师使用更新的包而其他人使用旧版本时可能出现的错误和问题。包管理器在包含的项目上下文中安装依赖项，确保每个人都围绕一组统一的包协调一致。

### 与全局状态隔离

包管理器通过在封装的项目上下文中安装包而不是全局安装，从而实现依赖项隔离。这允许明确定义项目的依赖项，与系统上全局安装的任何包分开。隔离性增强了可移植性，并使项目能够在不同目标环境中统一运行。

### 可重复且可靠的构建

通过在构建过程中使用固定且一致的依赖项版本，包管理器能够实现可靠的可重复构建。自动化构建将集成项目清单文件中定义的完全相同的依赖项。这种可重复性在持续交付管道中提供了巨大的信心。构建工件可以在不同环境中完全相同地重新创建。可重复构建还通过消除对底层包的不确定性，极大地帮助调试。

## Vendoring 的需求

在 Go 编程语言中，将所有外部依赖项复制到项目目录中的过程称为“vendoring”。在引入 Go Modules 之前，实现可重复构建的推荐方法是使用 vendoring。使用 vendoring 时，与项目关联的外部包通常保存在项目目录中名为 `/vendor` 的目录中。`/vendor` 目录中的包在应用程序构建过程中，比全局 GOPATH 目录中的包具有更高的优先级。

![](image/image-0-6.jpg)

Fig 2.2 Vendoring in Go

## Vendoring 的优点

*   您的项目与系统范围的包隔离，确保全局空间中的更新或删除不会影响您的项目。
*   由于所有依赖项都是本地的，您可以在没有互联网访问的情况下构建项目。
*   您的依赖项不会更改，除非您明确决定更新它们，从而实现可重复构建。

