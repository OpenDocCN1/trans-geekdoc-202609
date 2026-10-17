
### `TimerTask` 类

该类表示一个任务，该任务可以被 `Timer` 调度进行一次性或重复执行。可以使用 `cancel()` 方法取消 `TimerTask`。要执行的任务在 `TimerTask` 对象的抽象 `run()` 方法中实现。

## 6.4.4.5. 监控过程

当应用程序启动时，用户将看到图 6.44 所示的 GUI。点击“Monitor”按钮可以启动监控过程。点击 Monitor 按钮会触发 `monitorActionPerformed()` 方法，在该其中执行以下任务：

- 首先，通过验证布尔值 `monitoring` 的值检查监控过程的状态，以确定其已启动。
- 如果返回值为 false，则监控过程尚未启动。执行以下任务：
  - 使用默认的 `new Timer()` 构造函数初始化 `timer` 对象。
  - 使用 `new TimerTask()` 构造函数创建一个。该对象定义了 `Timer` 对象执行的任务。要执行的操作在 `TimerTask` 对象的抽象 `run()` 方法中定义。`TimerTask` 执行的操作在下文中进行了说明。
  - 使用 `JSOUP` 库从 API 获取数据。
  - 使用 `JSOUP` 类的 `connect()` 方法与 API 端点建立连接。使用 `get()` 方法获取 API 端点的 HTML 页面正文。将 `ignoreContentType()` 设置为 `true`，以便 `JSOUP` 在解析 HTML 文档时忽略内容类型。通过 `JSOUP` 获取的 `Document` 对象的 `.text()` 方法获取 API 响应的字符串表示。

# 云端实时数据采集与客户端架构 ... 655

b) 使用传入的数据更新图表

为了使用获取的气气读数更新图表，首先需要将字符串响应转换为 `JSONObject`。这是通过 `new JSONObject(String JSON)` 构造函数完成的，该构造函数接受有效的 `JSONObject` 字符串表示。创建 `JSONObject` 后，使用与 6.3.16 中相同的方法提取所需值。在提取所需值后，创建一个新的 `JSONObject` 并填充提取出的值。在 `JSONObject` 中添加一个新时间戳以标记其创建时间。为了更新图表，使用 `getDouble(String key)` 方法从新的 `JSONObject` 中获取所需的读数。将当前选定的变量添加到 `XYSeries` 数组中，并使用 `add(double x, y)` 方法增加计数器。

c) 将数据发送到云端数据库

从 API 获取数据后，需要将数据发送到本地服务器或云端数据库。使用 `if-else` 语句检查 `cloud_save` 复选框是否被选中。如果选中，则将数据发送到云端。要将数据发送到云端数据库，调用 `sendData(JSONObject JSON)` 方法并将新创建的 `JSONObject` 作为参数传递。如果复选框未勾选，则通过 `address_f` `JTextField` 中输入的 IP 地址建立 socket 连接将数据发送到本地服务器。

iii. 然后，使用 `Timer` 的 `schedule(TimerTask, long delay, long period)` 方法调度每 N 毫秒定期执行的 `TimerTask`。该方法定义了要执行的 `TimerTask`、相对于上次执行时间的启动延迟以及连续任务执行之间的时间。

3. 如果监控过程已启动，则使用 `Timer` 的 `cancel()` 函数停止调度的任务。这将终止定时器并丢弃任何当前调度的任务。

`monitorActionPerformed` 方法的代码见代码列表 6.26。

```
private void monitorActionPerformed(java.awt.event.ActionEvent event) {
    if (monitoring) {
        final boolean saveCloud = cloud_save.isSelected();
        timer = new Timer();
        TimerTask timerTask = new TimerTask() {
            public void run() {
                try {
                    // 连接到 API 链接以获取网页内容（读数）
```

# 656 T. P. Fowdar, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonadon

```java
Document doc = Jsoup.connect(URL).ignoreContentType(true);
//获取此文档中的文本
String result = doc.text();
```

