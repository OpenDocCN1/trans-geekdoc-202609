
![Tip](images/tip.png)您可以通过阅读 Azure 文档文章“Azure Policy 定义结构”来了解有关 Azure Policy JSON 语法的更多信息，网址为 [`https://docs.microsoft.com/en-us/azure/governance/policy/concepts/definition-structure`](https://docs.microsoft.com/en-us/azure/governance/policy/concepts/definition-structure)。

在策略部署时，您需要为 `listOfAllowedLocations` 参数指定一个值。`strongType` 元素是一项 ARM 魔法，它会创建一个包含所有 Azure 区域的下拉列表。这是一个在 ARM 模板和策略定义中使用的实用技巧。

请回想一下，Azure 资源管理器 (ARM) 是支撑您在 Azure 中执行的任何和所有操作的 API。

作为替代方案，您可以通过替换 `allowedValues` 数组来创建允许值的枚举：

```
"allowedValues": [ "EastUS", "EastUS2", "CentralUS" ]
```

策略的核心是条件语句。下一个代码块使用了一个包含一个或多个约束的 `if` 块。在本示例中，所有条件必须评估为 `true`，策略才会生效。策略评估部署中指定的位置。如果目标位置不在允许的位置列表中，则策略会拒绝该部署。

```
{ "if": { "allOf": [ { "field": "location", "notIn": "[parameters('listOfAllowedLocations')]" } ] }, "then": { "effect": "Deny" }}
```

策略包含多种不同的策略效果。在 Azure Policy 中，效果决定了如果给定策略评估为 true，Azure 将执行什么操作。

使用审核效果，您可以允许部署，但为了审核目的对其进行密切跟踪。DeployIfNotExists 效果非常强大，因为策略可以执行 ARM 模板部署来强制实施策略。例如，您可以设置一个策略，如果同事在资源上意外或故意关闭了资源诊断，则自动重新启用它。

![Tip](images/tip.png)如果您想深入了解 Policy，请参阅“了解 Azure Policy 效果”，网址为 [`https://docs.microsoft.com/en-us/azure/governance/policy/concepts/effects`](https://docs.microsoft.com/en-us/azure/governance/policy/concepts/effects)。

## 策略生命周期

部署策略分为三个阶段：

*   **创作：** 通常，您需要复制现有的策略定义，将其附加到管理范围，并对其进行编辑以满足您的要求。
*   **分配：** 您将策略链接到管理范围。
*   **合规性：** 您查看并报告 Azure 资源的合规性，并根据需要采取创作、分配和修正纠正措施。

在 Policy 中，*计划* 是一个与一个或多个单独的策略定义关联的容器对象。计划的用例是希望将多个相关的策略分配作为单个实体进行管理的企业。然而，本章重点介绍单个策略。

### 创建策略

您可以定义一个链接到订阅范围的策略，以限制管理员可以向其部署资源的区域。请在 Azure 门户中执行以下步骤：

1.  **浏览到“策略”边栏选项卡，然后选择“设置”⇒“定义”。**
2.  **在“策略 - 定义”边栏选项卡的搜索框中键入** `location` **。**

    您会在键入时看到搜索词的结果列表。花点时间浏览结果列表。我在[图 12-4](#c12.xhtml#c12-fig-0004) 中向您展示此界面。

    ![图 12-4：浏览内置 Azure Policy 定义。](images/9781119612148-fg1204.png)

    [图 12-4：](#c12.xhtml#rc12-fig-0004) 浏览内置 Azure Policy 定义。

3.  **选择“允许的位置”内置策略定义，然后从工具栏单击“复制定义”。**

    策略定义随即出现。内置模板是只读的，因此您需要复制它才能使其成为您自己的定义。

4.  **完成新的策略定义。**

    以下是关于属性的一些指导：

    *   *定义位置：* 选项为管理组和订阅。我建议您选择您的订阅。
    *   *名称：* 根据您的企业 Azure 命名约定，使策略名称具有意义。
    *   *类别：* 将策略存储在内置类别中或创建您自己的类别。

5.  **编辑策略规则以删除以下行：**

    ```
    { "field": "location", "notEquals": "global" }, { "field": "type", "notEquals": "Microsoft.AzureActiveDirectory/b2cDirectories" }
    ```

    严格来说，您唯一需要的策略条件是引用 `listOfAllowedLocations` 参数值的那个条件。

6.  **单击“保存”以提交您的更改。**

![Tip](images/tip.png)Microsoft 的策略工程团队托管了一个 Azure Policy 示例 GitHub 存储库，其中包含涵盖大多数 Azure 服务的数百个策略。这些策略定义应该能让您在管理自己的环境方面抢占先机。您可以在 [`https://github.com/Azure/azure-policy`](https://github.com/Azure/azure-policy) 找到它们。

### 分配策略

创建自定义策略定义后，将其分配给您的订阅并进行测试。请执行以下步骤：

1.  **在“策略 - 定义”边栏选项卡上，从“类型”下拉列表中选择“自定义”。**

    筛选视图以便仅查看您的自定义策略会很有帮助。

2.  **选择您的策略，然后单击工具栏上的“分配”。**

    您也可以从此配置边栏选项卡编辑或删除您的策略定义。

3.  **完成表单。**

    以下是我关于填写表单的建议：

    *   *范围：* 因为您将定义链接到了订阅级别，所以请选择该订阅作为分配范围。您可以进一步将策略范围限制为订阅中的特定资源组。
    *   *排除：* 您可以将资源组和单个资源从策略中豁免。在这种情况下，订阅中可能已存在已获授权位于不允许的区域中的资源。
    *   *分配名称：* 分配名称的显示名称可以与其底层策略定义不同。
    *   *参数：* 在这种情况下，您应该会看到一个填充了 Azure 区域的“允许的位置”下拉列表。选择您想要允许的任何区域。
    *   *创建托管标识：* 仅当您的策略将执行部署时，才需要此选项。Azure Active Directory (AD) 中的托管标识类似于本地 AD 中的服务帐户；请参阅[第 11 章](#c11.xhtml)。

4.  **单击“分配”以提交您的策略。**

![Warning](images/warning.png)打开通知菜单；您可能会看到一条信息性消息，通知您策略分配大约需要 30 分钟才能生效。

如果您浏览到“分配”边栏选项卡，应该会看到您新分配的策略，如[图 12-5](#c12.xhtml#c12-fig-0005) 所示。要获得更清晰的视图，请打开“定义类型”下拉列表并筛选“策略”。

![图 12-5：策略分配列表。](images/9781119612148-fg1205.png)

[图 12-5：](#c12.xhtml#rc12-fig-0005) 策略分配列表。

### 测试策略

要测试策略，请尝试将 Azure 资源部署到不允许的位置。例如，尝试部署一个新的存储帐户；[第 3 章](#c03.xhtml) 介绍了如何执行此操作。

部署应该会失败，如[图 12-6](#c12.xhtml#c12-fig-0006) 所示。

![图 12-6：Azure Policy 阻止了此部署。](images/9781119612148-fg1206.png)

[图 12-6：](#c12.xhtml#rc12-fig-0006) Azure Policy 阻止了此部署。

请注意，Azure 失败文本解释了所需的存储帐户资源被策略禁止，甚至贴心地提醒您是哪个策略起到了保护作用。

# 迁移到 Microsoft Azure 并监视您的基础设施

本部分内容……

将本地环境扩展到 Azure

掌握如何将海量数据从本地网络迁移到 Azure

理解 Azure VPN 与 ExpressRoute 之间的区别
