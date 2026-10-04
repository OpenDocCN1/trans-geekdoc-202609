

```java
if (dataSource.equals("localhost")) {
    if (String.valueOf(timestamp[i]).contains(convertedDate.toString())) {
        values = String.valueOf(timestamp[i]) + "," +
        String.valueOf(downspeed[i]) + "," + String.valueOf(upspeed[i]) + "," +
        String.valueOf(pacRec[i]) + "," + String.valueOf(pacSent[i]) + "," +
        String.valueOf(mobSpeed[i]) + "," + String.valueOf(mobUspeed[i]) + "," +
        String.valueOf(wstrength[i]) + "," + "in";
    }
}
// 从 HttpServletResponse 获取一个 PrintWriter 对象
PrintWriter out = response.getWriter();
// 允许跨域请求（允许 CORS 策略）以允许来自所有
// 域调用，这样浏览器就不会阻止请求
response.setHeader("Access-Control-Allow-Origin", "*");
// 创建一个 JSONObject 来存储数据
JSONObject result = new JSONObject();
// 将字符串放入 JSONObject 中
result.put("csv", values);
// 将 JSONObject 发送到客户端（网页）
out.print(result);
out.flush();
out.close();
System.out.println("Data sent");
```

## 5.3.7. 用于网络监控与分析的 Web 客户端

本节包含两个网页的开发，分别用于 PC 和 Android 设备的分析。这些页面使用 HTML、JavaScript 和 CSS 构建，并在 Eclipse 上作为动态 Web 项目托管，并使用第 5.4 节中的 servlets。如前所述，用户可以在托管在 IBM Bluemix 服务器上的网页上执行与本地服务器、桌面和 Android 相似的功能。首先创建了两个 HTML 页面并将它们添加到第 5.4 节创建的动态 Web 项目中。这些标记为“index1.html 和 index2.html”的页面分别代表 PC 和 Android 设备的页面。这意味着，要下载 PC 网络参数、执行分析并查看实时监控，可以通过“networkcloud-eu-gb.mybluemix.net/index1.html.” 访问网页。

图 5.55 显示了为“index1.html” 设计的界面，可以使用下拉菜单来导航参数的选择以及显示的数据源。如果使用 localhost 进行分析，可以输入本地服务器的 IP 地址。这样，网页就可以从浏览器

# 基于云的实时 . 服务器和 Servlet 架构 运行在手机上时，则使用运行服务器的 PC 的 IP 地址。但是，这两个设备必须连接到同一个网络。

对于 Android 页面“index2.html”，复制了相同的布局，除了相同的实时图表和下载选项外，还兼顾了 Wi-Fi 和 LTE 分类分析。这如图 5.57 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_564_0.png)

图 5.56. index1.html 的网页布局。

![](img/2b52fde0e707e8c2f05a10309c3f8982_564_1.png)

图 5.57. index2.html 的网页布局。

554 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoondonon

### 5.3.7.1. 创建 index1.html 和 index1.js

此步骤位于第 5.3.1 节创建的“NetworkCloud”动态 Web 项目之后。为了在动态 Web 项目中创建新的 HTML 文件，对“WebContent”文件夹点击右键，并选择一个新的 HTML 文件，如图 5.58 所示。这确保了文件可以在无需任何模式映射的情况下，通过 IBM Bluemix 上的托管 URL 访问。

![](img/2b52fde0e707e8c2f05a10309c3f8982_565_0.png)

图 5.58. 在 web 项目中创建“index1.js”。

同样，“index1.js” 带有使用 Fetch API 触发 servlet 的 JavaScript 代码。可以通过右键点击“New”并选择“File”，在弹出菜单中指定“index1.js”来创建，如图 5.59 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_565_1.png)

图 5.59. 在 web 项目中创建 JS 文件。

# 基于云的实时 . 服务器和 Servlet 架构

本节可以分为以下两个部分：

- 在 index1.html 中添加布局的 HTML 代码，例如字段、折线图和按钮。
- 在 index1.js 中添加使用 Fetch API 触发 servlet 的 JavaScript 代码。

将按照后续节中的步骤来创建页面，并确保为用户提供友好的方法。

### 5.3.7.2. 为 index1.html 添加 HTML 代码

对默认文档进行编辑，首先为了适应 jQuery 库 [19] 以及作为折线图库的 CanvasJS [20]。前者用于下拉菜单的动态使用。列表 5.54 代表了 index1.html 的 HTML 代码。可以观察到，它在 <head> 标签中引用了位于同一目录下的“index1.js”标签。

> 列表 5.54. index1.html 的 HTML 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
<!-- 指明页面标题-->
<title>Network Cloud Analytics</title>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<script
src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script type="text/javascript" src="index1.js"></script>
</head>

<body>
<!-- 添加一个居中的表格-->
<div class="table-responsive">
<table class="table" style="margin-left: auto; margin-right: auto;">
<tbody>
<tr>
<td>
<nav class="navbar navbar-default">
<div class="container-fluid">
<div class="navbar-header">
<!-- 指明网页的名称-->
<a class="navbar-brand" href="#" style="width:100px">Network Cloud
Analytics
</a>
</nav>
<div class="container">
<!-- PC -->
<div class="table-responsive">
<table class="table" style="margin-left: auto; margin-right: auto;">
<tbody>
<tr>
<td>
<!-- 这里的 IP 地址 -->
<div class="table-responsive">
<table class="table" style="margin-left: auto; margin-right: auto;">
<tbody>
<tr>
<td>
<!-- 这里的 IP 地址 -->
<div class="table-responsive">
```

```html

<!-- 指明实时图表的空间，来自 CanvasJS -->
<div id="chartContainer" style="height:370px; width: 100%;"></div>
<hr />
```

```html
# 基于云的实时 . 服务器和 Servlet 架构
```

```html
<td width="100%" id="dataset">
<table width="100%">
<tr>
<td width="300px" align="center">CLASSIFICATION ANALYSIS</td>
</tr>
</table>
</td>
</tr>
</tr>
</tr>
```

```html
<!-- 用于分类分析的字段和输入 -->
<div class="table-responsive">
<table class="table" style="margin-left: auto; margin-right: auto;">
<tbody>
<tr>
<td>
<b>Download Speed:</b>
<input class="form-control input-sm" id="downloadSpeed" type="text" size="200">
</tr>
<tr>
<td>
<b>Upload Speed:</b>
<input class="form-control input-sm" id="uploadSpeed" type="text" size="120">
</tr>
<tr>
<td>
<b>Packets received:</b>
<input class="form-control input-sm" id="packetsReceived" type="text" size="15" value="1500">
</tr>
<tr>
<td>
<b>Packets Sent:</b>
<input class="form-control input-sm" id="packetsSent" type="text" size="15" value="800">
</tr>
<tr>
<td>
<b>Activity - KNN:</b>
<input class="form-control input-sm" id="withKNNCC" type="text" size="15">
</tr>
<tr>
<td>
<b>Activity - MLP:</b>
<input class="form-control input-sm" id="withMLPC" type="text" size="15">
</tr>
<tr>
<td width="180px" align="right">
<!-- 添加分类按钮 -->
<button class="btn btn-primary" onclick="classify()">Classify</button>
</td>
</tr>
</tbody>
</table>
</div>
</div>
</body>
</html>
```