```java
/* 从 API 返回的字符串创建 JSON 对象：
从 JSONObject 中提取必要信息。
返回的 JSON 对象格式见第 6.3.15 节 */
JSONObject JSON = new JSONObject(result);
JSONObject main = JSON.getJSONObject("main");
JSONObject wind = JSON.getJSONObject("wind");
JSONObject cloud = JSON.getJSONObject("clouds");
```

```java
/* 使用 getDouble() 方法获取值
需要一个 String 作为键 */
double visibility = JSON.getDouble("visibility");
double cloudness = cloud.getDouble("all");
double temperature = main.getDouble("temp");
double humidity = main.getDouble("humidity");
double pressure = main.getDouble("pressure");
double w_speed = wind.getDouble("speed");
double w_direction = wind.getDouble("deg");
```

```java
// 创建一个仅包含所需读取器的 JSONObject
JSONObject weather_data = new JSONObject();
//向 JSONObject 添加一个新时间戳
Timestamp timestamp = new Timestamp(System.currentTimeMillis());
weather_data.put("Time", timestamp);
weather_data.put("Visibility", visibility);
weather_data.put("Cloudness", cloudness);
weather_data.put("Temperature", temperature);
weather_data.put("Humidity", humidity);
weather_data.put("Pressure", pressure);
weather_data.put("Wind Speed", w_speed);
weather_data.put("Wind Direction", w_direction);
```

```java
//获取 JComboBox 中选中的读数
double aDouble = weather_data.getDouble(parameter);
//用新读数更新图表
xy_series.add(++, aDouble);
```

```java
//验证是否勾选了保存到云端
if (saveCloud) {
//调用 sendData() 方法将数据传输到云端
sendData(weather_data);
} else {
// 如果开关被禁用，数据将设置为本地服务器。
// 从 address_fTextField 中提取 IP 地址
```

## 基于云的实时... 数据捕获主机与客户端架构 657

```java
String host = (address_f.getText());
//在输入的 IP 和端口 6000 上创建套字连接
Socket socket = new Socket(host, 6000);
//从 socket 输出流创建创建一个打印机
PrintWriter out = new PrintWriter(socket.getOutputStream());
//通过套字发送数据
out.println(weather_data);
// 刷新任何剩余数据
out.flush();
//关闭打印机
out.close();
//关闭 Socket 连接
socket.close();
    }
} catch (IOException exception) {
//记录发生的任何异常
    Logger.getLogger(MainFrame.class.getName()).log(Level.SEVERE, null, ex);
}
};
//调度每隔 N ms 执行一次的任务
timer.schedule(timer, 0, 1000);
//禁用保存到云端的复选框
cloud_save.setEnabled(false);
//更改 Monitor 按钮上的文本
monitor.setText("Stop Monitoring");
//将监控状态设置为 true
monitoring = true;
} else {
//终止此计时器并丢弃任何当前计划的任务
timer.cancel();
//更改 Monitor 按钮上的文本
monitor.setText("Monitor");
//将监控状态设置为 false
monitoring = false;
}
}
```

## 6.4.4.6. `sendData()` 方法

该方法用于将 `JSONObject` 保存到 `Cloudant` 数据库。它接受一个 `JSONObject` 作为参数。该方法的工作原理首先通过 URL 端点、用户名和密码连接到 `Cloudant` 平台。使用 `CloudClient` 对象建立连接。使用 `CloudantClient` 的 `database(String db, boolean create)` 方法连接到平台中的数据库。然后，构建一个查询来选择数据库中的所有数据并按降序排列。获取 `idx` 的最后一个值。`idx` 的值加 1 并添加到 `JSONObject` 中。该 `JSONObject`

# 658 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonman

被保存到数据库并关闭连接。此操作的代码显示在列表 6.27 中。

### 列表 6.27. `sendData` 方法

