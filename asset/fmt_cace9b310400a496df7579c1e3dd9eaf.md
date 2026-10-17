
## 7.2. 测试本地服务器

本节详细描述了本地服务器应用程序的操作流程。

### 7.2.1. 实时监控

- 1. 当应用程序启动时，会向用户显示图 7.14 所示的 GUI。

![](img/2b52fde0e707e8c2f05a10309c3f8982_754_0.png)

图 7.14 本地服务器应用程序。

- 2. 当按下“Monitor”（监控）按钮时，将启动一个线程，启动 `ServerSocket` 以监控来自边缘设备的接入连接。随着数据的接收，图表如图 7.15 所示。数据被发送到托管在 XAMP 上的本地数据库以及云端的 Cloudant 数据库。

![](img/2b52fde0e707e8c2f05a10309c3f8982_755_0.png)

图 7.15 监控已启动且图表更新。

- 3. 实时图表上观察到的天气参数可以使用 ComboBox 进行更改，如图 7.16 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_755_1.png)

图 7.16 使用 `JComboBox` 更改图表上的天气参数。

- 4. 例如，如图 7.17 所示，选中了“Wind Direction”（风向）参数。

![](img/2b52fde0e707e8c2f05a10309c3f8982_756_0.png)

图 7.17 风速图。

### 7.2.2. 下载天气数据

- 1. 要使用本地数据库的数据，用户必须在 `JComboBox` 中选择“Local database”（本地数据库）；若要使用 Cloudant 数据库的数据，用户必须在 `JComboBox` 中选择“Cloud database”（云数据库），如图 7.18 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_756_1.png)

图 7.18 选择数据源。

![](img/2b52fde0e707e8c2f05a10309c3f8982_757_0.png)

图 7.19 使用 `JFileChooser` 选择保存文件的位置。

- 2. 要下载最后 N 个天气样本，首先在 "Download Last N data" `JTextField` 中输入样本数。然后按下“Download”（下载）按钮。应用程序将指定数量的天气观测结果下载到 CSV 文件中。

![](img/2b52fde0e707e8c2f05a10309c3f8982_757_1.png)

图 7.20 文本框中下载的数据。

- 3. 将向用户显示一个 `JFileChooser` 窗口，用户可以选择保存 CSV 文件的位置，如图 7.19 所示。应用程序还将在结果 `TextView` 中显示下载的数据，如图 7.20 所示。

- 4. 要下载特定日期的天气观测数据，在 "Download Data for:" `JTextField` 中输入所需的日期。然后按下“Download”（下载）按钮。应用程序将重复步骤 2，允许用户选择保存文件的位置。

- 5. 在特定目录下下载的 CSV 文件如图 7.21 所示。根据用户的请求，它们会被自动标记为“weather_data x”和“weather_data y”。

![](img/2b52fde0e707e8c2f05a10309c3f8982_758_0.png)

图 7.21 最后 10 条记录的 CSV 文件和 2020/11/29 的 CSV 文件。

### 7.2.3. 执行分析

- 1. 要使用本地数据库的数据，用户必须在 `JComboBox` 中选择“Local database”；要使用 Cloudant 数据库的数据，用户必须在 `JComboBox` 中选择“Cloud database”。

- 2. 用户可以通过点击“Predict”（预测）之前指定“Prediction Time”（预测时间）和“Window Size”（窗口大小）来执行分析。应用程序将执行分析并在图 7.22 中显示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_759_0.png)

图 7.22 预测。

## 7.3. 用于预测和数据检索的 servlet

在本节，开发了一个向用户提供以下功能的 servlet：

- 在云端执行并获取结果。
- 下载特定日期的天气数据或仅下载最后 N 个样本。
- 在每 15 分钟更新一次的图表中观察天气变化。

该 servlet 在 `Eclipse IDE` 中开发，支持作为本地服务器或 Cloudant 服务器部署。

### 7.3.1. 安装 IBMSphere 插件

要安装 IBMSphere 插件，必须遵循以下步骤：

- 1. 通过启动 Eclipse 并从 Help（帮助）菜单访问来启动 Marketplace Client，如图 7.23 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_760_0.png)

图 7.23 访问 Eclipse Marketplace。

- 2. 一旦启动 Marketplace Client，它会显示一个类似于图 7.24 窗口的向导程序。

![](img/2b52fde0e707e8c2f05a10309c3f8982_760_1.png)

图 7.24 Eclipse Marketplace 窗口。

