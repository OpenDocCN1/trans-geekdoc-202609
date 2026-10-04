

# 504 T. P. Fowdur, L. Babooram, M. U-D-ibn Naz Rosun and M. Indoonondon

```java
if (greatestClass.doubleValue() == 3.0) {
    // Sending the values through the socket connection
    out.println("Client activity with KNN: streaming");
    out.flush();
    out.close();
}
MLPClassificationLTE(); // Performing MLP Classification
if (Math.round(classificationMLPLTE) == 1) {
    // Sending the values through the socket connection
    out.println("Client activity with MLP: idle");
    out.flush();
    out.close();
}
if (Math.round(classificationMLPLTE) == 2) {
    // Sending the values through the socket connection
    out.println("Client activity with MLP: browsing");
    out.flush();
    out.close();
}
if (Math.round(classificationMLPLTE) == 3) {
    // Sending the values through the socket connection
    out.println("Client activity with MLP: streaming");
    out.flush();
    out.close();
}
break;
```

列表 5.32 适用于 PC 边缘设备，其请求代码从六到九不等，对应表 4.7。

# 列表 5.32. PC 边缘设备的本地下载与分析

```java
// PC - Download to csv by N samples
case 6:
// Set the fetching for PC regression values to true
fetchRegressionPC = true;
// Fetching all values from the local PC database
fetchRegressionValuesPC();
// Getting the length from the JSONObject from the PC device
length = readings.getDouble("lengthSamples");
System.out.println("Length of samples: " + length);
// Calculating the initial value so that only the last N parameters are ordered
initial = (int)(numblets - length);
// Adding header in String object
csvStr = "Timestamp, Download Speed, Upload Speed, Packets Received, Packets
```

# 基于云的实时系统的服务器与 Servlet 架构。

```java
Sent = "\n";
// For loop list N parameters until end of database
for (int i = initial; i < numbitems; i++) {
    // Appending values to String object
csvStr = csvStr + String.valueOf(timestamp[i]).replace(",", " ") + ", " +
String.valueOf(downspeed[i]) + ", " + String.valueOf(upspeed[i]) + ", " +
String.valueOf(pacRec[i]) + ", " + String.valueOf(pacSent[i]) + ", " +
"\n";
}
System.out.println("Sending following through socket: " + csvStr);
// Sending the values through the socket connection
out.println(csvStr);
// Flushing the stream after each set
out.flush();
// Closing the socket connection
out.close();
break;
// PC - Download to csv by date
case 7:
    // Set the fetching for PC regression values to true
fetchRegressionPC = true;
// Fetching the values from the local database
fetchRegressionValues();
// Getting the data from the JSONObject from the PC device
date = readings.getString("date");
// Conversion of date to yyyy-mm-dd to match format of MySQL
formatter = DateTimeFormatter.ofPattern("MMM d, yyyy", Locale.ENGLISH);
convertedDate = LocalDate.parse(date, formatter);
// Adding header containing 5 variables
csvStr = "Timestamp, Download Speed, Upload Speed, Packets Received, Packets Sent " + ",";
for (int i = 0; i < numbitems; i++) {
    // Appending values if they consist to the desired date
if (String.valueOf(timestamp[i]).contains(convertedDate.toString())) {
csvStr = csvStr + String.valueOf(timestamp[i]) + ", " +
String.valueOf(downspeed[i]) + ", " + String.valueOf(upspeed[i]) + ", " +
String.valueOf(pacRec[i]) + ", " +
"\n";
}
System.out.println("Sending following through socket: " + csvStr);
// Sending the values through the socket connection
out.println(csvStr);
// Flushing the stream after each set
out.flush();
// Closing the socket connection
```

```java
out.close();
break;
// PC - Regression analytics
case 8:
// Fetching the parameters for regression from PC device
predictionTime = readings.getInt("predictionTime");
windowSize = readings.getInt("windowSize");
// Set the fetching for PC regression values to true
fetchRegressionPC = true;
// Fetching regression values for PC
fetchRegressionValuesPC();
localhostRegression = true;
MLPRegression(); // Performing MLP Regression
System.out.println("Sending flow through socket: " + mlrPrediction + "\n" + mlPrediction());
// Sending the values through the socket connection
out.println("Packets received with MLR: " + Math.round(mlrPrediction) + "\n" + \
```

