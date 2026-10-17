
在本示例中，攻击者的网站（[`malicious.h4cker.org/malware.html`](http://malicious.h4cker.org/malware.html)）可能托管恶意软件或恶意脚本，当受害者访问该站点时这些脚本就会执行。

注意
`URL http://malicious.h4cker.org/malware.html` 是一个真实的 URL，但它并不是恶意网站。如果你在网络浏览器中连接它，你将看到与图 6-23 相同的消息。

# 利用不安全的代码实践

以下章节涵盖了攻击者可以利用的以及你可以在渗透测试任务中利用的若干种不安全代码实践。

## 源代码中的注释

开发者经常会在源代码中包含可能提供过多信息且可能被攻击者利用的内容。例如，他们可能会提供有关系统密码、API 凭据或其他攻击者可以发现并使用的敏感信息的详细信息。

注意
MITRE 创建了一个名为“常见弱性枚举”（CWE）的标准。CWE 列出了分配给安全不规范行为或引入漏洞的底层弱性的标识符。`CWE-615`，“通过注释泄露信息”涵盖了本节描述的缺陷。你可以在 [`cwe.mitre.org/data/definitions/615.html`](https://cwe.mitre.org/data/definitions/615.html) 获取关于 `CWE-615` 的详细信息。

### 缺乏错误处理和过度详细的错误处理

不当的错误处理是一种弱性和安全不规范行为，可以向攻击者提供信息，帮助其对目标系统执行额外的攻击。错误代码、数据库转储和堆栈跟踪等错误消息可以为攻击者提供价值信息，例如有关应用程序中可能进一步利用的潜在漏洞的信息。

最佳实践是根据经过深思的方案处理错误消息，为用户提供有意义的错误信息，为开发者和支持人员提供诊断信息，而不向攻击者提供任何有用信息。

提示
OWASP 在 [`owasp.org/www-community/Improper\_Error\_Handling`](https://owasp.org/www-community/Improper_Error_Handling) 提供了不当错误处理的详细示例。OWASP 还提供了一份讨论如何发现和防止错误处理漏洞的速查表，请参 [`cheatsheetseries.owasp.org/cheatsheets/Error\_Handling\_Cheat\_Sheet.html`](https://cheatsheetseries.owasp.org/cheatsheets/Error_Handling_Cheat_Sheet.html)。

## 硬编码凭据

硬编码凭据是致命的缺陷，攻击者可以利用它完全破坏应用程序或底层系统。MITRE 在 `CWE-798` 中涵盖了这种不规范行为（或弱性）。你可以在 [`cwe.mitre.org/data/definitions/798.html`](https://cwe.mitre.org/data/definitions/798.html) 获取关于 `CWE-798` 的详细信息。

## 竞态条件

当系统或应用程序尝试执行两个或多个操作时，就会发生竞态条件。然而，由于此类系统或应用程序的性质，操作必须按照正确的顺序执行才能正确。当攻击者利用此类漏洞时，在安全控制生效和攻击执行之间有一个短暂的时间窗口。竞态条件的攻击复杂度非常高。换句话说，竞态条件非常难利用。

注意
竞态条件也被称为“检查时间到使用时间”（`TOCTOU`）攻击。

竞态条件的一个例子是安全管理系统向安全设备（如防火墙或入侵防御系统）推送配置，导致该过程从系统重建访问控制列表和规则。攻击者可能拥有非常短的时间窗口，可以在这些安全控制在受管理设备上生效之前绕过这些控制。

### 未受保护的 API

应用程序编程接口（API）如今无处不在。许多现代应用程序使用 API 允许其他系统与应用程序交互。遗憾的是，许多 API 缺乏充分的控制且难以监控。API 的广度和复杂性也使得自动进行有效的安全测试变得困难。现代 API 背后有几种方法或技术：

* **简单对象访问协议 (SOAP)：** 这种基于标准的 Web 服务访问协议最初由微软开发，已被许多遗留应用程序使用了多年。SOAP 专门使用 XML 来提供 API 服务。基于 XML 的规范由 XML 架构定义 (XSD) 文档管理。SOAP 最初创建是为了取代更旧的解决方案，如分布式组件模型（DCOM）和通用对象请求代理架构（CORBA）。你可以在 [`www.w3.org/TR/soap`](https://www.w3.org/TR/soap) 获取最新的 SOAP 规范。

* **表述状态转移 (REST)：** 这种 API 标准比 SOAP 更容易使用。它使用 JSON 代替 XML，并使用 Swagger 和 OpenAPI 规范（[`www.openapis.org`](https://www.openapis.org)）等标准以便编写文档并鼓励采用。

* **GraphQL：** GraphQL 是一种用于 API 的查询语言，提供了许多开发者工具。GraphQL 现在被用于许多移动应用程序和在线仪表板。许多不同的语言支持 GraphQL。你可以在 [`graphql.org/code`](https://graphql.org/code) 学习更多关于 GraphQL 的知识。

注意
SOAP 和 REST 使用 HTTP 协议。然而，SOAP 受限于更严格的 API 模式集。作为最佳实践，你应该始终使用超文本传输协议安全（HTTPS），它是 HTTP 的安全版本。

API 通常提供一个描述底层实现的路线图。该路线图可以为渗透测试人员提供他们可能忽略的线索。API 文档可以提供对渗透测试人员非常有价值的细节。API 文档可以包含以下内容：

* **Swagger (OpenAPI)：** Swagger 是一种现代 API 文档和开发框架，是 OpenAPI 规范 (OAS) 的基础。有关 Swagger 的更多信息可以在 [`swagger.io`](https://swagger.io) 获取。OAS 规范位于 [`github.com/OAI/OpenAPI-Specification`](https://github.com/OAI/OpenAPI-Specification)。

* **Web 服务描述语言 (WSDL) 文档：** WSDL 是一种用于文档 Web 服务功能的 XML 语言。WSDL 规范可以在 [`www.w3.org/TR/wsdl20-primer`](https://www.w3.org/TR/wsdl20-primer) 访问。

* **Web 应用描述语言 (WADL) 文档：** WADL 是一种描述 Web 应用程序的 XML 语言。WADL 规范可以从 [`www.w3.org/Submission/wadl`](https://www.w3.org/Submission/wadl) 获取。针对 API 进行渗透测试时，使用 Burp Suite 或 OWASP ZAP 等代理收集完整的请求是重要的。（你将在第 10 章中学习更多关于这些工具的内容。）确保代理能够收集完整的 API 请求而不是 URL，因为 REST、SOAP 和其他 API 服务使用的不仅仅是 `GET` 参数。

在分析收集到的请求时，请寻找非标准参数和异常的 HTTP 请求头。你还应该确定 URL 段落在其他 URL 中是否存在重复的模式。这些模式可能包括数字或 ID、日期以及其他有用信息。检查结果，并寻找 JSON、XML 甚至非标准结构中的结构化参数值。

### 提示

如果你发现某个 URL 段落包含许多值，那可能是因为它是一个参数，而不是 Web 服务器中的文件夹或目录。例如，如果 URL `http://web.h4cker.org/s/*abcd*/page` 带有不同的 `abcd` 值重复出现（例如 [`web.h4cker.org/s/dead/page`](http://web.h4cker.org/s/dead/page) 或 [`web.h4cker.org/s/beef/page`](http://web.h4cker.org/s/beef/page)），那么这些变化的值无疑疑是 API 参数。

你还可以使用模糊测试（fuzzing）来发现 API 漏洞（或任何应用程序或系统的漏洞）。根据 OWASP 的定义，“模糊测试或 Fuzzing 是一种未知环境/黑盒软件测试技术，其基本上是通过自动化的方式注入畸形/半畸形数据来发现实现层面的 Bug。”

### 注意

请参考 OWASP 页面 [`www.owasp.org/index.php/Fuzzing`](https://www.owasp.org/index.php/Fuzzing) 来学习适用于用于协议、应用程序和其他系统的不同类型的模糊测试技术。在 第 10 章中，你将看到一些模糊测试器的示例以及如何使用它们来发现漏洞。

在测试 API 时，你应该始终分析收集到的请求以优化模糊测试。在你找到要进行模糊测试的潜在参数后，确定你想发送到应用程序的有效值和无效值。当然，模糊测试应该关注无效值（例如，发送带有大值或特殊字符、Unicode 等的 `GET` 或 `PUT` 请求）。在 第 10 章中，你将学习到诸如 Radamsa ([`gitlab.com/akihe/radamsa`](https://gitlab.com/akihe/radamsa)) 等工具，这些工具可用于为应用程序、协议等创建模糊测试参数。

### 提示

OWASP 有一份 REST 安全快速备忘录（Security Cheat Sheet），提供了关于如何保护 RESTful (REST) API 的众多最佳实践。请参 [`cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html`](https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html)。

以下是保护 API 的若干通用最佳实践和建议：

* 保护 API 服务，仅提供强 TLS 版本的 HTTPS 端点。
* 在应用程序中验证参数并对来自 API 客户端的输入进行清洗。
* 显式扫描常见的攻击签名；注入攻击通常通过遵循常见模式暴露自己。
* 使用强身份验证和授权标准。
* 使用可靠且标准的库来创建 API。
* 将 API 实现和 API 安全划分到不同的层级；这样做可以使 API 开发人员完全专注于应用程序领域。
* 识别哪些数据应该是公开的，哪些信息是敏感的。
* 如果可能，让安全专家对 API 代码进行验证。
* 强制编写内部 API 文档。
* 避免在公共论坛上讨论公司的 API 开发（或任何其他应用程序开发）。

### 注意

CWE-227，“API 滥用”涵盖了未保护的 API。有关 CWE-227 的详细信息，请参见 [`cwe.mitre.org/data/definitions/227.html`](https://cwe.mitre.org/data/definitions/227.html)。

## 隐藏元素

Web 应用程序参数篡改攻击可以通过操控 Web 客户端与 Web 服务器之间交换的参数来修改应用程序数据。这可以通过操纵 Cookie（在本章前面的部分讨论过）和滥用隐藏表单字段来实现。

可能会篡改 Web 应用程序存储在隐藏表单字段中的值。让我们来看一个隐藏 HTML 表单字段的示例。假设以下内容是一个向在线客户销售商品的电子商务网站的一部分：

```
<input type="hidden" id="123" name="price" value="100.00">
```
