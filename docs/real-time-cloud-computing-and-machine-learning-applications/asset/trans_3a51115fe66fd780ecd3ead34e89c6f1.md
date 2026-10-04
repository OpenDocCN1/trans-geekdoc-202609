

# 基于云的实时数据采集与客户端架构... 637

2. 运行在 PC 上 NetBeans IDE 的本地服务器 IP 地址可以输入第一个 EditText 中，然后点击“MONITOR”（监控）按钮启动网络监控活动。

![](img/2b52fde0e707e8c2f05a10309c3f8982_648_0.png)

图 6.22 可见性变化监控。

![](img/2b52fde0e707e8c2f05a10309c3f8982_648_1.png)

图 6.23. 直接将数据发送到云端。

# 638 T. P. Fowdar, L. Babooram, M. N-U-Dbn Nazir Rosun 和 M. Indoonundan

3. 默认情况下，图 6.21 所示的下拉菜单选择了“Visibility”（可见性）参数。当监控开始时，图表将根据从 API 获取的相应值进行更新。从 API 获取的数值适用于“Port Louis”地区。图表如图 6.22 所示。

4. 要将数据发送到本地服务器，必须关闭“Cloud”（云）开关。要将数据直接发送到云数据库，必须将“Cloud”开关切换到“ON”（开启）位置，如图 6.23 所示。

5. 图表显示的参数通过图表下方的下拉菜单进行更改，如图 6.24 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_649_0.png)

图 6.24. 用于更改显示天气参数的下拉菜单。

![](img/2b52fde0e707e8c2f05a10309c3f8982_649_1.png)

图 6.25 使用风速值更新的图表。

6. 例如，在图 6.25 中，选择了“Wind Speed”（风速），观察到图表的描述随之发生了变化。使用“STOP”（停止）按钮停止监控过程，图表停止更新且不再从 Web API 请求数据。

7. 图 6.26 和图 6.27 显示了被推送到 Cloudant 平台和 MySQL 本地数据库的数据。

![](img/2b52fde0e707e8c2f05a10309c3f8982_650_0.png)

图 6.26 推送到 MySQL 服务器的数据。

![](img/2b52fde0e707e8c2f05a10309c3f8982_650_1.png)

图 6.27 推送到 Cloudant 数据库的数据。

## 6.3.28.2. 下载天气数据

- 1. 通过点击主活动（Main Activity）上的“DOWNLOAD DATA”（下载数据）按钮，启动“DownloadData”活动，如图 6.28 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_651_0.png)

图 6.28. DownloadData 活动。

- 2. 要从 Cloudant 平台下载天气观测数据，将“Cloud”开关切换到“ON”位置。然后按下“DOWNLOAD”（下载）按钮。要从本地 Java 平台下载天气观测数据，将“Cloud”开关切换到“OFF”（关闭）位置。在 EditText 中输入本地服务器的 IP 地址。然后按下“DOWNLOAD”按钮。
- 3. 从 Cloudant 平台下载最后 N 个样本，首先在“Download Last N Samples”字段中输入数量。然后按下“DOWNLOAD”按钮。应用程序将指定数量的天气观测下载到 CSV 文件中。应用程序将文件保存在默认的“Download”文件夹中，并将数据保存在“result” TextView 中，如图 6.29 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_651_1.png)

图 6.29 从 Cloudant 下载样本。

4. 要按日期下载，在指定了“DD/MM/YYYY”格式的数据后，点击另一个“DOWNLOAD”按钮。应用程序将指定日期的天气观测数据下载到 CSV 文件并保存在应用程序文件夹中，同时将在图 6.30 所示的 TextView 中显示下载的数据。

![](img/2b52fde0e707e8c2f05a10309c3f8982_652_0.png)

图 6.30 带有特定日期读数的 CSV 文件。

## 6.3.28.3. 执行分析

- 1. 通过点击主活动上的“ANALYSE”（分析）按钮，启动如图 6.31 所示的“Analysis”活动。

![](img/2b52fde0e707e8c2f05a10309c3f8982_652_1.png)

图 6.31. 分析活动。

![](img/2b52fde0e707e8c2f05a10309c3f8982_653_0.png)

图 6.32 显示来自 Servlet 的结果。

- 2. 要对收集的数据进行分析，必须相应输入回归算法的窗口大小和需要分析的时间，并点击相应的按钮。
- 3. “Cloud Analysis”（云分析）按钮用于从云端获取分析结果，“Local Analysis”（本地分析）按钮用于从本地 Java 服务器获取分析结果（前提是在 EditText 中输入了 IP 地址）。
- 4. 分析完成后，获得的结果显示在 result TextView 中。当选择“Cloud Analysis”选项时，预期的输出如图 6.32 所示。

## 6.4. 用于天气数据采集和分析的桌面应用程序

本节提供了提供了使用 Java 开发桌面应用程序的详细步骤指南。该应用程序将从 OpenWeather API 请求当前天气状况，实时显示所需的变量读数，并请求 Java Servlet 获取未来的天气状况。该应用程序在 NetBeans IDE 中开发，该 IDE 支持通过拖放功能来构建 GUI 应用程序。

## 6.4.1. 在 NetBeans 中创建桌面应用程序

在 NetBeans 中创建 Java Swing 应用程序的步骤如下：
- 1. 启动 NetBeans，通过“File”（文件）然后“New Project”（新建项目）创建一个新项目。

![](img/2b52fde0e707e8c2f05a10309c3f8982_654_0.png)

图 6.33 新项目。
- 2. 下一步是选择项目类型。为此，选择类别“Java”以使用 Ant 工具，项目类型选择为“Java Application”（Java 应用程序）。

![](img/2b52fde0e707e8c2f05a10309c3f8982_654_1.png)

图 6.34 项目类别与类型。

- 3. 指定新项目的名称和位置。这里一个重要的步骤是取消勾选“Create Main Class”（创建主类）复选框。这将防止创建带有 main 方法的方法。点击 Finish（完成）按钮。

![](img/2b52fde0e707e8c2f05a10309c3f8982_655_0.png)

图 6.35 项目名称与位置。
- 4. 新创建的项目是空的，没有类。要显示窗口，需要通过右键点击默认包来添加 JFrame 类。会弹出一个窗口，选择“New”（新建）然后“JFrame Form”。

![](img/2b52fde0e707e8c2f05a10309c3f8982_655_1.png)

图 6.36 添加 JFrame。

- 5. 如图 6.37 所示的窗口将在添加到源包之前对 JFrame 类进行命名。输入适当 JFrame 名称，然后点击完成按钮。
- 6. 下一步是使用 NetBeans 的拖放功能构建 GUI。可以通过点击顶部的“Design”（设计）进入设计模式。GUI 设计模式由 GUI 元素调板组成，可以将它们拖入设计界面并放置在所需的 JFrame 上。这节省了时间，因为 IDE 会自动生成显示 GUI 元素的代码。

![](img/2b52fde0e707e8c2f05a10309c3f8982_656_0.png)

图 6.38 带有调板的 GUI 设计。

- 7. 图 6.39 和图 6.40 显示了 JFrame 中存在的 GUI 元素以及 JFrame 的最终设计。

![](img/2b52fde0e707e8c2f05a10309c3f8982_657_0.png)

图 6.39 GUI 设计。
导航器标签页提供了 JFrame 中元素放置的树形结构。它还显示了 GUI 元素类型和变量名。表 6.4 详细说明了每个 GUI 元素的作用。

![](img/2b52fde0e707e8c2f05a10309c3f8982_657_1.png)

图 6.40 JFrame GUI 元素导航器。

