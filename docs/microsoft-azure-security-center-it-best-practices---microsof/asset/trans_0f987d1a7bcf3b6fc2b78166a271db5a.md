

## 通过 API 安全警报

尽管 Azure Security Center 有它自己的仪表板，你可以在其中查看所有的安全警报，但在某些特定场景，你可能希望通过 API 消费警报。这对于想要构建自己的仪表板并程序化操作所有警报的组织来说是一个常见场景。

在本章中，你将学习如何利用内置的 Security Center 表述状态转移（REST）API 和 Microsoft Graph Security API，使用 HTTP 请求来检索警报。

## 理解 REST API

表述状态转移（REST）API 是服务端点，支持一组 HTTP 操作（方法），这些方法为服务的资源提供了创建、检索、更新或删除的访问能力。一个 REST API 请求/响应对可以分为五个部分——三个用于请求，两个用于响应——如图 10-1 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_198_0.png)

请求的第一部分是请求 URI，它是主地址。该地址包含以下部分：

结构：(URI-scheme)://{URI-host}/{resource-path}?{query-string}
示例：https://management.azure.com/subscriptions/XXX/providers/Microsoft.Security/alerts/api-version=2019-01-01

第二部分是 HTTP 请求头，它由请求 HTTP 方法组成，例如 GET、HEAD、PUT、POST。此外，你可能还有其他可选标头，例如身份验证。第三部分是可选的，它可以包含根据所用方法而异的补充信息。例如，POST 方法可以包含 MIME 编码的对象，这意味着你还需要指定 Content-type 请求头。

响应的第一部分是 HTTP 状态码，它也可能根据后端如何响应此请求而变化。如果一切运行正常且这是一个成功的请求，你应该收到收到 HTTP 200 状态码。此外，第二个字段是可选的，它的存在是为了支持主响应，就像之前的 MIME 编码示例一样。

## 使用 Security Center REST API 访问警报

Security Center 有它自己的一组 REST API，分为不同的操作组。以下是可用组的描述：

- Alerts（警报）：这些是订阅级别的安全警报。
- Auto Provisioning Settings（自动配置设置）：这些允许你为订阅指定配置配置。
- Compliances（合规性）：检索订阅的法规合规性信息。
- Discovered Security Solutions（已发现的安全解决方案）：检索有关已发现的安全解决方案。
- External Security Solutions（外部安全解决方案）：检索当前与 Security Center 集成的合作伙伴解决方案的详情。
- JIT Network Access Policies（JIT 网络访问策略）：检索使用即时 (JIT) 虚拟机访问来保护资源的策略。
- Locations（位置）：检索特定位置的详情。
- Operations（操作）：检索所有可用操作。
- Pricings（定价）：检索 Security Center 正在使用的定价层级。
- Security Contacts（安全联系人）：这允许你配置订阅的安全联系人信息。
- Tasks（任务）：允许你查看脚本的可视化 Security Center 建议。
- Workspace Settings（工作空间设置）：允许你配置与工作空间相关的设置。

如你所见，可以通过 API 执行很多操作；本章仅关注警报。通过 REST API 调用的 Alert 有许多可以执行的操作，包括获取与资源组或订阅关联的警报。要列出与资源关联的所有警报，可以使用以下示例：
https://management.azure.com/subscriptions/{subscriptionId}/providers/Microsoft.Security/alerts?api-version=2019-01-01

此 HTTP GET 的响应应该是一个 HTTP 200 Header，随后是 JSON 格式的正文，如列表 10-1 所示。

## 列表 10-1 HTTP GET 请求的响应

