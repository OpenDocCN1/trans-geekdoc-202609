

强度，" + "\n, ");

```java
// 用于遍历 N 个参数的循环
for (int i = 0; i < numItems; i++) {
    if (String.valueOf(timestamp[i]).contains(type1) ||
        String.valueOf(timestamp[i]).contains(type2)) {
        records.add(new String[]{
            String.valueOf(timestamp[i]),
            String.valueOf(downspeed[i]),
            String.valueOf(upspeed[i]),
            String.valueOf(pacRec[i]),
            String.valueOf(pacSent[i]),
            String.valueOf(mobSpeed[i]),
            String.valueOf(mobUspeed[i]),
            String.valueOf(wstrength[i])
        });
        fetchArea.append(String.valueOf(timestamp[i]) + " " + 
                         String.valueOf(downspeed[i]) + " " + 
                         String.valueOf(upspeed[i]) + " " + 
                         String.valueOf(pacRec[i]) + " " + 
                         String.valueOf(pacSent[i]) + " " + 
                         String.valueOf(mobSpeed[i]) + " " + 
                         String.valueOf(mobUspeed[i]) + " " + 
                         String.valueOf(wstrength[i]) + "\n");
    }
}
if (records.size() == 1) {
    fetchArea.setText("");
    fetchArea.append("未找到该日期的记录。");
} else {
    // 将列表写入选择的位置
    CSVWriter csvWriter = new CSVWriter(new
    FileWriter(finalPath));
    csvWriter.writeAll(records); // 写入记录
    csvWriter.close(); // 关闭流
    csvWriter.flush(); // 刷新流
}
} catch (Exception ex) {
    java.util.logging.Logger.getLogger(LocServer.class.getName());
    log(Level.SEVERE, null, ex);
}
};
```

# 云端实时系统的服务器与 Servlet 架构 . 495

1. 列表 5.27 之后是 `Runnable` 线程的实现 `downloadLocalhost` 在下载到 `.csv` 文件之前，从 localhost 数据库中获取参数。如列表 5.28 所示。

# 列表 5.28. 从 localhost 下载特定日期的线程

```java
Runnable downloadLocalhost = new Runnable() {
@Override
public void run() {
  try {
    // 点击按钮时清除文本区域
    fetchArea.setText("");
    // 如果选定的设备是 PC 设备
    if (downloadDevice.getSelectedItem().toString().equals("PC")) {
      // 从 localhost 数据库获取 PC 的所有记录
      ResultSet resultSet = null;
      Class.forName("com.mysql.jdbc.Driver");
      Connection m_Connection = (Connection) DriverManager.getConnection("jdbc:mysql://localhost:3306/network"
```

# 496 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoonon

```java
String.valueOf(resultSet.getString(2)),
String.valueOf(resultSet.getString(3)),
String.valueOf(resultSet.getString(4)),
String.valueOf(resultSet.getString(5)));
// 使用获取的值更新 UI
fetchArea.append(resultSet.getString(6)) +
  """ + String.valueOf(resultSet.getString(2)) + """ +
  String.valueOf(resultSet.getString(3)) + """ +
  String.valueOf(resultSet.getString(4)) + """ +
  String.valueOf(resultSet.getString(5)) + "\n";
}

// 将对象写入选择的位置
CSVWriter csvWriter = new CSVWriter(new FileWriter(finalpath));
csvWriter.addAll(records); // 写入记录
csvWriter.close(); // 关闭流
csvWriter.flush(); // 刷新流
// 如果选定的设备是 Android 设备
if (downloadDevice.getSelectedItem().toString().equals("Android")) {
  // 从 localhost 数据库获取 Android 的所有数据
  ResultSet result = null;
try {
    Class.forName("com.mysql.jdbc.Driver");
    Connection M_Connection = (Connection) DriverManager.getConnection("jdbc:mysql://localhost:3306/network","root","password");
    Statement m_Statement = (Statement) m_Connection.createStatement();
    String query = "SELECT * FROM androidregression";
    result = m_Statement.executeQuery(query);
} catch (ClassNotFoundException | SQLException e) {
  Logger.getLogger(LogServer.class.getName()).log(Level.SEVERE, null, ex);
}
// 确保列表包含字符串数组
List<String[]> records = new ArrayList<>();
// 添加头部记录
records.add(new String[]{
  "时间戳",
  "下载速度",
  "上传速度",
  "接收到的数据包",
  "发送的数据包",
  "移动下载速度",
  "移动上传速度","Wifi 信号强度"
});
```

