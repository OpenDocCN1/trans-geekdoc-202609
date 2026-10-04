

## 基于云的实时系统服务器与 Servlet 架构

| 回归分析 | |
| :--- | :--- |
| 预测时间: | 10 |
| 窗口大小: | 20 |
| 接收包数 RK - MLR: | |
| 发包数 RX - MLP: | |

| 下载为 CSV | |
| :--- | :--- |
| 下载最后 N 个: | 10 |
| 按日期下载: | 2020年12月17日 |

### 5.3.7.3. 为 index1.js 添加 JavaScript 方法

前所述，JavaScript 用于显示从 Servlet 获取的值，同时由后者来执行分析工作。JavaScript 代码包含在 "index1.js" 文件。表 5.20 显示了定义的方法：

# 表 5.20.index1.js 的 JavaScript 方法描述

| 方法 | 描述 |
| :--- | :--- |
| classification(n) | 点击“Classify”（分类）按钮时，查询 Servlet 或 localhost，以返回 KNN 和 MLP 分类的分析值。 |
| regression() | 点击“Predict”（预测）按钮时，查询 Servlet 或 localhost，以返回 MLP 和 MLP 回归的分析值。 |
| window.onload | 在整个页面加载后立即调用，表示折线图的开始，该图每五秒从 Cloudant 或 MySQL 数据库中获取最后一组值。 |
| refreshGraph() | 当折线图的参数选择更改时调用，以便将选择参数显示在图表中。 |
| downloadLast(N) | 在输入要下载的样本数量后点击“Download”（下载）按钮时，查询 Servlet 或 localhost，返回一个包含用于解析 .csv 文件的 String 参数的 JSONObject。 |
| downloadByDate() | 在输入要下载的特定日期后点击“Download”（下载）按钮时，查询 Servlet 或 localhost。返回一个包含 JSONObject 中封装的 String 参数的 .csv 文件。 |

需要注意的是，表 5.20 中提到的所有方法都使用了 JavaScript 中可用的 Fetch API，在点击相应按钮时查询 Servlet。

表 5.20 中的方法将在以下步骤中详细说明并编写代码：

- 1. 由“Classify”和“Predict”按钮调用的 `classification()` 和 `regression()` 方法通过代码列表 5.55 构建，其中使用 Fetch API 查询 Servlet 或本地服务器（如 Apache Tomcat [21]），该服务器可以在 Eclipse 内部设置。使用 `json()` 方法以 JSON 对象的形式获取响应。在页面上打印结果之前，通过指定用于引用的 String，将来自 Servlet 的特定结果检索到变量中。

# 代码列表 5.55.index1.js 的分析方法

```javascript
function classification() {
  // 在显示框中设置提示
  document.getElementById("withNC").value = "Please wait...";
  document.getElementById("withPC").value = "Please wait...";

  // 从页面获取取值
  var downloadSpeed = document.getElementById("downloadSpeed").value;
  var uploadSpeed = document.getElementById("uploadSpeed").value;
  var packetsReceived = document.getElementById("packetsReceived").value;
  var packetsSent = document.getElementById("packetsSent").value;
  // 从云或本地获取选定的源
  var selectedSource = sourceSelection.options[sourceSelection.selectedIndex].innerHTML;
  // 如果选择了切换器，则获取 localhost 的 IP 地址
  var ipAddress = "" + document.getElementById("serverAddress").value;

  var query;
  // 选择源为“Cloudant database”
  if(selectedSource === "Cloudant database") {
    query = "https://networkcloud.eu-gb.bluemix.net/ml?downloadSpeed=" + downloadSpeed + "&uploadSpeed=" + uploadSpeed + "&packetsReceived=" + packetsReceived + "&packetsSent=" + packetsSent + "&predictionTime=10&windowSize=20&device=1&action=2&source=1";
  }
  // 选择源为“Local host”
  if(selectedSource === "Local host") {
    query = "http://" + ipAddress + ":8080/NetworkCloud/ml?downloadSpeed=" + downloadSpeed + "&uploadSpeed=" + uploadSpeed + "&packetsReceived=" + packetsReceived + "&packetsSent=" + packetsSent + "&predictionTime=10&windowSize=20&device=1&action=2&source=2";
  }
}

// 使用 Fetch API 查询 "networkCloudServlet"
fetch(query).then(function(response) {
  return response.json();
}).then(function(data) {
  console.log(data);
  // 从 JSON 响应中获取变量
  var knnResult = data.knnClassification;
  console.log("KNN RESULT: " + knnResult);

  var mlpResult = data.mlpClassification;
  console.log("MLP RESULT: " + mlpResult);

  // 在适当的结果框中打印变量
  document.getElementById("withNC").value = knnResult;
  document.getElementById("withPC").value = mlpResult;
}).catch(function(error) {
  console.log("Error in retrieving");
});

function regression() {
  // 在显示框中设置提示
  document.getElementById("withRR").value = "Please wait...";
  document.getElementById("withPR").value = "Please wait...";

  // 从页面获取取值
  var predictionTime = document.getElementById("predictionTime").value;
  var windowSize = document.getElementById("windowSize").value;
  // ... (其余回归逻辑如下)
}
```

