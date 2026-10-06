
- **按特定日期下载：** 将用户输入的特定格式日期作为输入，并使用 `fetchRegressionAndroid()` 方法本身获取参数。它将用户输入的日期与相同日期的记录进行比较，并将匹配项输出到 `.csv` 文件和界面上的 `resultArea` `TextView` 组件中。本地服务器使用带有“two”的 `requestCode`。

# 4.3.11.1. 全局变量

遵循 `MainActivity.java` 类的相同原则，布局组件通过首先在 `onCreate()` 之外声明它们来与后端链接。这如列表 4.42 所示。

> 列表 4.42. 在 `Download.java` 中声明全局变量

```java
package com.example.network_monitor_app;
// 导入 Android 库：
import android.content.Context;
import android.content.Intent;
import android.content.pm.PackageManager;
import android.os.Bundle;
import android.text.ScrollingMovementMethod;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.TextView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;

// 导入用于连接 Cloudant 的库； 
```

# 基于云的实时...数据采集与客户端架构 ... 315

```java
import com.cloudant.client.api.ClientBuilder;
import com.cloudant.client.api.CloudantClient;
import com.cloudant.client.api.Database;
import com.cloudant.client.api.query.QueryResult;
import com.codekildabs.storagechooser.StorageChooser;
import com.google.gson.internal.LinkedTreeMap;
// 导入处理 JSON 类的库：
import org.json.JSONException;
import org.json.JSONObject;
// 导入 Java 库：
import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.Socket;
import java.net.URL;
import java.util.ArrayList;
import java.util.List;
import java.util.logging.Level;
// 导入 OpenCV 库：
import au.com.bytecode.opencv.CSVWriter;

public class Download extends AppCompatActivity {
// 允许读写外部存储的权限代码：
p static final int FOLDERPICKER_PERMISSIONS = 1;

// 声明组件
Button JButton, downloadNButton, downloadCameraButton; // 用于导航应用程序的按钮
TextView fetchArea; // 打印获取值的区域
EditText lastField, dateField; // 代表 GUI 上最后 N 和日期的字段变量
RadioGroup dataSource; // 代表持有源选择的按钮组
RadioButton sourceSelection; // 代表在组上进行的源选择的变量
EditText ipaddress; // 如果使用本地主机 (XAMPP)，则输入 ip 地址的字段

// 用于从 Cloudant 数据库获取值的变量：
double keys[]; // Key
double downspeed[]; // Wi-Fi 下载速度
double uppeed[]; // Wi-Fi 上传速度
```

# 316 T. P. Fowdur, L. Bababoor, M. U-D-Ibn Nazir Rosun and M. Indoon

```java
double pac[]; // 接收到的包
double pacSent[]; // 发送的包
double mobSpeed[]; // LTE 下载速度
double mobUspeed[]; // LTE 上传速度
double wstring[]; // Wi-Fi 强度
String timestamp[]; // 每条记录的时间戳

// 操作 .csv 文件选择目录的变量：
String finalpath = ""; // 最终路径
String miniPath = ""; // 用户选择的目录
String filename = ""; // 根据用户创建的文件名

// XAMPP 连接本地托管数据库
String host = ""; // 从 GUI 获取的 IP 地址
final int port = 2002; // NetBeans IDE 运行的端口
// 本地服务器的代码
final JSONObject requestCode = new JSONObject();
// Cloudant 数据库连接变量：
CloudantClient client = null;
// 从 Cloudant 获取的项目数
double numItems = 0.0;
```

# 4.3.11. 在 onCreate() 中初始化组件

遵循 `MainActivity.java` 类的相同原则，通过首先在 `onCreate()` 之外声明组件来与后端链接。此方法涉及映射布局到类，以及相关的变量。这里也详细介绍了三个按钮。第一步是从 UI 检索组件，以便通过编程方式进行交互。

> 列表 443. 在 `Download.java` 的 `onCreate(Bundle)` 中初始化组件

```java
protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);

// 将此类的布局设置为 csvdownload 文件：
  ContentView(R.layout.csvdownload);

// 将创建的变量映射到相应的布局对象：
  fetchArea = (TextView) findViewById(R.id.resultArea);
  browseButton = findViewById(R.id.browseButton);
  downloadNButton = findViewById(R.id.downloadNButton);
  downloadDateButton = findViewById(R.id.downloadDateButton);
  lastNField = findViewById(R.id.lastN);
  dateField = findViewById(R.id.date);
  dataSource = findViewById(R.id.dataSource);
  ipaddress = findViewById(R.id.EDT1);
}
```

# 基于云的实时...数据采集与客户端架构 317

```java
// 设置包含打印值的区域的移动方式为滚动
fetchArea.setMovementMethod(new ScrollingMovementMethod());

// 禁用下载按钮开始：
// 需要用户首先浏览目录以启用按钮
downloadButton.setEnabled(false);
downloadDateButton.setEnabled(false);
// 包含列表 4.44 到 4.48
```

