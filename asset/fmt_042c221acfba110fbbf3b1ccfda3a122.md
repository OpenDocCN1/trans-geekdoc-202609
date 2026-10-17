
在前面的代码示例中，我们使用 `sizedwaitgroup` 包中的 `New` 函数设置了一个“特殊的 `WaitGroup`”，该函数接受最大 goroutine 数量作为数值参数。之后，我们使用一个遍历 0-99 的 for 循环。然后，像普通的 `WaitGroup` 一样，我们使用 `Add()` 函数声明 goroutine 启动。

在 goroutine 内部，我们执行 `logic` 函数，该函数打印数字并休眠一秒，然后使用 `Done()` 函数表示 goroutine 完成了工作。最终结果是输出会每次以 5 个元素为一批打印所有数字，并在每批之间等待一秒。

### 安全

在本章中，我们将简要讨论围绕服务的安全性 —— 主要从开发者的角度出发，即认证和授权。部署安全的服务到生产环境以防止恶意威胁的访问至关重要 —— 但我们不会探讨作为运维一部分所需采取的安全措施。这主要是因为这是运维的责任，而非开发者。

在任何微服务系统中，我们都希望保证仅系统用户能够访问。

此外，每个用户通常都有特定且不同的访问限制。要实现这两点，我们必须实施认证和授权。

#### 认证

> “认证验证你就是你声称的那个人，或者你拥有的东西不是伪造品。它可能涉及验证文件、要求你提供输入，或两者兼有。”

这是来自 Okta 的一句很好地描述了认证的引言。

在 Web 应用程序中实现认证有多种选择，范围从使用第三方服务到自行实现认证服务。以下是一些示例：

##### 第三方服务

*   **Auth0**：Auth0 提供认证和授权即服务。
*   **Firebase Authentication**：Firebase 提供一套用于构建 Web 和移动应用程序的服务，包括认证。

##### 自行实现的认证

*   **JWT（即 JSON Web Token）**：我们可以使用 JWT 实现认证。JWT 是包含一组声明的编码令牌，可用于认证用户。
*   **基于会话的认证**：我们可以使用会话和 Cookie 实现认证。当用户登录时，会在服务器上创建一个会话，会话 ID 存储在客户端的 Cookie 中。后续请求包含会话 ID，服务器用它来认证用户。

##### 库/框架

*   **Passport.js**：Passport.js 是 Node.js 流行的认证中间件。
*   **Spring Security**：Spring Security 是一个强大且高度可定制的认证和访问控制框架，用于 Java 应用程序。

#### 授权

> “在系统安全中，授权是给予用户访问特定资源或功能权限的过程。该术语常与访问控制或客户端特权互换使用。” —— 另一句来自 Okta 的引言描述了授权。

与认证不同，授权过程要求我们实现业务逻辑。只有当我们了解系统的资源和功能时，产品团队才会定义用户权限的样子。在微服务架构中，系统中的每个服务都必须在拥有授权系统时强制执行用户权限。

问题在于我们不想为每个服务实现单独的授权系统。通常，授权逻辑在整个系统中是相似的，我们希望利用这一点来创建一个中央授权服务或包含授权逻辑的共享代码。无论我们使用外部授权服务还是仅仅共享代码，我们都会使用中间件将用户权限注入到单个服务的上下文中。

正如我们在 *第 7 章，构建 RESTful API* 中提到的许多其他能力一样，中间件可以根据需要使用共享代码或集中式授权服务。我们需要通过代码手动强制执行用户权限，或在数据库层面更自动地执行。以下是使用授权的用例：

*   仅授予账户管理员访问端点 `POST /users` 的权限。
*   授予所有用户访问端点 `GET /views` 的权限，仅授予管理员和经理访问 `UPDATE /views` 的权限，仅授予管理员访问 `DELETE /views` 的权限。

#### 功能开关

