

# 基于云的实时... 数据采集与客户端架构 ... 647

# 表 6.4. Main.java 中不同元素的功能

| 变量名 | Swing 元素 | 功能 |
| :--- | :--- | :--- |
| window_s | JTextField | 用户输入算法的窗口大小值 |
| ptime | JTextField | 用户输入预测时间 |
| predict | JButton | 点击时，开始预测 |
| monitor | JButton | 点击时，创建一个 New Timer 对象并调度每隔 N 分钟执行一次 TimerTask |
| result | JTextArea | 用于显示从本地服务器或 Java Servlet 获取的预测算法结果的区域 |
| w_var | JComboBox | 选择用于显示图表的变量 |
| address_f | JTextField | 用户输入本地服务器 IP 地址的文本框 |
| cloud_wave | JComboBox | 决定是将数据直接发送到云端还是本地服务器 |
| window_label | JLabel | 如果勾选，则发送到云端，否则发送到本地服务器 |
| prediction_label | JLabel | window JTextField 的标签 |
| result_label | JLabel | prediction JTextField 的标签 |
| graph_label | JLabel | result JTextArea 的标签 |
| IP_label | JLabel | 图表的标签 |
| cloud_label | JLabel | address JTextField 的标签 |
| download_label | JLabel | 保存到云 JCheckBox 的标签 |
| download_date | JLabel | 窗口大小 JTextField 的标签 |
| download_Samples | JButton | date JTextField 的标签。点击时，获取指定样本量的应用程序数据 |
| download_date | JButton | 点击时，获取指定日期的应用程序数据 |
| View_label | JLabel | 查看 JTextArea 的标签 |
| down_n | JTextField | 用于输入获取样本数量的 JTextField |
| down_date | JTextField | 用于输入所需样本日期的 JTextField |
| data_view | JTextArea | 用于查看从云端获取的数据的 JTextArea |
| data_src | JComboBox | 选择使用的数据源 |

# 6.4.2. 添加库

该应用程序使用了三个 Java 库，需要使用 NetBeans 的导入功能进行导入。每个库实现的功能在表 6.5 中进行了解释，在项目中添加这些库的步骤如下所示。还列出了可以下载每个库的 GitHub 仓库。

- 1. 首先，在项目目录下创建一个名为 'lib' 的新文件夹。此文件夹将存储所有库的 jar 文件。
- 2. 然后，从各自的 GitHub 仓库下载所需的库并保存到之前创建的文件夹中。
- 3. 下载 jar 文件后，使用 NetBeans 将文件导入项目。首先，展开项目树并找到“Libraries”（库）文件夹。

# 648 T. P. Fowdar, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoonondan

# 表 6.5. 桌面应用程序使用的库

| 库 | 用途 | Jar 文件 |
| :--- | :--- | :--- |
| Cloudant Manager | 包含多个类，用于编程与 Cloudant 数据库交互 | https://github.com/cloudant/java-cloudant | * cloudant-http-2.19.2.jar<br>* cloudant-http-2.19.2.jar<br>* commons-codec-1.6.jar<br>* commons-io-2.4.jar<br>* gson-2.8.6.jar |
| JSON | 用于将 JSON 文档解析为 Java 对象并从 Java 类生成新的 JSON 文档。 | https://github.com/stleary/JSON-java | json-20210307.jar |
| JSoup | jsoup 是一个用于处理 HTML 的 Java 库。它提供了用于处理 URL、操作数据以及 DOM 选择器的方便 API。 | https://mvnrepository.com/artifact/jsoup | jsoup-1.13.jar |
| JFreeChart | JFreeChart 是一个全面的库，用于创建带有新值的图表。 | https://github.com/jfree/jfreechart | freechart-1.0.jar<br>* freechart-1.1.jar<br>* freechart-1.2.jar<br>* freechart-1.3.jar<br>* freechart-1.4.jar<br>* freechart-1.5.jar<br>* freechart-1.6.jar<br>* freechart-1.7.jar<br>* freechart-1.8.jar<br>* freechart-1.9.jar<br>* freechart-1.0.1.jar<br>* freechart-1.0.2.jar<br>* freechart-1.0.3.jar<br>* freechart-1.0.4.jar<br>* freechart-1.0.5.jar<br>* freechart-1.0.6.jar<br>* freechart-1.0.7.jar<br>* freechart-1.0.8.jar<br>* freechart-1.0.9.jar<br>* freechart-1.0.10.jar<br>* freechart-1.0.11.jar<br>* freechart-1.0.12.jar<br>* freechart-1.0.13.jar<br>* freechart-1.0.14.jar<br>* freechart-1.0.15.jar<br>* freechart-1.0.16.jar<br>* freechart-1.0.17.jar<br>* freechart-1.0.18.jar<br>* freechart-1.0.19.jar |

Figure 6.4. 库。

- 4. 右键点击“Libraries”文件夹，会出现包含添加选项的弹出菜单。

Figure 6.41. 库文件夹。

- 5. 点击之前的选项后，将打开一个选择 jar 文件的窗口。导航到项目根目录并点击 lib 以查看其内容。所有 jar 文件都被选中并点击了“Open”（打开）按钮。

![](img/2b52de0e708c2f05a10293f82_660.png)

Figure 6.42. 弹出菜单。

Figure 6.43. 选择 JAR 文件。

# 6.4.3. 程序结构

表 6.6 显示了桌面程序的结构。

# 表 6.6. 桌面项目结构

| DataRetriever.java | Mainframe.java |
| :--- | :--- |
| 负责从 Cloudant 数据库获取数据。 | 显示用户界面。 |
| Mainframe 类中的方法 | |
| MainForm() – 显示 GUI 并初始化图表的构造函数。 | waActionPerformed() – 当 wComboBox 改变时触发。通过清除所有值和数据来重置图表。 |
| monitorActionPerformed() – 点击监控按钮时触发。启动或结束监控线程。 | predictActionPerformed() – 从本地服务器或云端 servlet 获取分析结果。 |
| sendData() – 将来自 API 的数据发送到 Cloudant 数据库。 | downloadActionPerformed() – 启动线程从本地服务器下载特定日期的所有记录。 |
| requestDataLocal() – 从本地服务器请求 CSV 数据 | requestAnalyticsCloud() – 从云端 servlet 请求分析结果。 |
| requestDataCloud() – 从云服务器请求 CSV 数据 | requestAnalyticsLocal() – 从本地 servlet 请求分析结果。 |
| downloadActionPerformed() – 启动线程从数据库下载最后 N 行。 | |
| DataRetriever 类中的方法 | |
| DataRetriever() – 建立 Cloudant 数据库连接的主构造函数 | |
| getNoOffs() – 获取数据库中的行数 | |
| getDatabase() – 获取特定日期的最后 N 个气象观测值。 |

 6.4.4. MainFrame 类

MainFrame 类是负责显示应用程序 GUI、更新来自 API 的新数据以及请求 Java Servlet 获取预测的主类。预测结果随后显示在 result TextArea 中。

# 6.4.4.1. 添加导入

为了程序正常运行，需要从相应的包导入正确的类。列表 6.23 列出了必要的导入类及其在程序中的功能。

# 列表 6.23. 导入

// 此类构建 CloudClient 实例。
import com.cloudant.client.api.ClientBuilder;
// 暴露 Cloudant API
import com.cloudant.client.api.CloudantClient;
// 包含数据库公共 API
import com.cloudant.client.api.Database;
// 在数据结构中包含查询结果
import com.cloudant.client.api.query.QueryResult;

