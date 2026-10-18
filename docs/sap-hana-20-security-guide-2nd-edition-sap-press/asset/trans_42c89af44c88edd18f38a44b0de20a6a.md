

# SAP Web IDE for SAP HANA 中 HDI 容器的外部对象访问

如果你正在构建商业智能解决方案，你的表和架构很可能位于非仓库架构或由标准用户账户拥有的架构中。因此，你的 HDI 容器可能需要访问外部对象或其他 HDI 容器。其次，当你部署引用外部对象的 HDI 容器内容时，`#OO` 用户将在运行时需要访问这些外部对象。SAP Web IDE for SAP HANA 提供了解决这两种情况的机制，但开发人员无法完全在 SAP Web IDE for SAP HANA 内完成任何一种机制。因此，你需要详细探索每个选项及其要求。让我们先看看外部目录对象的安全注意事项，然后再看看其他 HDI 容器的注意事项。

## 开发人员在设计时访问外部目录对象

SAP Web IDE for SAP HANA 使用用户提供的服务和服务实例来代理访问外部目录对象或 HDI 容器。此服务是 SAP HANA XSA 架构的一部分，可以在 SAP Web IDE for SAP HANA 或 SAP HANA XSA 驾驶舱中创建。你也可以使用 SAP HANA XSA 驾驶舱在创建后管理该服务。服务实际上是一段代码片段，它提供了到 SAP HANA 数据库的 Java Database Connectivity (JDBC) 访问桥。该代码片段采用 JSON 格式，如 [Figure 18.15](#18_004.html#f18.15) 中的示例所示。

[![Example Definition of a User-Provided Service within the SAP HANA XSA Cockpit GUI](bilderklein/klein18_015.png)](img-f18.15.html)

**Figure 18.15** SAP HANA XSA 驾驶舱 GUI 中用户提供的服务定义示例

定义并与你的 HDI 容器 `di-builder` 关联后，你可以配置项目以使用此服务。但是，SAP Web IDE for SAP HANA 还有一个工作流可帮助你创建服务，我们将在本节中引导你完成此过程。

在构建服务之前，让我们先讨论服务用户所需的安全性。服务桥提供两个功能。首先，在设计时，搜索外部目录对象时可以选择该服务。例如，在创建同义词或 SAP HANA 计算视图时，你可能需要使用此服务搜索外部对象。其次，如果你使用 `.hdbgrants` 文件向 `#OO` 用户授予权限，此服务桥将向 `#OO` 用户授予权限。因此，使用 `.hdbgrants` 时，服务用户必须为两种场景（包括 `WITH GRANT OPTION`）拥有所需的权限。一旦在 `.hdbgrants` 项目文件中引用，此服务用户也将成为项目的永久组件。安全团队必须仔细设计 SAP HANA 数据库上的服务账户用户，并确保该账户仅拥有支持应用程序所需的权限。

现在，让我们看看如何使用 SAP Web IDE for SAP HANA GUI 创建用户提供的服务。在开始此步骤之前，请确保你的项目已分配空间和 `di-builder`。在你的 SAP Web IDE for SAP HANA 项目中，右键单击 `db` 文件夹并选择 New • SAP HANA Service Connection，如 [Figure 18.16](#18_004.html#f18.16) 所示。

[![Creating an SAP HANA Service Connection](bilderklein/klein18_016.png)](img-f18.16.html)

**Figure 18.16** 创建 SAP HANA 服务连接

将出现 Add External SAP HANA Service 窗口。输入 SAP HANA 数据库的详细信息，如 [Figure 18.17](#18_004.html#f18.17) 所示，包括连接信息和本地数据库中用户的凭据。

[![Defining the Service Connection](bilderklein/klein18_017.png)](img-f18.17.html)

**Figure 18.17** 定义服务连接

单击 OK 继续。该服务现在可用于帮助你搜索 HDI 容器外部的外部对象。例如，在创建同义词时，你可以连接到服务并在 GUI 中搜索对象。同样，从安全角度来看，只有服务拥有 SELECT 访问权限的对象才会显示。如果你担心开发人员拥有服务用户的凭据，开发人员不必创建此服务。安全管理员和 SAP HANA XSA 管理员可以使用 SAP HANA XSA 驾驶舱定义服务。然后，开发人员可以更新 `mta.yaml` 文件并引用该服务。例如，你可以随时使用 `mta.yaml` GUI 编辑器创建或更改服务值。

[Figure 18.18](#18_004.html#f18.18) 显示了使用 `mta.yml` GUI 编辑此值的示例。你将在项目的工作区中找到 `mta.yaml` 文件。默认情况下，打开该文件将启动 GUI 编辑器。选择 Resources 选项，然后选择 `cross-container-servcie-1` 以显示 `service-name` 属性。将值更改为与用户定义的服务的值匹配。请注意，更改此值可能会影响项目中任何现有的 `.hdbgrants` 文件，因为 `.hdbgrants` 文件引用服务以在运行时向 `#OO` 用户授予访问权限。

[![Changing the Service-Name Associated with Our MTA Project within the mta.yaml File](bilderklein/klein18_018.png)](img-f18.18.html)

**Figure 18.18** 在 `mta.yaml` 文件中更改与我们的 MTA 项目关联的服务名称

## 开发人员访问其他 HDI 容器

我们将使用类似的过程来提供对另一个 HDI 容器的设计时访问。在定义 SAP HANA 服务连接时，选择 HDI Container 选项，然后选择现有的 HDI 容器。列表将仅显示已完全构建并部署到数据库并在 SAP HANA XSA 中具有服务实例的 HDI 容器。将在 `mta.yaml` 文件中定义一个新服务，该服务在 GUI 中定义计算视图和同义词时也可选择。请注意，在引用对象构建之前，你需要授予本地项目 `#OO` 用户对远程容器的访问权限。在下一节中，我们将解释如何使用 `.hdbgrants` 文件和 HDI 角色来授予必要的访问权限。

## `#OO` 服务用户在运行时访问对象

在完全部署或构建项目中的内容文件之前，容器的 `#OO` 用户必须能够访问其引用的远程内容。远程内容包括经典 SAP HANA 数据库对象以及其他 HDI 容器。你可以通过三种方式创建此访问权限。让我们看看给定场景可用的每个选项：

*   当需要访问经典 SAP HANA 数据库中的外部对象时，安全团队可以直接授予权限。简而言之，他们可以使用 SQL 控制台或 SAP HANA 驾驶舱向 `#OO` 用户授予对外部目录对象的访问权限。此步骤可以独立于开发人员和 SAP Web IDE for SAP HANA 工件完成。此选项更安全，因为开发人员不需要访问可以授予权限的用户提供的服务。

*   安全管理员可以在数据库中创建标准角色，然后使用开发人员定义的 `.hdbgrants` 文件将这些角色授予 `#OO` 用户。在这种情况下，用户提供的服务需要能够根据 `.hdbgrants` 文件中的信息将这些角色授予 `#OO` 账户。服务用户是授予这些角色给 `#OO` 账户的用户。此方法可能不太安全，因为狡猾的开发人员可能会向 `#OO` 用户授予对象访问权限，然后更新分配给其账户的容器中的 HDI 角色，以提升自己的权限。