在部署服务到生产环境时获得信心的另一种方法是使用功能开关。功能开关允许我们在服务中使用标志（所谓的功能标志）。标志是动态值，通常是布尔值，在服务运行时从其他服务注入。标志可以针对不同用户具有不同的配置。标志可用于多种目的：测试新功能、A/B 测试、负载测试、因客户要求仅向特定用户开放功能等。

以下是一些标志示例：

*   一个名为 `show-billing-tab-ui` 的布尔标志决定名为 `billing` 的 UI 标签页是否打开。我们可以仅向公司内部的产品经理展示该功能（`billing` 标签页），以便他们在向所有客户发布前进行批准或完善。
*   一个名为 `pagination-size` 的数值标志决定 API 的分页大小，可用于测试最佳性能的最优分页大小。

```
func main() {
    if getEnvBool("feature-a", false) {
        fmt.Println("Feature A is enabled. Performing Feature A logic.")
        // Include Feature A logic here
    } else {
        fmt.Println("Feature A is not enabled.")
    }

    if getEnvBool("feature-b", false) {
        fmt.Println("Feature B is enabled. Performing Feature B logic.")
        // Include Feature B logic here
    } else {
        fmt.Println("Feature B is not enabled.")
    }

    // Rest of the application logic
}

func getEnvBool(flagName string, defaultValue bool) bool {
    value, exists := os.LookupEnv(flagName)
    if !exists {
        return defaultValue
    }
    result, err := strconv.ParseBool(value)
    if err != nil {
        fmt.Printf("Error parsing environment variable %s: %v\n", flagName, err)
        return defaultValue
    }
    return result
}
```

这是一个 Golang 中功能开关的示例。在示例中，我们有两个布尔标志 —— `feature-a` 和 `feature-b`。函数 `getEnvBool` 使用环境变量动态检查标志的值。同样的检查也可以通过向第三方服务发起 API 请求来完成。在 `main` 函数中，我们请求标志的值，然后决定是否执行业务逻辑。

我们可以自行创建功能开关外部服务，或者更推荐使用广泛采用的 SaaS，如 LaunchDarkly。

#### 发布

在将应用程序和服务部署到生产环境时，在旧版本和新版本之间切换的摩擦点称为发布。有多种执行发布的技术，所有这些技术都可以通过使用 Kubernetes 的原生工具或适用于 Kubernetes 的外部软件来实现。让我们观察一下不同的技术。

#### 基础部署

这是执行发布最直接的方式。它会立即终止所有先前的实例（Pod），并使用新版本创建新实例（Pod）。这种技术是执行发布最快且最具成本效益的方式，尽管它极易遭遇停机，风险最高。在 Kubernetes 中，我们可以通过定义 `.spec.strategy.type==Recreate` 将此技术指定给工作负载。

##### 滚动更新

滚动更新允许逐步推出新版本。我们控制旧版本和新版本之间的过渡剂量。滚动更新会启动新版本的新实例（Pod），并在终止旧版本之前将流量转移给它们。

![](img/Figure-9.6.jpg)

**图 9.6：** 滚动部署

要在 Kubernetes 中实现这种类型的发布，我们需要指定以下配置：`.spec.strategy.type==RollingUpdate`。Kubernetes 支持在执行滚动更新时可调整的事项包括：

*   **最大不可用数**：发布期间不可用的最大 Pod 数量。它可以是一个绝对数字（例如 5）或一个百分比（70%）。
*   **最大激增数**：可以在工作负载中定义的期望 Pod 数量之上创建的最大 Pod 数量。与前一个配置类似，它可以是一个绝对数字或百分比。

##### 蓝绿部署

这是最安全的发布技术，允许创建具有所有实例（Pod）的期望新版本。通过人工决策，开发人员可以选择将网络路由到旧版本（下图中的蓝色）或新版本（下图中的绿色）。

![](img/Figure-9.7.jpg)

**图 9.7：** 蓝绿部署

