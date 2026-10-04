
# 586 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonondon

![](img/2b52fde0e707e8c2f05a10309c3f8982_597_0.png)

图 6.4. Android Studio 项目详情。

- 4. 点击完成（finish）后，Android Studio 将开始下载构建项目所需的 Gradle 文件，如图 6.5 所示。这需要一些时间以及互联网连接。

![](img/2b52fde0e707e8c2f05a10309c3f8982_597_1.png)

图 6.5. Gradle 设置过程。

- 5. 在 Gradle 对项目进行首次构建后，现在对其进行修改以适应项目需求。默认情况下，会创建一个空活动（activity），并创建与布局交互的相应类，如图 6.6 所示。这两个默认文件分别是用于程序布局的 activity_main.xml 和用于程序交互的 MainActivity.java。

## 基于云的实时数据采集与客户端架构

![](img/2b52fde0e707e8c2f05a10309c3f8982_598_0.png)

6.6. 默认 MainActivity.java。

## 6.3.2. Android 应用中使用的库

表 6.1 显示了 Android 应用中使用的库、该库执行的功能描述以及下载链接。

## 表 6.1. Android 应用中使用的库

| 库 | 描述 | 链接 |
| --- | --- | --- |
| Cloudant Client | 包含多个用于通过程序与 Cloudant 数据库交互的类 | https://mvnrepository.com/artifact/com.cloudant/cloudant-client/2.119.1 |
| JSOUP | JSOUP 是一个处理真实 HTML 的 Java 库。它提供了非常方便的 API 用于获取 URL 以及提取和处理数据，利用了 HTML5 DOM 方法和 CSS 选择器的最佳特性。 | https://mvnrepository.com/artifact/org.jsoup/jsoup/1.13.1 |
| JSON | 用于将 JSON 文档解析为 Java 对象，并从 Java 类生成新的 JSON 文档。 | https://mvnrepository.com/artifact/org.json/json/20210307 |
| MPAndroidChart | 适用于 Android 的强大且易用的图表库 | https://mvnrepository.com/artifact/com.github.PhilJay/MPAndroidChart/v3.0.0 |

要向 Android Studio 项目添加库，必须遵循以下步骤：

- 1. 按下“Ctrl+Shift+Alt+S”打开“项目结构”（Project Structure）窗口。将显示图 6.7 所示窗口。点击“依赖”（Dependencies）并选择“所有模块”（All Modules>）。

# 588 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonon

![](img/2b52fde0e707e8c2f05a10309c3f8982_599_0.png)

图 6.7. 项目结构表。

- 2. 要向项目添加新依赖，点击 + 按钮并选择“库依赖”（Library Dependency）。将显示图 6.8 所示窗口。

![](img/2b52fde0e707e8c2f05a10309c3f8982_599_1.png)

图 6.8. 添加库依赖。

- 3. 要向项目添加新库，在搜索区域输入库的名称并点击搜索按钮。例如，要添加 JSOUP 库，在搜索区域输入“JSOUP”并点击搜索。将显示该库的不同版本。

## 基于云的实时数据采集与客户端架构 589

![](img/2b52fde0e707e8c2f05a10309c3f8982_600_0.png)

图 6.9. 添加 JSOUP 库。

- 4. 选择所需的版本并点击 OK。所选的库将被添加到项目中，如图 6.10 所示。重复步骤 1 到 3 以添加其他库。

![](img/2b52fde0e707e8c2f05a10309c3f8982_600_1.png)

图 6.10. JSOUP 库已添加到项目。

- 5. 某些库需要在“Build.gradle”文件中添加一个远程仓库。这些库提供了向项目添加所需的自定义设置。例如，Android 要求向项目添加 Jitpack 仓库。Jitpack 仓库必须添加在 BUILD.GRADLE 文件中，如图 6.11 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_600_2.png)

图 6.11. 添加远程仓库。

# 590 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonon

## 6.3.3. 程序结构

表 6.2 显示了应用程序结构。详细列出了不同的类。

## 表 6.2. 应用结构

| MainActivity.java | QueryAPI.java | Analysis.java | QueryServer.java | DownloadData.java | QueryLocal.java | DataRetriever.java |
| --- | --- | --- | --- | --- | --- | --- |
| 使用: activity_main.xml | 使用: activity_main.xml | 使用: activity_main.xml | 使用: activity_main.xml | 使用: activity_main.xml | 使用: activity_main.xml | 使用: activity_main.xml |
| 负责 UI | 负责 UI | 负责 UI | 负责 UI | 负责 UI | 负责 UI | 负责 UI |
| ... | ... | ... | ... | ... | ... | ... |

*(注：表 6.2 的 OCR 文本在源码中是碎片；我根据 OCR 片段中发现重复类名重建了结构。）*

## 6.3.4. 构建主活动布局

首先，需要修改应用程序的布局，在 activity_main.xml 文件中添加所需的组件。图 6.12 显示了应用程序的组件树，显示了主活动设计的层级视图。

![](img/2b52fde0e707e8c2f05a10309c3f8982_602_0.png)

图 6.12. main_activity.xml 组件树。

布局由一个 ConstraintLayout 组成，它固定在屏幕上，其上的 LinearLayout 用于按行放置元素。

在第一行，放置了一个 EditText 用于用户输入本地服务器的 IP 地址，一个用于确定是否直接发送数据到云端的开关，以及一个名为 Monitor（监控）的按钮用于启动监控过程。

第二行包含一个用于切换监控变量的 spinner 和一个从 MPAndroidChart 库获取的 GraphView。

第三行包含一个名为 Analyze（分析）的按钮，点击后将启动用于预测的 Analysis Activity。Analysis Activity 将在本节稍后部分描述。

图 6.13 显示了完成的应用设计。spinner 尚可见，因为尚未使用相应的数组创建它。