# 云端实时系统的服务器与 Servlet 架构 . 497

```java
fetchArea.append("Timestamp, " + "Download Speed, " + "
Upload Speed, " + "Packets Received, " + "Packets Sent, " +
"Mobile Download Speed, " + "Mobile Upload Speed, " + "Wifi
Strength, " + "\n",");
// 用于遍历 N 个参数的循环
while (resultSet != null && resultSet.next()) {
    if(String.valueOf(resultSet.next()).contains(type1)) {
        records.add(new String[]{
            String.valueOf(timestamp[i]),
            String.valueOf(downspeed[i]),
            String.valueOf(upspeed[i]),
            String.valueOf(pacRec[i]),
            String.valueOf(pacSent[i]),
            String.valueOf(mobSpeed[i]),
            String.valueOf(mobUspeed[i]),
            String.valueOf(wstrength[i])
        ]);
        fetchArea.append(String.valueOf(timestamp[i]) + " " + 
                         String.valueOf(downspeed[i]) + " " + 
                         String.valueOf(upspeed[i]) + " " + 
                         String.valueOf(pacRec[i]) + " " + 
                         String.valueOf(pacSent[i]) + " " + 
                         String.valueOf(mobSpeed[i]) + " " + 
                         String.valueOf(mobUspeed[i]) + " " + 
                         String.valueOf(wstrength[i]) + "\n");
    }
}
if (records.size() == 1) {
    fetchArea.setText("");
    fetchArea.append("未找到该日期的记录。");
} else {
    // 将列表写入选择的位置
    CSVWriter csvWriter = new CSVWriter(new
    FileWriter(finalPath));
    csvWriter.writeAll(records); // 写入记录
    csvWriter.close(); // 关闭流
    csvWriter.flush(); // 刷新流
}
} catch (Exception ex) {
    java.util.logging.Logger.getLogger(LocServer.class.getName());
    log(Level.SEVERE, null, ex);
}
};
```

# 498 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoonon

最后，列表 5.27 和 5.28 定义的线程在 `download()` 方法中调用，首先检查 `localhostDownload` 切换开关是否启用。

# 列表 5.29. 按日期下载的线程

```java
if (localhostDownload.isSelected()) {
  // 获取 localhost 数据的线程
  Thread downloadParameters = new Thread(downloadLocal);
  downloadParameters.start();
} else {
  // 获取 Cloudant 数据的线程
  Thread downloadParameters = new Thread(download);
  downloadParameters.start();
}
```

# 5.1.14. 本地下载与分析

除了从 Servlet 和 Cloudant 数据库提供下载和分析功能外，本地服务器利用“启动与分析”按钮启动 ServerSocket 连接，接受来自边缘设备的连接。后者通过请求代码（如表 4.3 和 4.7）向服务器提交请求。本地服务器执行所需的功能并向边缘设备返回响应。服务器与边缘设备之间通过 JSONObject 对象进行数据收传输。列表 5.30 显示了在端口 2002 上创建的客户端-服务器架构，以及处理不同请求代码的 switch-case 机制。列表 5.31 和 5.32 放置在 switch 语句中。

# 列表 5.30. 本地下载与分析的 ServerSocket

```java
public void launchLocalServerActionPerformed(java.awt.event.ActionEvent evt) {
  // 更新 GUI 状态
  serverStatus.setText("服务器状态：下载/分析服务器已启动");
  // 创建处理边缘设备请求的 Runnable
  Runnable localDAServer = new Runnable() {
    @Override
    public void run() {
      int requestCode; // 每次请求收到的请求代码
      double length; // 下载到 csv 的值长度
      String date; // 下载到 csv 的日期
      final int port = 2002; // 服务器创建端口
```

