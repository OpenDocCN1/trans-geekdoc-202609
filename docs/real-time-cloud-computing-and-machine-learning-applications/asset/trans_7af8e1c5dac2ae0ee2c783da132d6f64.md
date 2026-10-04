

# 基于云的实时服务器与 Servlet 架构

```java
resultSet.next(); // 移动到条记录
// 将 List 对象写入选定的目标
CSVWriter csvWriter = new FileWriter(finalPath);
csvWriter.writeAll(records); // 写入记录
csvWriter.close(); // 关闭流
csvWriter.flush(); // 刷新流
}
// 如果选定的设备是 Android 设备
if (downloadDevice.getSelectedItem().toString().equals("Android")) {
    // 获取 N 个
    double length = Double.parseDouble(lastN.getText().toString());
    // 从本地数据库为 Android 获取所有所有值
    ResultSet resultSet = null;
    try {
        Class.forName("com.mysql.jdbc.Driver");
        Connection m_Connection = (Connection) DriverManager.getConnection("jdbc:mysql://localhost:3306/network", "root", "");
        Statement m_Statement = new Statement(m_Connection);
        m_Connection.createStatement();
        String query = "SELECT * FROM androidregression";
        resultSet = m_Statement.executeQuery(query);
    } catch (ClassNotFoundException | SQLException ex) {
        Logger.getLogger(LoCServer.class).log(Level.SEVERE, null, ex);
    }
    // 创建包含数组字符串的列表
List<String> records = new ArrayList<>();
// 添加表头记录
records.add(new String[]{
    "Timestamp",
    "Download Speed",
    "Upload Speed",
    "Packets Received",
    "Packets Sent",
    "MobileDownloadSpeed",
    "MobileUloadSpeed"
});
fetchArea.add("Timestamp, " + "Download Speed, " + "Upload Speed, " + "Packets Received, " + "Packets Sent, " + "Mobile Download Speed, " + "Mobile Upload Speed, " + "Wifi Strength, " + "in,");
// 计算初始值以便仅存储最后 N 个参数
int initial = (int) (numitems - length);
resultSet.absolute(initial); // 将光标移动到最后 N 个的开头
```

```java
// 循环遍历列表 N 个参数
for (int i = initial; i < resultSet.getFetchSize(); i++) {
    // 将值添加到 records 对象中保存到 csv
    records.add(new String[]{
        String.valueOf(resultSet.getString(9)),
        String.valueOf(resultSet.getString(2)),
        String.valueOf(resultSet.getString(3)),
        String.valueOf(resultSet.getString(4)),
        String.valueOf(resultSet.getString(5)),
        String.valueOf(resultSet.getString(6)),
        String.valueOf(resultSet.getString(7)),
        String.valueOf(resultSet.getString(8))
    });
    // 使用获取到的值更新 UI
    fetchArea.append(String.valueOf(resultSet.getString(9)) +
        "" + " + String.valueOf(resultSet.getString(2)) + "" + " + +
        String.valueOf(resultSet.getString(3)) + "" + " + +
        String.valueOf(resultSet.getString(4)) + "" + " + +
        String.valueOf(resultSet.getString(5)) + "" + " + +
        String.valueOf(resultSet.getString(6)) + "" + " + +
        String.valueOf(resultSet.getString(7)) + "" + " + +
        String.valueOf(resultSet.getString(8)) + ""\n");
    resultSet.next(); // 移动到下一条记录
}
// 将 List 写入选定的目标
CSVWriter csvWriter = new CSVWriter(new FileWriter(filepath));
csvWriter.writeAll(records); // 写入记录
csvWriter.close(); // 关闭流
csvWriter.flush(); // 刷新流
}
} catch (Exception ex) {
    java.util.logging.Logger.getLogger(LogServer.class.getName()).log(
        Level.SEVERE, null, ex);
}
}
```

接下来，根据 “localhostDownload” 切换的选择，调用列表 5.23 和 5.24 中定义的线程，这区分了从 Cloudant 数据库或本地下载。列表 5.25 也放置在 `downloadButtonActionPerformed(method)` 方法中。

