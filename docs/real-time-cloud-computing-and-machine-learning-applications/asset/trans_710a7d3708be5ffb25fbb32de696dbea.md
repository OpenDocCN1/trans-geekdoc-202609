

# 列表 5.58. 通过最后 N 个样本下载参数

```javascript
function downloadLastN() {
// 从网页上获取下载的样本数量
  var downloadSamples =
  document.getElementById("downloadSamples").value;
// 从 Cloud 或 Localhost 获取源地址
  var selectedSource =
  sourceSelection.options[sourceSelection.selectedIndex].innerHTML;
// 如果选择了切换开关，则获取 localhost 的 IP 地址
  var ipAddress = "" + document.getElementById("serverAddress").value;
  var query = "传递给 Fetch调用的查询语句";
if(selectedSource === "Cloudant database") {
    query = "https://network.cloud-eu-gb.mybluemix.net/downloader?" + "number=" + downloadSamples + "&source=1";
}
if(selectedSource === "Local host") {
    query = "http://" + ipAddress + ":8080/NetworkCloud/downloader?" + "number=" + downloadSamples + "&source=2";
}
// 向选定的源发送查询
fetch(query);
  .then(res => res.json())
  .then((out) => {
// 获取 servlet 返回的字符串对象
  var csv_dat = out.csv;
  console.log(csv_dat);
// 创建元素以输出可下载的 .csv 文件
  var hiddenElement = document.createElement('a');
// 设置必要的元数据
  hiddenElement.href = 'data:text/csv;charset=utf-8,' + 
  encodeURI(csv_dat);
  hiddenElement.target = '_blank';
// 设置文件名
  hiddenElement.download = 'networkPCSamples.csv';
// 从浏览器中将 .csv 文件作为可下载文件输出
  hiddenElement.click();
}).catch(err => console.error(err));
}
```

- 5. 按日期下载样本，遵循了步骤 4 中解释的相同原理。downloadDate() 方法显示在列表 5.59 中。

# 基于云的实时服务器和 Servlet 架构

# 列表 5.59. 按日期下载参数

```javascript
function downloadDate() {
  // 从网页上获取样本名称
  var downloadDate = document.getElementById(`downloadDate`).value;
  // 从 Cloudant 或 Localhost 获取选定的源
  var selectedSource =
  sourceSelection.options[sourceSelection.selectedIndex].innerHTML;
  // 如果选择了 localhost，则获取 localhost 的 IP 地址
  var ipAddress = "" + document.getElementById(`serverAddress`).value;
  var query; // 传递给 fetch 调
  if(selectedSource === `Cloudant database`) {
    query = `https://networkcloud.eu.gb.blemix.net/downloaderDate?` +
    `date=` + downloadDate + `&source=1`;
  }
  else if(selectedSource === `Local host`) {
    query = `http://` + ipAddress + ":8080/NetworkCloud/downloaderDate?` +
    `date=` + downloadDate + `&source=2`;
  }
  // 向选定的源发送查询
  fetch(query)
    .then(res => res.json())
    .then((out) => {
      // 通过 servlet 获取字符串对象
      var csv_dat = out.csv;
      console.log(csv_dat);
      // 创建元素以输出可下载的 .csv 文件
      var hiddenElement = document.createElement('a');
      // 设置必要的元数据
      hiddenElement.href = 'data:text/csv;charset=utf-8,' +
      encodeURI(csv_dat);
      hiddenElement.target = '_blank';
      // 设置文件名
      hiddenElement.download = 'networkPCDate.csv';
      // 从浏览器中将 .csv 文件作为可下载文件输出
      hiddenElement.click();
    }).catch(err => console.error(err));
```

### 5.3.7.4. 创建 index2.html 和 index2.js

此页面根据 "index1.html" 适配而来，具有相同的功能，但它首先从 Cloudant 或 localhost 数据库获取总共七个参数用于实时图表。它还向用户显示了 Wi-Fi 和 LTE 能力。遵循了第 5.3.7.1 节提到的相同步骤，分别创建 "index2.html" 和 "index2.js" 文件。HTML 代码与 5.54 相同，但增加了用于 LTE 分析的新组件。"index2.html" 的代码已在书籍网站上提供。

在 JavaScript 中实现的分析方法与 "index1.js" 相同。但对于分类(n) 和回归(m) 方法，传递给 Fetch API 的 URL 中的 "device" 变量从 "1" 更改为 "2"，以表示 Android 设备。对于 LTE 分类，标记为 classification:LTE()的方法处理该过程，同时使用变量为 "3" 的 "device"。在其他方面遵循了相同的原理。这些代码也可以在书籍网站上找到。

添加了列表 5.56 中相同的 window.onload 方法，随后为 refreshGraph() 方法添加了三个额外参数。同样，这些代码在书籍网站上提供。

### 5.3.8. 在 IBM Bluemix 上托管 Java Servlet

在执行前几节描述的创建和填充 servlet 的步骤后，下一步是在 Eclipse 中使用 IBM Bluemix 插件。

- 1. 在左侧面板选择 "index1.html" 并右键点击。在下拉菜单中选择“运行方式 (Run As)",然后点击“服务器 (Server)”。

![](img/2b52fde0e70e8c2f05a10309c3f8982_581_0.png)

图 5.60. 从 Bluemix 服务器运行 HTML 文件。

- 2. 在图 5.60 的下一个窗口中，选择“手动定义新服务器 (Manually define a new server)”，选择“IBM Bluemix”。然后给出服务器名称。

![](img/2b52fde0e70e8c2f05a10309c3f8982_582_0.png)

图 5.61. 手动定义新服务器。

- 3. 在图 5.62 中输入登录凭据。

![](img/2b52fde0e70e8c2f05a10309c3f8982_582_1.png)

图 5.62. 登录凭据。

- 4. 在图 5.63 中，从可用列表中选择 "NetworkCloud" 项目。

![](img/2b52fde0e70e8c2f05a10309c3f8982_583_0.png)

图 5.63. 选择项目。

- 5. 在图 5.64 中，设置部署详情。

![](img/2b52fde0e70e8c2f05a10309c3f8982_584_0.png)

图 5.64. 部署详情。

- 6. 随后通过点击“完成 (Finish)”部署应用程序。

![](img/2b52fde0e70e8c2f05a10309c3f8982_584_1.png)

图 5.65. 部署应用程序。

- 7. 仪表板因此显示了已注册的资源。

| 资源摘要 | 查看全部 |
| :--- | :--- |
| 2 个资源 | |
| Cloud Foundry 应用 | 1 |
| 服务 | 1 |

图 5.67. 资源的仪表板。

