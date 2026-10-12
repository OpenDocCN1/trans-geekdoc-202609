

## 参考链接

- <https://blog.danslimmon.com/2019/05/03/no-observability-without-theory/>
- <https://cloud.google.com/profiler/docs/interacting-flame-graph>
- <https://www.airplane.dev/blog/kubernetes-cpu-limits-and-throttling>
- <https://medium.com/@shivam2003/memory-leak-unveiling-the-dark-side-of-c-the-silent-killer-lurking-in-your-code-e675599add9>

# 索引

## 符号

## A

**API 网关** [101](#c06.xhtml#page101), [102](#c06.xhtml#page102)

**API 网关，功能**

- 可观测性 [102](#c06.xhtml#page102)
- 路由 [102](#c06.xhtml#page102)
- 安全性 [102](#c06.xhtml#page102)

## B

**前端后端（BFF）** [107](#c06.xhtml#page107)

**基准测试** [69](#c04.xhtml#page69)

## C

**`chan` 关键字** [75](#c05.xhtml#page75)

**CI/CD** [154](#c09.xhtml#page154), [155](#c09.xhtml#page155)

**CI/CD，原因**

- 一致性，维护 [155](#c09.xhtml#page155)
- 可扩展性 [155](#c09.xhtml#page155)

## D

**数据访问层（DAL）** [3](#c01.xhtml#page3)

**每服务一个数据库**

- 简介 [106](#c06.xhtml#page106)
- 优势 [106](#c06.xhtml#page106)
- 概念 [106](#c06.xhtml#page106)
- 劣势 [107](#c06.xhtml#page107)

## E

**错误处理**

- 简介 [59](#c04.xhtml#page59), [60](#c04.xhtml#page60)
- 惯例 [61](#c04.xhtml#page61)
- Go，对比 [61](#c04.xhtml#page61)
- 易用性，利用 [61](#c04.xhtml#page61)

**事件驱动架构**

- 简介 [108](#c06.xhtml#page108)
- CQRS [111](#c06.xhtml#page111)
- 事件溯源 [110](#c06.xhtml#page110)
- 用法 [109](#c06.xhtml#page109)
- 对比，消息传递 [109](#c06.xhtml#page109)

**事件驱动架构，缺点**

- 复杂性 [110](#c06.xhtml#page110)
- 数据一致性 [109](#c06.xhtml#page109)
- 重复事件 [110](#c06.xhtml#page110)

**事件驱动架构，优点**

- 解耦服务 [109](#c06.xhtml#page109)
- 可扩展性 [109](#c06.xhtml#page109)

**事件溯源，优势**

- 不变性 [110](#c06.xhtml#page110)
- 可重放性 [110](#c06.xhtml#page110)

## F

**扇入** [95](#c05.xhtml#page95), [96](#c05.xhtml#page96)

**扇出** [93](#c05.xhtml#page93), [95](#c05.xhtml#page95)

**标志**

- 简介 [164](#c09.xhtml#page164)
- 示例 [164](#c09.xhtml#page164)
- 功能 [166](#c09.xhtml#page166)

**`forgottenSender` 函数** [89](#c05.xhtml#page89)

## G

**生成器函数** [96](#c05.xhtml#page96)

**泛型**

- 简介 [53](#c04.xhtml#page53)
- 概念 [53](#c04.xhtml#page53), [54](#c04.xhtml#page54)
- 约束，利用 [54](#c04.xhtml#page54)–[56](#c04.xhtml#page56)

**Go Context，最佳实践** [58](#c04.xhtml#page58)

**Go Context，概念**

- 并发，处理 [56](#c04.xhtml#page56)
- 键值存储，管理 [56](#c04.xhtml#page56)
- 任务，管理 [56](#c04.xhtml#page56)

**Go Context，理解** [56](#c04.xhtml#page56)–[59](#c04.xhtml#page59)

**`GODEBUG`** [24](#c02.xhtml#page24)

**Go 部署，步骤**

- 构建 [28](#c02.xhtml#page28)
- 编写代码 [26](#c02.xhtml#page26)
- 包管理 [26](#c02.xhtml#page26)
- 规划 [26](#c02.xhtml#page26)
- 安全性 [27](#c02.xhtml#page27)
- 语法，掌握 [26](#c02.xhtml#page26)
- 测试 [27](#c02.xhtml#page27)
- 工具，集中化 [28](#c02.xhtml#page28)
- 故障排查 [27](#c02.xhtml#page27)

**Go 快速编译，原因**

- 编译，设计 [20](#c02.xhtml#page20)
- 循环依赖，避免 [20](#c02.xhtml#page20)
- 简洁性 [21](#c02.xhtml#page21)
- 用法，导入 [21](#c02.xhtml#page21)

**Go，函数式模式** [51](#c04.xhtml#page51)–[53](#c04.xhtml#page53)

**Go 可维护性，原因**

- API，检查 [24](#c02.xhtml#page24)
- 兼容性 [24](#c02.xhtml#page24)
- 错误，处理 [25](#c02.xhtml#page25)
- 简洁性 [24](#c02.xhtml#page24)
- 测试 [24](#c02.xhtml#page24)

**Go，包测试** [61](#c04.xhtml#page61)–[64](#c04.xhtml#page64)

**Go 范式，技术**

- 并发，编程 [16](#c02.xhtml#page16)
- 命令式 [15](#c02.xhtml#page15), [16](#c02.xhtml#page16)
- 面向对象编程 [16](#c02.xhtml#page16)

**`gophersource`** [28](#c02.xhtml#page28)

**Go 编程语言**

- 简介 [14](#c02.xhtml#page14)
- 组合，复杂化 [46](#c03.xhtml#page46), [47](#c03.xhtml#page47)
- 接口，分析 [47](#c03.xhtml#page47), [48](#c03.xhtml#page48)
- 发明 [14](#c02.xhtml#page14)
- 多种，方法 [17](#c02.xhtml#page17), [18](#c02.xhtml#page18)
- 开源驱动，分析 [28](#c02.xhtml#page28)
- 包 [42](#c03.xhtml#page42), [43](#c03.xhtml#page43)
- 范式 [15](#c02.xhtml#page15)
- 项目，结构 [44](#c03.xhtml#page44)
- 结构体，初始化 [44](#c03.xhtml#page44)–[46](#c03.xhtml#page46)

**Go 编程语言，特性**

- 并发，方法 [21](#c02.xhtml#page21)–[23](#c02.xhtml#page23)
- 类 C，相似 [21](#c02.xhtml#page21)
- 快速，编译 [19](#c02.xhtml#page19)

**Go 编程语言，原则**

- 高效性 [15](#c02.xhtml#page15)
- 可维护性 [15](#c02.xhtml#page15)
- 简洁性 [15](#c02.xhtml#page15)

**Go 编程语言，属性**

- 静态，类型 [17](#c02.xhtml#page17)
- 强，类型 [17](#c02.xhtml#page17)

**Go 编程语言，风格**

- 数组 [37](#c03.xhtml#page37)
- 注释 [34](#c03.xhtml#page34)
- `const` 关键字 [41](#c03.xhtml#page41), [42](#c03.xhtml#page42)
- 函数 [38](#c03.xhtml#page38), [39](#c03.xhtml#page39)
- Hello World [31](#c03.xhtml#page31)
- If 语句 [35](#c03.xhtml#page35)
- 语言，规范 [42](#c03.xhtml#page42)
- 循环 [36](#c03.xhtml#page36), [37](#c03.xhtml#page37)
- Map [39](#c03.xhtml#page39)
- 运算符 [34](#c03.xhtml#page34)
- 基本数据 [33](#c03.xhtml#page33), [34](#c03.xhtml#page34)
- 切片 [37](#c03.xhtml#page37), [38](#c03.xhtml#page38)
- switch 语句 [41](#c03.xhtml#page41)
- 变量 [32](#c03.xhtml#page32), [33](#c03.xhtml#page33)

**Goroutine**

- 简介 [73](#c05.xhtml#page73), [74](#c05.xhtml#page74)
- 通道关闭，原则 [87](#c05.xhtml#page87), [88](#c05.xhtml#page88)

**Goroutine，缓冲概念**

- 通道，关闭 [77](#c05.xhtml#page77)
- 通道，方向 [79](#c05.xhtml#page79)
- 通道，选择 [78](#c05.xhtml#page78)
- 通道，同步 [79](#c05.xhtml#page79)
- 锁 [82](#c05.xhtml#page82), [83](#c05.xhtml#page83)
- 底层，例程 [84](#c05.xhtml#page84)
- range 语法 [77](#c05.xhtml#page77), [78](#c05.xhtml#page78)
- 单例，求和 [83](#c05.xhtml#page83), [84](#c05.xhtml#page84)
- 优势，利用 [80](#c05.xhtml#page80)
- `sync` 包 [80](#c05.xhtml#page80)
- `WaitGroup` [81](#c05.xhtml#page81), [82](#c05.xhtml#page82)

**Goroutine，情况**

- 泄漏，检测 [93](#c05.xhtml#page93)
- 接收方，放弃 [91](#c05.xhtml#page91), [93](#c05.xhtml#page93)
- 发送方，遗忘 [89](#c05.xhtml#page89)–[91](#c05.xhtml#page91)

**Go 测试，工具**

- Fuzz，测试 [66](#c04.xhtml#page66), [67](#c04.xhtml#page67)
- Mock [64](#c04.xhtml#page64), [65](#c04.xhtml#page65)

## K

**Kubernetes**

- 简介 [140](#c08.xhtml#page140), [141](#c08.xhtml#page141)
- 存活探针，就绪 [147](#c08.xhtml#page147), [148](#c08.xhtml#page148)
- 资源，分配 [149](#c08.xhtml#page149)
- 工作负载，管理 [143](#c08.xhtml#page143)

**Kubernetes，方面**

- `ConfigMap` [146](#c08.xhtml#page146)
- 水平 Pod 自动扩缩 [146](#c08.xhtml#page146)
- Ingress 暴露 [147](#c08.xhtml#page147)
- `Secret` [146](#c08.xhtml#page146)

**Kubernetes，最佳实践**

- 环境，管理 [151](#c08.xhtml#page151)
- 监控 [151](#c08.xhtml#page151)
- 具体地，日志记录 [150](#c08.xhtml#page150)
- YAML 规范，维护 [150](#c08.xhtml#page150)

**Kubernetes，资源**

- `Namespace` [142](#c08.xhtml#page142), [143](#c08.xhtml#page143)
- `Node` [142](#c08.xhtml#page142)
- `Pod` [143](#c08.xhtml#page143)

**Kubernetes，工具**

- `Kind` [141](#c08.xhtml#page141)
- `Kubectl` [141](#c08.xhtml#page141), [142](#c08.xhtml#page142)
- `kubectx` [142](#c08.xhtml#page142)