## 4.3.11.3. 浏览按钮

此按钮允许用户选择一个目录，以存储要下载的 `.csv` 文件。它使用一个创建的方法，命名为 `showDirectoryPicker()`，该方法首先验证读写外部存储的必要权限。`hasPermissions()` 方法在此处执行此检查，并触发目录选择器。

## 列表 4.44. 实现浏览功能

```java
// 点击“浏览 (Browse)”按钮时的操作：
browseButton.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        // 创建一个数组来存储所需的权限所需的 String 对象：
        String[] PERMISSIONS = {
            android.Manifest.permission.READ_EXTERNAL_STORAGE,
            android.Manifest.permission.WRITE_EXTERNAL_STORAGE
        };
        // 检查这些权限是否已被接受：
        if (hasPermissions(Download.this, PERMISSIONS)) {
            // 调用发布目录选择的方法：
            showDirectoryPicker();
        } else {
            // 如果尚未接受，则向用户提供允许必要的
            // 权限的选项：
            ContextCompat.requestPermissions(Download.this, PERMISSIONS,
            FOLDERPICKER_PERMISSIONS);
        }
    }
});
```

318 T. P. Fowdur, L. Babooram, M. N-U-D-ib Rosun and M. Indoondom

## 4.3.11.4. 下载最后 N 个样本按钮

定义在 `onCreate()` 内部，此按钮具有以下功能：

- 确定打印值数量的选择选项

- 根据单选按钮以及在单选按钮上选择的源创建自动文件名，即“Cloudant”或“Local（本地）”。

- 使用 `Runnable` 类创建两个线程，其中一个用于从 Cloudant 数据库获取过程，另一个用于从本地服务器获取。

“download” `Runnable` 线程可以描述如下：

- 使用 `List` 对象通过包含最后“N”条记录的 for 循环存储要发送的变量，并将变量类型转换为 String。

- 使用来自 OpenCSV 库 [14] 的 `CSVWriter` 类将 `List` 对象写入到之前选定的目标位置。

另一方面，“downloadlocalhost” `Runnable` 线程具有以下属性：

- 获取用户在 GUI 上输入的 IP 地址。

- 通过 `Socket` 连接到 NetBeans 上的本地服务器，使用一个请求代码为整数“1”的 `JSONObject`。

- 使用 `BufferedReader` 对象通过 `Socket` 对象的输入流接收来自本地服务器的输出。

- 使用 `PrintWriter` 对象将应用程序中的值写入使用“浏览”按钮选择的位置的 `.csv` 文件中。

这在列表 4.45 中执行如下。

## 列表 4.45. 下载最后 N 个样本

```java
// 点击“下载最后 N 个 (Download Last N)”时的操作：
downloadButton.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        // 找到单选组选的数据源 ID
        int selectedId = dataSource.getCheckedRadioButtonId();
        // 将单选按钮设置为所选选项
        sourceSelection = findViewById(selectedId);
        // 将选择选项转换为 String 对象
        String selectedOption = sourceSelection.getText().toString();
```

319 基于云的实时...数据采集与客户端架构 319

```java
// 用户在下载前应先输入记录数并选择
// 目标位置
if (lastNField).getText().toString().equals("")) {
    fetchArea.setText("请先浏览目标位置并输入\n记录数量。");
} else {
    // 根据要打印值的数量，
    // 以及选定的设备和源创建活动文件名
    filename = "Last_" + (lastNField).getText().toString() + "_" +
    "Android" + "_" + selectedOption;
    // 为文件名添加 csv 扩展名
    finalpath = miniPath + "/" + filename + ".csv";
    // 将完整的目录路径存储到 finalpath 对象中
    System.out.println("File path: " + finalpath);
}
// 创建一个用于 Cloudant 数据的可运行线程
Runnable download = new Runnable() {
    @Override
    public void run() {
        try {
            // 点击按钮时清除获取区域
            fetchArea.setText("");
            // 从 GUI 获取 N
            double length = Double.parseDouble(lastNField.getText().toString());
            // 从云数据库获取用于 Android 的回归值
            fetchRegressionValues();
            // 创建包含 String 数组的列表
            List<String> records = new ArrayList<>();
            // 添加表头记录
            records.add(new String[]{
                "Timestamp",
                "Download Speed",
                "Upload Speed",
                "Packets Received",
                "Packets Sent",
                "MobileDownloadSpeed",
                "MobileUploadSpeed",
                "WiFiStrength"
            });
            fetchArea.append("Timestamp, " + "Download Speed, " +
            "Upload Speed, " + "Packets Received, " + "Packets Sent, " +
            "MobileDownloadSpeed, " + "MobileUploadSpeed, " +
            "WiFiStrength, " + "\n");
            // 计算初始值以便仅存储最后 N
            // 参数
            int initial = (int) (numitems - length);
```

320 T. P. Fowdar, L. Babooram, M. N-D-ibn Nazir Rosun and M. Indoondonon
