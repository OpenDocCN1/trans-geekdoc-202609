

一旦数据建模并清理以满足报告规范，请导航到报表视图以构建交互式报表。此视图允许报表创建者做他们最擅长的事：构建报表。以下步骤可用于创建报表，该报表将显示每个公路自行车子类别的总订单销售额和总订单数量。

## 1. 为产品名称创建切片器

有两种方法可以开始使用 Power BI Desktop 创建可视化效果。你可以将字段窗格中的字段拖到画布上并选择合适的可视化效果，或者将可视化窗格中的可视化效果拖到画布上并将数据字段拖到相应的设置中。对于此筛选器，我们将从 `Product Category` 表中拖动 `Names` 字段到画布上并选择 `Slicer` 可视化效果。在切片器中选择 `Road Bikes`，以筛选页面上的每个可视化效果，仅显示公路自行车的数据。

## 2. 创建聚集柱形图以显示每个已售产品类别的总订单数量

选择 `Clustered Column Chart` 可视化效果以创建空白聚集柱形图。将 `Product` 表中的 `Name` 字段拖到 `Axis` 设置中。接下来，将 `Sales Order Detail` 表中的 `OrderQty` 字段拖到 `Values` 设置中。这将创建一个聚集柱形图，显示每个产品的销售数量。由于切片器正按公路自行车类别主动筛选报表，柱形图将显示每个公路自行车子类别的订单数量数据。你可以随时通过单击 `Visualizations` 窗格中的 `Format` 图标并更改柱形颜色、文本字体、标题和数据标签等设置来修改可视化效果的格式。

## 3. 创建三个卡片可视化效果，分别显示总销售额、总订单数量和最受欢迎的商品

选择 `Card` 可视化效果三次，在画布上创建三个空白卡片。将以下内容添加到每个卡片中：

1. 对于第一张卡片，将 `Sales Order Detail` 表中的 `OrderQty` 字段拖到 `Fields` 设置中。Power BI 将自动聚合 `OrderQty` 字段，以根据任何应用的筛选器显示其总和。

2. 对于第二张卡片，将 `Sales Order Detail` 表中的 `LineTotal` 字段拖到 `Fields` 设置中。Power BI 将自动聚合 `LineTotal` 字段，以根据任何应用的筛选器显示其总和。

3. 对于第三张卡片，将先前定义的 `Most Popular Item` 度量值从 `Product` 表拖到 `Fields` 设置中。Power BI 将使用此度量值，根据任何应用的筛选器显示 `OrderQty` 值最高的商品。

作为交互式报表，筛选功能不仅限于切片器可视化效果。单击柱形图中的任何柱子时，页面将进行筛选，以便其他可视化效果聚焦于与单击柱子关联的特定产品名称。此外，如果你将鼠标悬停在任何柱子上，将看到一个工具提示，显示该特定产品的产品名称和订单数量。[Figure 6.9](#c06.xhtml#c06-fig-0009) 说明了带有柱形图中第一个柱子工具提示的完成报表。

![FIGURE 6.9 Power BI Desktop Report view on the Order Quantity Sold Per Item page](images/c06f009.png)

[FIGURE 6.9](#c06.xhtml#R_c06-fig-0009) Power BI Desktop Report view on the Order Quantity Sold Per Item page

构建完报表后，可以将文件本地保存为 `PBIX` 文件。`PBIX` 文件（使用 `.pbix` 文件扩展名保存）可以随时由 Power BI Desktop 打开，以便报表创建者修改用于驱动报表的可视化效果、数据模型和查询定义。除了将报表保存为 `PBIX` 文件外，还可以将报表保存为 Power BI 报表模板（`PBIT`），其他报表创建者可以将其用作新报表布局、数据模型和查询定义的起点。与 `PBIX` 文件不同，`PBIT` 文件（使用 `.pbit` 文件扩展名保存）不包含用于驱动报表的数据。有关 Power BI 报表模板的更多信息，请参阅 `https://docs.microsoft.com/en-us/power-bi/create-reports/desktop-templates`。

## 使用 Power BI 服务发布和共享交互式报表

既然数据模型和报表已准备好与其他用户共享，让我们将报表发布到 Power BI 服务。你可以通过单击 `Home` 功能区中的 `Publish` 按钮，并为报表和数据模型选择目标工作区来完成此操作。请记住，在发布报表之前，你需要先登录服务。

`Workspaces` 在 Power BI 服务中充当容器，用户可以在其中逻辑地组织内容并与同事协作。单个工作区可以托管多个数据集、报表和仪表板，以满足特定业务单元或特定解决方案的报告需求。拥有 Power BI Pro 或 Power BI Premium Per User 许可证的内容创建者可以将工作区内容共享给不同用户，并通过分配以下角色之一来控制其访问级别：

* `Viewer`—分配此角色的用户只能查看和与工作区中包含的报表和仪表板进行交互。

* `Contributor`—分配此角色的用户将获得 `Viewer` 权限以及创建、编辑和删除内容的能力。这包括将报表发布到工作区、下载报表和计划数据刷新。

* `Member`—分配此角色的用户将获得 `Viewer` 和 `Contributor` 权限，以及将其他用户添加到工作区并授予 `Viewer` 或 `Contributor` 权限的能力。

* `Admin`—分配此角色的用户将对工作区拥有完全控制权，包括更新和删除工作区的能力。

有关 Power BI 工作区角色的更多信息，请参阅 `https://docs.microsoft.com/en-US/power-bi/collaborate-share/service-roles-new-workspaces#workspace-roles`。

可用于用户的工作区功能（例如，他们可以计划数据刷新的次数或工作区可以管理的最大数据模型大小）取决于用户拥有的许可证类型以及应用于工作区的 Power BI 计划。虽然许可证不在 DP-900 考试范围内，但重要的是要知道，用户可以使用 Power BI Pro 或 Power BI Premium Per User 许可证来管理内容，并且工作区可以使用共享容量或高级（专用）容量。许可证和计划类型之间的功能和价格差异可以在 `https://powerbi.microsoft.com/en-us/pricing` 上找到。

工作区内容按仪表板、报表和数据集以及迄今未讨论的另外两个对象（工作簿和数据流）组织成不同的部分。Power BI 工作簿是导入到 Power BI 工作区的 Excel 工作簿。一旦导入到 Power BI 工作区，工作簿将转换为可用于提供新报表的数据集。Power BI 数据流提供与 Power BI Desktop Power Query 编辑器类似的数据连接、引入和转换功能，但由 Power BI 服务管理。

你可以通过访问 `https://powerbi.com` 导航到 Power BI 服务。登录后，你将能够使用左侧菜单中的按钮浏览服务。该菜单分为两个部分，顶部包括将用户带到常用页面的按钮，例如 Power BI 服务主页、最近查看的对象、Power BI 应用和部署管道。左侧菜单的底部允许用户导航到他们有权访问的不同工作区。