```json
{
  "value": [
    {
      "id": "/subscriptions/f5bcb5bd4-93d5-4cd0-913b-b4a7ecb1a70/resourceGroups/contososc/microsoft.security/locations/central/alerts/251849388370938726_1d69063a-54f4-4771-9b96-ccfac1cddd35",
      "name": "251849388370938726_1d69063a-54f4-4771-9b96-ccfac1cddd35",
      "type": "Microsoft.Security/Locations/alerts",
      "properties": {
        "systemSource": "Azure",
        "vendorName": "Microsoft",
        "alertDisplayName": "检测到异常 PowerShell 活动",
        "alertName": "SCBA_PSINSIGHT",
        "detectedUtc": "2019-03-18T12:34:52.0616732",
        "description": "对运行在 %(Compromised Host) 上的 脚本检测的主机数据分析显示与已知异常脚本具有共同特征。该脚本可能是合法活动，也可能是主机被入侵的迹象。",
        "remediationSteps": "与 {User Name} 审核此警报中的可疑脚本，以查看是否为合法活动。如果不是，请将警报升级到安全团队。",
        "actionTaken": "Undefined",
        "reportedSeverity": "High",
        "compromisedEntity": "w012READYO",
        "associatedResource": "/subscriptions/{subscriptionId}/resourcegroups/contososc/providers/microsoft.compute/virtualmachines/w012READYO",
        "subscriptionId": "XXXX",
        "instanceId": "XXXX",
        "extendedProperties": {
          "compromisedHost": "w012READYO",
          "userName": "yuri",
          "accountId": "0x871a4aa",
          "suspiciousProcess": "c:\\windows\\system32\\powershell\\v1.0*"
        }
      },
      "exe": "powershell -nop exec -encodedcommand cvahazqbyhmaaaabagawacaoywbag0ubqbhqag4azaagaciajagagahsaiabpbhcacgagaggagadab00ahwaacw6al1wkag8adduwbaagdwhabagqlgbkahzahacwbbpag4adabliabiahghwagwcauagmawwbtac8azbgpagwazqbzc8aw5hbagvbqag41gbqqaacaac0atwlbahqrgbpagwazqwagmaogbnwcahazqtbtaaxabahyahwoaq8awbcoc0acqb24iapplabqiaw",
      "reportedUtc": "2019-03-18T12:34:52.0616273Z",
      "state": "Active",
      "confidenceScore": 0.494,
      "resourceId": "/subscriptions/XXXX",
      "resourceType": "Virtual Machine",
      "canBeInvestigated": true,
      "isIncident": false,
      "suspiciousProcess": "powershell.exe",
      "command": -encodedcommand cvahazqbyhmaaaabagawacaoywbag0ubqbhqag4azaagaciajagagahsaiabpbhcacgagaggagadab00ahwaacw6al1wkag8adduwbaagdwhabagqlgbkahzahacwbbpag4adabliabiahghwagwcauagmawwbtac8azbgpagwazqbzc8aw5hbagvbqag41gbqqaacaac0atwlbahqrgbpagwazqwagmaogbnwcahazqtbtaaxabahyahwoaq8awbcoc0acqb24iapplabqiaw",
      "suspiciousScript": "powershell -command { iwr https://download.sysinternals.com/files/Sysmon.zip -OutFile c:\\sv.exe }",
      "confidenceReasons": [
        {
          "type": "Process",
          "reason": "powershell.exe triggered this alert"
        },
        {
          "type": "Computer",
          "reason": "This alert triggered multiple times in the last 24 hours"
        },
        {
          "type": "User",
          "reason": "User was involved in multiple alerts in the last 7 days"
        }
      ],
      "entities": [
        {
          "type": "host",
          "id": "centralus_1",
          "hostName": "w012READYO",
          "netBiosName": "w012READYO",
          "osFamily": "Windows",
          "osVersion": "Windows",
          "isJoined": false
        },
        {
          "type": "process",
          "id": "centralus_2",
          "commandLine": ""
        },
        {
          "type": "account",
          "id": "centralus_3",
          "name": "yuri",
          "ntDomain": "w012READYO",
          "sid": "S-1-21-43177023320-132450192-196-3277483117-500",
          "isJoined": false,
          "LogonId": "0x871a4"
        },
        {
          "type": "file",
          "id": "centralus_4",
          "directory": "c:\\windows\\system32\\powershell\\v1.0",
          "name": "powershell.exe"
        }
      ]
    }
  ]
}
```

使用 Security Center REST API 访问警报 第10章 183