Kubernetes 中没有运行蓝绿部署的内置解决方案。但是，有像 `ArgoCD` 这样的工具允许我们这样做。一般来说，蓝绿部署指的是创建所有期望的软件（甚至整个系统），然后决定将所有网络流量路由到哪个版本。虽然它是执行发布最安全的方式，但它是最不具成本效益的技术，且耗时最长。

##### 多服务发布

这种发布技术是指从系统的角度进行发布，而不是从单个服务的角度。使用多服务发布，我们希望将多个服务作为一个整体单元一起发布。我们可以使用之前提到的任何技术来执行多服务发布。Kubernetes 不提供执行此技术的内置能力。然而，`Helm` 是市场上最流行的 Kubernetes 原生开源工具之一，它可以非常快速地实现这一点。`Helm` 是一个用于管理 Chart 的 Kubernetes 开源模板引擎，可以聚合多个 Kubernetes 资源并一次性发布它们。

##### 金丝雀部署

金丝雀部署是滚动更新和蓝绿部署的结合。这种技术允许我们像滚动更新技术一样执行逐步发布，同时将流量路由到旧版本和新版本两者。像蓝绿部署一样，金丝雀部署允许我们观察这两个版本，并手动决定是将所有流量路由到新版本，还是继续将流量路由到先前版本。与蓝绿部署一样，它在 Kubernetes 中没有内置解决方案，我们可以使用 `ArgoCD` 等外部工具。

##### 回滚

新版本往往不如预期，可能会导致多个问题和故障。在这种情况下，我们希望执行回滚。回滚是将系统或应用程序恢复到先前状态或版本。在 Kubernetes 中，有两种执行回滚的方法：

*   **Kubectl**：Kubernetes 中的每个资源都有一个修订版本，每次我们发布新版本时，都会创建一个新的修订版本。以下是如何使用 `kubectl` 执行回滚的示例：

    ```
    kubectl rollout undo <kind>/<resource-name> --to-revision=<revision-number>
    kubectl rollout undo deployment/nginx-deployment --to-revision=2
    ```

*   **Helm**：Helm 中的每个 Chart 都有修订版本，因为它是 Kubernetes 中的一种资源。以下是如何使用 Helm 执行回滚的示例：

    ```
    helm rollback <RELEASE> [REVISION] [flags]
    helm rollback frontend-services 13
    ```

### 结论

在本章中，我们探讨了为将应用程序和服务部署到生产环境做准备所需的关键步骤。从最初的代码完成到确保服务具备生产就绪性，我们涵盖了各种主题，包括 CI/CD、面向失败的设计、超时、重试、回退机制，以及身份认证和授权等安全措施。

我们深入研究了各种部署策略，如基本部署、滚动更新、蓝绿部署、金丝雀部署和多服务发布，每种策略都有其自身的优势和注意事项。此外，我们还讨论了功能开关作为逐步引入新功能的一种技术的重要性，以及在发生意外问题时回滚到先前稳定版本的回滚概念。

通过实际示例，特别是在 Golang 的背景下，我们演示了如何有效地实现这些技术。通过理解和应用这些概念，开发人员可以确保他们的服务按预期交付到生产环境，并在面对潜在故障时保持其完整性和可靠性。

在本章结束时，很明显，将应用程序部署到生产环境是一个多方面的过程，需要仔细的规划和执行。通过遵循最佳实践并利用所讨论的工具和技术，开发人员可以自信地驾驭生产部署的复杂性，并确保其服务在现实世界中取得成功。

在 *第 10 章，生产环境中的后续步骤* 中，我们将介绍应用程序和服务已在生产环境中运行时需要考虑的事项。

### 参考资料