```java
public void sendData(JSONObject currentReadings) {
  try {
    /* 将数据发送到数据库.*/
    CloudantClient client = ClientBuilder.URL(new URL(
      ("/ic3ce0434f-ab39-4abf-a854-5532a64d1f89-bluemixcloud.com/"))
    ).username("apikey-ec10b30de78974b57ab57b516f949965093")
    .password("69385274f8ec7098c35f032fbc7ef4606fb").build();
    /* 连接到 weather_data 数据库的数据库 API 实现
       创建 flag - 设置为 false以便如果数据库不存在则不创建。*/
    Database database = client.database("weather_data", false);
// 选择所有数据并按 idx 降序排序的查询字符串表示
    final String query = "{\"selector\":{\"idx\":{\$gt 0}},\"sort\":{\"idx\":desc}}";
    // 在选定的数据库 "weather_data" 上执行查询
    QueryResult-LinkedTreeMap queryResult = database.query(query, LinkedTreeMap.class);
    // 获取与查询匹配的文档列表
    List-LinkedTreeMap resultList = query.getDocs();
    // 如果数据库为空，idx 的值返回 1
    double idx = (resultList.size() > 0) ? (double) resultList.get(0).get("idx") : 1;
    // 将 idx 加 1 并添加到 JSONObject
    currentReadings.put("idx", idx + 1);
    // 将 JSONObject 保存到数据库
    database.save(currentReadings.toMap());
    //关闭与 Cloudant 数据库的连接
    client.shutdown();
  } catch (MalformedURLException ex) {
    Logger.getLogger(MainFrame.class.getName()).log(Level.SEVERE, null, ex);
  }
}
```

## 基于云的实时... 数据捕获与客户端架构 659

### 6.4.4.7. `analyticsCloud()` 方法

为了查询 Java 服务器获取结果，需要在 `JTextField` 中输入窗口大小和预测时间。然后按下 predict 按钮并调用 `ActionPerformed()` 方法。如果 `"src_cloud"` 的值为 true，则从云端获取分析数据，否则联系托管在客户端的 servlet。

为了查询本地服务器获取预报结果，首先在用户在端口 1111 上输入的 IP 地址上打开套接字连接。创建一个 `JSONObject` 来存储用户输入的请求类型、窗口大小和预测时间。将 `JSONObject` 发送到服务器。服务器处理请求并以 `JSONObject` 的形式返回分析结果。从 `JSONObject` 中提取数据，使用 `getData()` 方法将其格式化为可读格式并显示在 `TextView` 中。

### 列表 6.28. 查询 Java Servlet

```java
public void analyticsCloud() {
    //启动匿名线程从云端请求分析数据
    new Thread(() -> {
        try {
            //连接到 URL
            String host = "https://bluemix.net?"
                + "&prediction_time=" + ptime.getText()
                + "&window_size=" + window.getText();
            //从云端获取数据
            Document doc = Jsoup.connect(host).ignoreContentType(true).get();
            //在 TextArea 中显示数据
            String analytics = doc.text();
            result.setText(analytics);
        } catch (IOException e) {
            //打印错误
            System.out.println(e);
        }
    }).start();
}
```

#660 T. P. Fowder, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondon

## 6.4.4.8. `requestLocal()` 方法

为了查询 Java 服务器获取结果，需要在 `JTextField` 中输入窗口大小和预测时间。然后按下 predict 按钮并调用 `ActionPerformed()` 方法。如果 `"src_local"` 的值为 true，则从本地服务器获取分析数据，否则联系托管在客户端的 servlet。

为了查询本地服务器获取预报结果，首先在用户在端口 1111 上输入的 IP 地址上打开套接字连接。创建一个 `JSONObject` 来存储用户输入的请求类型、窗口大小和预测时间。将 `JSONObject` 发送到服务器。服务器处理请求并以 `JSONObject` 的形式返回分析结果。从 `JSONObject` 中提取数据，使用 `getData()` 方法将其格式化为可读格式并显示在 `TextView` 中。

### 列表 6.29. `requestLocal` 方法