# 基于云的实时服务器与 Servlet 架构

# 列表 5.25. 根据最后 N 个样本调用下载线程

```java
if (localhostDownload.isSelected()) {
  // 启动本地值的线程
  Thread downloadParameters = new Thread(downloadLocal);
  downloadParameters.start();
} else {
  // 启动 Cloudant 数据库值的线程
  Thread downloadParameters = new Thread(downloadLocal);
  downloadParameters.start();
}
```

# 5.1.13.2. 按特定日期下载按钮

从用户输入的日期下载 .csv 文件的实现遵循第 4.4.12.3 节中桌面应用程序的相同原理。

- 5. 文件名首先在列表 5.26 中创建。对于从本地获取数据，由于日期格式的细微差异，还根据用户输入的日期创建了相应的日期格式。这是使用 `DateTimeFormatter` 类并指定输入日期的格式来实现的。

# 列表 5.26. 为特定日期下载创建自动名称

```java
private void downloadDateButtonActionPerformed(java.awt.event.ActionEvent event) {
  // 用户在下载前输入日期并选择目标
  if (path.equals("") || date.toString().equals("")) {
    System.out.println("请浏览路径并输入日期。");
  } else {
    // 根据数量创建自动名称
    filename = date.toString() + "_" + count;
    // 为文件名添加 .csv 扩展
    finalpath = path + filename + ".csv";
    // 打印完整路径
    System.out.println("File path: " + finalpath);
    // 分割日期
    String[] splits = date.toString().split("_");
    String type1 = splits[0];
    String type2 = splits[1];
    // 转换为 yyyy-mm-dd
    DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd", Locale.ENGLISH);
    LocalDate convertedDate = LocalDate.parse(date, formatter);
    // 代表内容的变量
    System.out.println("Date: " + convertedDate);

# 列表 27. 按特定日期下载的线程

Runnable download = new Runnable() {
  @Override
public void run() {
    // 点击按钮时清除区域
    fetchArea.setText("");
    // 如果选定的设备是 PC
    if (downloadDevice.getSelectedItem().toString().equals("PC")) {
      fetchRegressionValues();
      // 将列表转换为数组
      List<String[]> records = new ArrayList<>();
      // 添加表头
      records.add(new String[]{"Timestamp", "Download Speed", "Upload Speed", "Packets Received", "Packets Sent"});
      // 追加到区域
      fetchArea.append("Timestamp, " + "Download Speed, " + "Upload Speed, " + "Packets Received, " + "Packets Sent" + "\n");
      // 循环所有参数
      for (int i = 0; i < numitems; i++) {
        // 将数据与时间戳中的单个值比较
        if (String.valueOf(timestamp[i]).contains(type1) ||
            String.valueOf(timestamp[i]).contains(type2)) {
          records.add(new String[] {
            String.valueOf(timestamp[i]),
            String.valueOf(downspeed[i]),
            String.valueOf(upspeed[i]),
            String.valueOf(pacRec[i]),
            String.valueOf(pacSent[i])
          });
        }
      }
      # 将每个值打印到 JTextArea
      resultArea.append(String.valueOf(timestamp[i]) + ", \n" +
        String.valueOf(downspeed[i]) + ", \n" +
        String.valueOf(upspeed[i]) + ", \n" +
        String.valueOf(pacRec[i]) + ", \n" +
        String.valueOf(pacSent[i]) + "\n");
    }
    // 检查是否存在特定日期的记录
    if (records.size() <= 1) {
      // 没有记录
      resultArea.setText("No records found for this date.");
      resultArea.append("No records found for this date.");
    } else {
      // 将 List 写入存在的记录记录
      CSVWriter csvWriter = new CSVWriter(new FileWriter(filepath));
      csvWriter.writeAll(records); // 写入记录
      csvWriter.close(); // 关闭流
      csvWriter.flush(); // 刷新流
    }
  }
};
```