- 3. 访问链接 https://marketplace.eclipse.org/content/eclipse-tools-cloud-foundry 以访问“Eclipse Tools for Cloud Foundry”插件，如图 7.25 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_761_0.png)

图 7.25 Eclipse Tools for Cloud Foundry。

- 4. 将 install（安装）按钮拖入 Eclipse Marketplace Client 以将插件安装到 Eclipse 中。用户将看到一个接受插件许可证审查的窗口，如图 7.26 所示。点击“I accept the terms of the license agreement”（我接受许可协议条款）并点击“Finish”（完成）。插件随后将被下载并添加到 Eclipse。

![](img/2b52fde0e707e8c2f05a10309c3f8982_761_1.png)

图 7.26 许可证审查。

# 基于云的实时... 服务器与 Servlet 架构 751

### 7.3.2. Servlet 程序结构

程序中使用的类和方法总结在表 7.23 中，并在后续章节中进行了详细说明。

## 表 7.23. Servlet 程序结构

| `MainFrame.java` | `DataRetriever.java` | `DataSetSetter.java` |
|---|---|---|
| 显示主 GUI，从边缘设备检索数据，更新图表并发送到云端。 | 用于从 Cloudababase 获取一个值数组。 | 用于为不同类型的网络按适当顺序创建训练数据集。 |
| `MinMaxScalerNorm.java` | `CNNRegression.java` | `MLPRegression.java` |
| 使用最小最大法对 2D 数组进行列归一化 | 用于创建一个 CNN 网络来预测未来 15 分钟的多个天气参数 | 用于创建一个 MLP 网络来预测未来 15 分钟的单变量参数 |
| `Regression.java` | `RegressionPredictor.java` | `SQLConnector.java` |
| 创建 MLP 或多项式回归模型 | 使用 "regression" 创建用于天气预测的多项式和 MLP 模型。 | 用于连接 MySQL 数据以推送或获取数据。 |
| `MainFrame.java` 方法 | | |
| `main()`: : 初始化 GUI 的方法 | `initComponents()`: : 自动生成的代码，在相应的坐标上使用 GUI 元素。 |
| `drawAction()`: : 清除图表 | `monitorActionPerformed()`: : 监控过程 |
| `downloadActionPerformed()`: : 从云数据库下载最后 N 条数据并作为 CSV 文件 | `sendData()`: : 将数据发送到云数据库 |
| `convertToFloat()`: : 将 double 数组转换为 float | `roundOutput()`: : 将输出保留一位小数。 |
| `main()`: : 用于使用 GUI 并检查程序外观和感觉的方法 | `predictActionPerformed()`: : 使用所有算法预测天气参数。 |
| `download_actionPerformed()` : 从云数据库下载特定日期的所有数据并作为 CSV 文件 | | |
| `DataRetriever.java` 方法 | | |
| `DataRetriever()` : 建立到 Cloudababase 的连接。 | `getRows()`: : 获取数据库中元素的当前数量。 |
| `getDatabaseArray()`: : 从数据库获取最后 N 行数据。 | | |
| `SQLConnector.java` | | |
| `SQLConnector()` : 初始化到 MySQL 数据库连接的构造函数 | `fetchLastN()`: - 从本地数据库获取最后 N 行 |
| `fetchData()`: : 获取特定日期的所有数据。 | `insertIntoDatabase()`: - 在本地插入记录 |
| `DataSetSetter.java` 方法 | | |
| `DataSetSetter()` : 创建天气观测值的 2D 数组并对其进行归一化的构造函数 | `generateMultiVarDataSet()`: : 为 CNN 网络生成训练数据集。 | |
| `getLastTimestamp()`: : 根据观测值中的最后 n 行生成输入时间戳 | `getLastMLP()`: : 根据特定日期观测值中的最后 n 个值生成输入时间戳。 | |
| `generateSingleVarDataSet()`: : 为特定参数的 MLP 网络生成训练数据集 | `denormalize(float arr[])` : 对观测值数组进行反归一化。 |
| `denormalize(float value, int var)`: : 对特定参数进行反归一化 | `getCol()`: : 从 2D 数组中提取一列 |
| `getTargetNames()`: : 返回输出标签，继承自 TabularDataSet 类。 | | |

## 表 7.23. （续）

