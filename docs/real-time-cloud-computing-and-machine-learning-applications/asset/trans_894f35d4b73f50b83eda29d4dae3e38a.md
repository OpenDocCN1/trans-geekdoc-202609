

# 云端实时系统的服务器与 Servlet 架构

并以 JSON 响应的形式返回分类。表 5.17 概述了涉及的 Servlet 及其相应的描述。还给出了 URL 映射，并在文档中进一步引用。

## 表 5.17. Servlet 类概览

| Servlet Java 类 | URL 映射 | 描述 |
|---|---|---|
| networkCloudServlet | ml | 执行分析并以 JSON 响应形式返回结果，写入页面 |
| livegraph | livegraph | 返回从 PC 和 Android 从云数据库获取的最后一组值 |
| livegraphAndroid | livegraphAndroid | 根据用户在网页上指定的批次进行获取，将 .csv 文件作为附件输出到页面供 PC 和 Android 使用 |
| downloadValues | downloader | 根据用户在网页上指定的批次获取值，将 .csv 文件作为附件输出到页面供 PC 和 Android 使用 |
| downloadValuesAndroid | downloaderAndroid | downloadDate downloaderDateAndroid |

上述类可以总结为图 5.42，该图是根据项目生成的统一建模语言 (UML) 图。这些类显示了第 5.1 节中本地服务器的描述方法，这些方法经过轻微修改后用于 Servlet。

![](img/2b52fde0e707e8c2f05a10309c3f8982_530_0.png)

PC 方法

Android 方法

图 5.42. Servlet 包的类和方法概览。

520 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondon

## 5.3.1. 在 Eclipse IDE 中创建动态 Web 项目

如前所述，动态 Web 项目同时持有 Java 类和网页文件。Eclipse IDE 适用于部署在 IBM Bluemix 服务器或如 Apache Tomcat 类的本地服务器上。可以在 [17] 找到它，必要的插件从 [18] 下载。通过以下步骤将 Cloud Foundry 的 Eclipse Tools 插件添加到 Eclipse 中：

- 1. 启动 Eclipse Marketplace，并通过“Help (帮助)”菜单访问，如图 5.43 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_531_0.png)

图 5.43. 访问 Eclipse Marketplace。

- 2. 图 5.44 显示了弹出的下一个窗口。

![](img/2b52fde0e707e8c2f05a10309c3f8982_531_1.png)

图 5.44. Eclipse Marketplace 菜单。

# 云端实时系统的服务器与 Servlet 架构

- 3. 使用搜索栏搜索“Eclipse Tools for Cloud Foundry”插件，并在图 5.45 中点击“Install (安装)”按钮将其添加到 IDE 中。它也可以在 [18] 找到。

![](img/2b52fde0e707e8c2f05a10309c3f8982_532_0.png)

图 5.45. 搜索 Eclipse Tools for Cloud Foundry。

- 4. 接受许可协议条款，并在图 5.46 的新窗口中点击“Finish (完成)”按钮。插件将被下载并添加到 Eclipse。

![](img/2b52fde0e707e8c2f05a10309c3f8982_532_1.png)

图 5.46. 接受许可协议。

522 T. P. Fowdar, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondon

动态 Web 项目的创建通过以下步骤完成：

- 1. 要创建一个新项目，在“File (文件)”标签页下选择“New (新建)”，然后点击“Dynamic Web Project (动态 Web 项目)”，如图 5.47 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_533_0.png)

图 5.47. 在 Eclipse IDE 中创建新的 Dynamic Web 项目。

- 2. 接下来在“Project name (项目名称)”条目下添加名称，并选择项目的默认位置。也可以设置目标运行时 (target runtime)。在这种情况下，用户可以选择“IBM Bluemix Runtime”，这样 servlet 在运行时将被部署在配置的云服务器上。然后如图 5.48 所示点击“Finish (完成)”按钮。

![](img/2b52fde0e707e8c2f05a10309c3f8982_533_1.png)

图 5.48. 配置 Web 项目详情。

# 云端实时系统的服务器与 Servlet 架构

- 3. 随后创建项目，并如图 5.49 所示在左侧面板中可用。

![](img/2b52fde0e707e8c2f05a10309c3f8982_534_0.png)

图 5.49. 创建的项目概览。

## 5.3.2.向项目添加库

由于 servlet 是本地服务器的托管版本，它包含了相同的方法，这些方法反过来需要第 5.1.4 节中详细说明的库。这些在表 5.8 中描述的库通过以下步骤添加：

- 1. 在左侧面板上，右键点击项目“NetworkCloud”，然后选择“Properties (属性)”选项，如图 5.50 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_534_1.png)

图 5.50. 编辑项目属性。

- 2. 打开图 5.51 所示的窗口，从左侧面板选择“Java Build Path (Java 构建路径)”，然后选择“Libraries (库)”选项卡。点击“Add External Libraries (添加外部库)”，

524 T. P. Fowdar, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonundan

在定位所有需要的 .jar 文件之前。在新窗口中点击“Order Export (导出)”，最后选择“Apply and Close (应用并关闭)”以确认库的选择。

![](img/2b52fde0e707e8c2f05a10309c3f8982_535_0.png)

图 5.51. 向项目添加库。

## 5.3.3. 创建分析 Servlet 类

此部分涉及通过请求-响应模型为分析创建 networkCloudServlet servlet。遵循以下步骤：

- 1. 右键点击项目“NetworkCloud”，选择“New (新建)”和“Servlet”选项，如图 5.52 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_535_1.png)

图 5.52. 创建新 Servlet。

# 云端实时系统的服务器与 Servlet 架构

- 2. 当图 5.53 弹出时，输入类名并选择“Next (下一步)”。

![](img/2b52fde0e707e8c2f05a10309c3f8982_536_0.png)

图 5.53. 添加类详情。

- 3. 下一个窗口涉及输入访问此 servlet 所需的 URL 映射。在这种情况下，编辑后者并输入“ml”作为模式，表示“机器学习”。然后点击“Finish (完成)”按钮。

![](img/2b52fde0e707e8c2f05a10309c3f8982_536_1.png)

图 5.54. 完成类的创建。

526 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondon

图 5.55 是编辑器中自动生成的代码段，即 networkCloudServlet.java 类。

```
1
import java.io.IOException;
2
3
/*
   Servlet 实现类 networkCloudServlet
 */
6
@WebServlet("/")
7 public class networkCloudServlet extends HttpServlet {
    private static final long serialVersionUID = -1L;
8
9
    /*
      构造函数
      */
10
    public networkCloudServlet() {
      super();
      // TODO: 自动生成的构造函数存根
    }
14
15
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
      // TODO: 自动生成方法
      response.getWriter().append("Served at: ").append(request.getPath());
    }
18
19
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws IOException {
      // TODO: 自动生成方法
      doGet(request, response);
    }
}
```

图 5.55. 自动创建方法的概览。

## 5.3.4. 构建分析 Servlet

如前所述，此 servlet 的功能是首先接收一个 GET 请求，通过 HTTP 请求附加变量，将 servlet 导向