*   [`www.mabl.com/blog/what-is-cicd`](https://www.mabl.com/blog/what-is-cicd)
*   [`github.com/sony/gobreaker`](https://github.com/sony/gobreaker)
*   [`aws.amazon.com/blogs/containers/building-a-fault-tolerant-architecture-with-a-bulkhead-pattern-on-aws-app-mesh/`](https://aws.amazon.com/blogs/containers/building-a-fault-tolerant-architecture-with-a-bulkhead-pattern-on-aws-app-mesh/)
*   [`github.com/remeh/sizedwaitgroup`](https://github.com/remeh/sizedwaitgroup)
*   [`www.okta.com/identity-101/authentication/`](https://www.okta.com/identity-101/authentication/)
*   [`www.okta.com/identity-101/authentication-vs-authorization/`](https://www.okta.com/identity-101/authentication-vs-authorization/)
*   [`launchdarkly.com`](https://launchdarkly.com)
*   [`codefresh.io/learn/software-deployment/`](https://codefresh.io/learn/software-deployment/)
*   [`kubernetes.io/docs/concepts/workloads/controllers/deployment/#rolling-update-deployment`](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#rolling-update-deployment)
*   [`argo-cd.readthedocs.io/en/stable/`](https://argo-cd.readthedocs.io/en/stable/)
*   [`github.com/helm/helm`](https://github.com/helm/helm)

## 第 10 章：生产环境中的后续步骤

### 简介

### 生产维护

本章将重点关注我们的服务在生产环境中运行时必须考虑的各个方面。一个当前稳定且运行在生产环境中的服务，并不意味着它将持续正确运行。无人维护的生产服务就像被忽视的花园 —— 会随时间枯萎。许多事情正在我们不知不觉中发生 —— 发现新漏洞、新客户带来我们未曾经历的新场景、扩缩容效应，等等。维护是韧性的生命线！

维护不仅包含代码中的 Bug 和问题。它还包含文化。良好的文化能在不指责特定个人的前提下更快地解决问题。

维护包括观察系统并通过遥测监控正在发生的事情。遥测数据可以是日志、指标和追踪。我们应致力于实现可观测性，这将使我们能够掌控系统。当我们观察到问题或 Bug 时，我们会想要解决它并寻找解决方案 —— 故障排查。本章将深入探讨故障排查流程及其包含的内容。

在使用微服务系统时，分布式维护的力量至关重要，没有它，微服务架构的威力将大打折扣。

#### 结构

在本章中，我们将讨论以下主题：

*   监控
*   可观测性
    *   日志
    *   指标
    *   追踪
*   生产故障排查
    *   理论的力量
*   性能分析
    *   PGO
    *   性能问题
*   告警
    *   性能指标

#### 监控

监控使利益相关者能够深入了解远程环境（如生产环境或预发布环境）的工作原理。它是持续观察、收集和分析系统性能、健康状况和行为数据的过程。这确保系统运行良好且符合预期。

监控**持续观察**并分析应用程序、基础设施和服务的性能、健康状况和可用性，以检测并响应实时问题，确保最佳运行。它涉及收集指标、日志和其他数据，以洞察系统行为并识别潜在问题或改进点。

监控帮助我们检测系统和服务中的趋势与异常。通过为我们关心的数据设置预定义的阈值和条件，我们可以基于监控定义告警或通知。

通常，我们可以通过仪表盘查看监控输出，以了解正在发生的事情。

![](img/Figure-10.1.jpg)

**图 10.1：** 监控仪表盘示例

上图展示了一个监控仪表盘示例。

监控和 APM 是经常互换使用的概念。APM 代表应用性能监控，是监控的一个子集，用于跟踪特定应用程序的性能。APM 跟踪应用程序是否稳定可用，以及错误率、延迟等。监控是一个更广泛的主题，可以描述性能以外的事物，如趋势、付费客户数量、地理规格数据、SLO（服务等级目标）等。市场上知名的监控工具示例包括 `Prometheus`、`DataDog` 和 `NewRelic`。

### 可观测性

可观测性是衡量系统当前状态并将所有数据聚合为历史视图的能力。可观测性使用三种类型的遥测数据 —— 日志、指标和追踪。这也是它们被引入的历史顺序。

我们可以将可观测性视为一种系统属性，类似于功能性或可测试性。