```java
if (greatestClass.doubleValue() == 2.0) {
    // Sending the values through the socket connection
    out.println("Client activity with KNN: browsing");
    out.flush();
    out.close();
}
if (greatestClass.doubleValue() == 3.0) {
    // Sending the values through the socket connection
    out.println("Client activity with KNN: streaming");
    out.flush();
    out.close();
}
MLPClassification(); // Performing MLP Classification
if (Math.round(classificationMLP) == 1) {
    // Sending the values through the socket connection
    out.println("Client activity with MLP: idle");
    out.flush();
    out.close();
}
if (Math.round(classificationMLP) == 2) {
    // Sending the values through the socket connection
    out.println("Client activity with MLP: browsing");
    out.flush();
    out.close();
}
if (Math.round(classificationMLP) == 3) {
    // Sending the values through the socket connection
    out.println("Client activity with MLP: streaming");
    out.flush();
    out.close();
}
break;
```

## 5.1.15. 使 GUI 更加友好

由于 Android 设备具有两个用于分类的数据库，分别涉及 Wi-Fi 参数或 LTE 值，这两者在分类过程中都是可用的，因此通过在 `useMobiledataValues` 单选框和 `analysisDevice` 组合框上设置 `ActionPerformed` 事件来使 GUI 具有交互性。详细信息请见以下方法。

- *useMobiledataValuesActionPerformed() 方法执行如图所示的功能，通过启用和禁用相应的 JTextField 实现。*

508 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonundur

# 分析

![](img/2b52fde0e707e8c2f05a10309c3f8982_519_0.png)

图 5.20. 仅选择 PC 值。

# 分析

![](img/2b52fde0e707e8c2f05a10309c3f8982_519_1.png)

图 5.21. 选择带有 Wi-Fi 的 Android 值。

# 基于云的实时系统的服务器与 Servlet 架构。

![](img/2b52fde0e707e8c2f05a10309c3f8982_520_0.png)

图 5.22. 选择带有 LTE 的 Android 值。

上述过程的代码如下：

# 列表 5.33. 通过 LTE 切换设置字段

```java
private void useMobileValuesActionPerformed(java.awt.event.ActionEvent event) {
    if (useMobileValues.isSelected()) {
        mobspeed.setEnabled(true);
        mobuspeed.setEnabled(true);
        tdspeed.setEnabled(false);
        tuspeed.setEnabled(false);
    } else {
        mobspeed.setEnabled(false);
        mobuspeed.setEnabled(false);
        tdspeed.setEnabled(true);
        tuspeed.setEnabled(true);
    }
}
```

- *2. 同样，analysisDeviceActionPerformed() 方法如列表 5.34所示。*

510 T. P. Fowdur, L. Babooram, M. N-D-Ibn Naz Rosun and M. Indoonon

# 列表 5.34. 通过数据源切换设置字段

```java
private void analysisDeviceActionPerformed(java.awt.event.ActionEvent evt) {
    if (analysisDevice.getSelectedItem().toString().equals("PC")) {
        useMobileDataValues.setEnabled(false);
        mobspeed.setEnabled(false);
        mobuspeed.setEnabled(false);
        tdspeed.setEnabled(true);
        tuspeed.setEnabled(true);
    }
    if (analysisDevice.getSelectedItem().toString().equals("Android")) {
        useMobileDataValues.setEnabled(true);
    }
}
```

- *3. 下一方法对应于当 parameterSelectionJComboBox 检测到参数任何变化时清空实时图表*

# 列表 5.35. 参数更改时清空图形

```java
private void parameterSelectionActionPerformed(java.awt.event.ActionEvent evt) {
    // 检测到参数变化时清空图形
    series.clear();
}
```

## 5.2. 测试本地服务器

如图 5.2 所示的本地服务器具有完整的 GUI，本节包含了软件操作的逐步说明。

### 5.2.1. 本地实时监控

- *1. 在启动服务器之前，“选择边缘设备”下拉菜单用于选择从哪个设备接收值，如如图 5.23 所示。*


