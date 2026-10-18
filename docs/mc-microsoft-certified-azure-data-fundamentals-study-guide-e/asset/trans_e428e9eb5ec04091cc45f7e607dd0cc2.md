

# 构建带有复制数据活动的 ADF 管道

以下部分“构建带有复制数据活动的 ADF 管道”将详细介绍如何创建与管道关联的活动、数据集和链接服务，如[图 5.20](#c05.xhtml#c05-fig-0020)（前面所示）所示。更具体地说，它将演示如何使用复制活动将数据从 Azure SQL 数据库复制到 ADLS 帐户。源数据库是从公开可用的 AdventureWorksLT2019 数据库备份还原的。如果您想自行构建此演示，可以在 `https://docs.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver15&tabs=ssms#download-backup-files` 处找到数据库备份。

## 构建带有复制数据活动的 ADF 管道

在 Azure Data Factory Studio 中创建 ADF 管道的第一步是导航到“创作”页面，方法是单击左侧工具栏上的“创作”按钮或主页上的“编排”按钮。“创作”页面左侧窗格包含名为“工厂资源”的树形视图。从此处，您可以单击每个菜单项旁边的 + 按钮或省略号 (…) 来创建或浏览现有管道、数据集、映射数据流或 Power Query 活动。[图 5.23](#c05.xhtml#c05-fig-0023) 说明了如何通过单击 + 按钮创建空白管道。

![FIGURE 5.23 Creating a blank ADF pipeline](images/c05f023.png)

[FIGURE 5.23](#c05.xhtml#R_c05-fig-0023) 创建空白 ADF 管道

单击“管道”后，将打开一个空白管道画布，画布左侧有一个新工具栏，其中包含可以添加到管道的每个活动。可以从“活动”工具栏将这些活动中的任何一个拖动到中央画布上以构建管道。在画布顶部，有用于验证管道是否存在错误、调试管道以及向管道添加触发器的按钮。在画布右侧是“属性”选项卡，您可以在其中为管道添加友好名称和描述。在画布底部，有用于创建新参数和变量的选项，这些参数和变量可以使管道运行更加动态。[图 5.24](#c05.xhtml#c05-fig-0024) 说明了这些组件，并在“属性”选项卡中添加了友好名称。

![FIGURE 5.24 The ADF Pipeline Creation page](images/c05f024.png)

[FIGURE 5.24](#c05.xhtml#R_c05-fig-0024) ADF 管道创建页面

要添加复制活动，请在“活动”工具栏中展开“移动和转换”选项，并将“复制数据”活动拖动到画布上。新活动将包含六个配置选项卡，这些选项卡将位于选项卡底部。第一个选项卡（“常规”选项卡）允许您为活动提供友好名称和描述，以及超时和重试设置。[图 5.25](#c05.xhtml#c05-fig-0025) 是此视图的示例，其中包含描述活动功能的友好名称。

![FIGURE 5.25 Copy Data Activity: General tab](images/c05f025.png)

[FIGURE 5.25](#c05.xhtml#R_c05-fig-0025) 复制数据活动：常规选项卡

在六个复制活动配置选项卡中，只有两个需要用户输入：源选项卡和接收器选项卡。这两个选项卡将定义源数据集和目标（或接收器）数据集，数据将被复制到该数据集。源选项卡允许您选择现有数据集或创建新数据集。如果单击“+ 新建”按钮，将打开一个新页面，您可以在其中从可用的数据源连接器中进行选择（请参阅[图 5.26](#c05.xhtml#c05-fig-0026)）。

![FIGURE 5.26 New Dataset page](images/c05f026.png)

[FIGURE 5.26](#c05.xhtml#R_c05-fig-0026) 新建数据集页面

在搜索栏中，键入 **Azure SQL 数据库** 并选择 Azure SQL 数据库连接器。单击页面底部的“继续”以打开数据集的“设置属性”页面。此页面允许您为数据集设置友好名称，并选择/创建将用于连接到数据源的链接服务。展开“链接服务”下拉菜单并单击“+ 新建”以为数据库创建链接服务。这将打开一个新页面，您可以在其中为链接服务设置友好名称、集成运行时以及数据库的连接信息。[图 5.27](#c05.xhtml#c05-fig-0027) 是 Azure SQL 数据库的“新建链接服务”页面的完成示例。

![FIGURE 5.27 New linked service page: Azure SQL Database](images/c05f027.png)

[FIGURE 5.27](#c05.xhtml#R_c05-fig-0027) 新建链接服务页面：Azure SQL 数据库

链接服务设置正确后，单击“创建”按钮以创建链接服务并重定向到数据集的“设置属性”页面。定义链接服务后，下一步是选择数据集将代表的表或视图，或将“表名”设置留空。为了本示例的目的，我们将选择 SalesLT.ProductCategory 表。[图 5.28](#c05.xhtml#c05-fig-0028) 是“设置属性”页面的完成示例。

![FIGURE 5.28 Set properties page for a new dataset: Azure SQL Database](images/c05f028.png)

[FIGURE 5.28](#c05.xhtml#R_c05-fig-0028) 新建数据集的设置属性页面：Azure SQL 数据库

单击“设置属性”页面底部的“确定”后，数据集将被创建并添加为复制活动中的源数据集。由于源数据集是 Azure SQL 数据库，源选项卡包括几个针对关系数据库定制的可选设置。例如，如果您在数据集选项卡中未选择表或视图，可以使用查询或存储过程来定义数据集。您还可以参数化此设置，以便数据集基于传递给参数的值而变化。[图 5.29](#c05.xhtml#c05-fig-0029) 说明了 Azure SQL 数据库源选项卡中可用的选项列表。

![FIGURE 5.29 Copy Data Activity: Source tab](images/c05f029.png)

[FIGURE 5.29](#c05.xhtml#R_c05-fig-0029) 复制数据活动：源选项卡

现在源数据集已设置，下一步是配置接收器数据集。接收器选项卡提供与源选项卡相同的选项，并具有创建新数据集的功能。由于本示例使用 ADLS 帐户作为接收器数据存储，请在“新建数据集”页面上选择 Azure Data Lake Storage Gen2 连接器。单击“继续”后，系统将提示您为数据集设置文件格式。对于本示例，请选择 DelimitedText (CSV) 选项并单击“继续”。

与 Azure SQL 数据库数据集一样，“设置属性”页面允许您为数据集设置友好名称，并选择/创建将用于连接到数据源的链接服务。ADLS 的新建链接服务页面也与 Azure SQL 数据库的新建链接服务页面类似，因为它允许您为链接服务设置友好名称、集成运行时以及存储帐户的连接信息（请参阅[图 5.30](#c05.xhtml#c05-fig-0030)）。单击“创建”按钮以创建链接服务并重定向到数据集的“设置属性”页面。

![FIGURE 5.30 New linked service page: ADLS](images/c05f030.png)

[FIGURE 5.30](#c05.xhtml#R_c05-fig-0030) 新建链接服务页面：ADLS

定义 ADLS 链接服务后，“设置属性”页面允许您为数据集设置文件路径或将其留空。本示例为接收器数据集使用 `dp900-adls-container/products/` 文件路径（请参阅[图 5.31](#c05.xhtml#c05-fig-0031)）。

![FIGURE 5.31 Set properties page for a new dataset: ADLS](images/c05f031.png)

[FIGURE 5.31](#c05.xhtml#R_c05-fig-0031) 新建数据集的设置属性页面：ADLS