| `MinMaxNorm.java` 方法 |
|---|---|
| `MinMaxNorm()`: 接受 2D 数组并找到每列最小和最大值的主构造函数 | `Normalize()`: 使用最小最大法对 2D 数组进行归一化 |
| `denormalize (float i)`: 对值数组进行反归一化 | `denormalize (float norm, int var)`: 对给定变量索引的值进行反归一化 |
| **`CNNRegression.java` 方法** | | |
| `CNNRegression()`: 创建训练数据集和 CNN 网络 | `trainModel()`: 使用数据集和反向传播训练模型 | |
| `predictNext()`: 预测未来 15 分钟的未来七个参数 | | |
| **`MLPRegression.java` 方法** | | |
| `MLPRegression()`: 创建单变量训练数据集和 MLP 网络 | `trainModel()`: 使用数据集和反向传播训练模型 | |
| `predictNext()`: 预测未来 15 分钟的未来七个参数 | | |
| **`Regression.java` 方法** | | |
| `setWindow()`, `setType()`, `setTimeout` 方法用于为变量分配适当的值。 | | |
| `predict()`: 根据类型创建模型，并根据指定的预测变量返回预期的响应 y | | |
| **`RegressionPredictor.java` 方法** | | |
| `RegressionPredictor()`: 创建一个接受 2D 数组中每个天气参数数据的回归模型 | `polynomialPredict()`: 为每个天气参数创建一个回归模型并使用其进行时间预测 | |
| `multilPredict()`: 创建一个线性的 | `roundOutput()`: 将输出舍入到最近的小数位 | | |
| **`Downloader.java` 方法** | | |
| `response()`: 根据用户的查询创建 CSV 文件。CSV 文件包含特定日期的观测值或仅最后 N 个观测值。 | `doPost()`: 获取用户请求的详情并调用 `response()` 生成 CSV 文件并将数据发送给用户 | | |
| **`graphUpdater.java` 方法** | | |
| `doPost()`: 获取用户请求的详情，从数据库获取最后一次观测值并将所需的参数发送到网页 | | |
| **`Forecaster.java` 方法** | | |
| `doPost()`: 获取用户请求的详情，从数据库获取最后一次观测值并将所需的参数发送到网页 | `response()`: 使用所有算法计算未来的天气，并以 JSON 格式返回结果 | | |

### 7.3.3. 创建动态项目

在 Eclipse 中创建 Web 项目遵循以下步骤：

- 1. 启动应用程序并点击 "File" 然后 "New"，最后选择 "Dynamic Project"。
- 2. 会弹出一个新窗口，其中包含项目名称，并可以如图所示设置 "Target Runtime"。
- 3. 创建动态 Web 项目后，必要的文件夹将被创建。
- 4. 要将库导入到项目中，通过点击 "Alt + Enter" 打开项目属性。然后点击 "Java Build Path" 并点击 "Libraries" 选项卡。窗口将弹出。
- 5. 如图所示点击 "Add External Libraries"，定位所需的库并将其添加到项目中。库的过程和下载链接已在第 7.1.2 节解释。导入库后，点击 "Order and Export" 选项卡并选择所有，然后点击 "Apply."。然后点击 "Apply and Close" 应用更改并关闭窗口。

在导入负责预测计算的库和类之后，下一步是创建所需的 Servlet 类来执行指定的函数。

## 3.4.4. 向项目添加 Servlet

“Forecaster” Servlet 负责响应来自移动端和 PC 端用户的查询，为请求的时间提供天气预报。要向项目中添加新的 Servlet 类，请遵循以下步骤：

- 1. 按“Shift + Alt + N” 打开下拉菜单，并如图 7.33 所示选择 servlet。

![](img/2b52fde0e707e8c2f05a10309c3f8982_767_0.png)

图 7.33. 添加 Servlet 类。

- 2. 会出现一个新窗口，可以在其中如图 7.34 所示设置 Servlet 的名称和包名。Servlet 的名称设置为 "Forecaster”，"Java Package" 保持不变。Servlet 默认将生成在 "src" 包中。

## 基于云的实时...的服务器与 Servlet 架构

![](img/2b52fde0e707e8c2f05a10309c3f8982_768_0.png)

图 7.34. 设置 Servlet 名称与包。

3. 创建 Servlet 后，编辑器中将显示图 7.35 所示的类。

```java
import java.io.IOException;

/**
 * Servlet implementation class Forecaster
 */

@WebServlet("/forecaster")
public class Forecaster extends HttpServlet {
    public static final long serialVersionUID = 1L;

    // @WebServlet(HttpServletServlet())
    public Forecaster() {
        super();
        // TODO Auto-generated constructor stub
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
        response.getWriter().append("Served at :").append(request.getPathInfo());
    }

    @WebServlet(HttpServletRequest)
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
        // TODO Auto-generated method stub
        doPost(request, response);
    }
}
```
