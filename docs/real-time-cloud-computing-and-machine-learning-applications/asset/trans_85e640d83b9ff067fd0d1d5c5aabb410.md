

# 云端实时...数据采集与客户端架构 - 301

## 4.3.9.5. 通过程序化向实时图表添加数据

- 1. 在 `onCreate()` 方法中填充了与实时图表相关的必要调用后，本节中的方法位于 `MainActivity.java` 类内部，因此在 `onCreate()` 之外。`addEntry()` 方法负责在每次被调用时向图表添加数据点。这是在第 4.3.8 节描述的 `mRunnable` 线程内部执行的。每秒调用一次，就像将参数 String 对象打印到布局上一样。该方法首先使用 `LineData` 对象来验证图表是否包含任何唯一值，如列表 4.36 所示。

# 列表 4.36. 每秒向实时图表添加数据

```
// 向实时监控器添加一个值
private void addEntry(double var) {
// 从图表中获取数据（如果有）
LineData data = chart.getData();
// 如果图表包含之前的数据:
if (data != null) {
LineDataSet set = data.getDataByIndex(0);
if (set == null) {
set = SetData();
}
data.addDataSet(set);
}
// 通过设置 x, y 和 index = 0 向图表添加数据点
data.addEntry(new Entry(set.entryCount(), (float) var), 0);
data.notifyDataChanged();
// 通知图表数据发生变化
chart.notifyDataSetChanged();
// 设置固定的可见条目数量
chart.setVisibleXRangeMaximum(130);
// 将焦点位于最后一个条目
chart.moveToX(data.entryCount());
}
```

- 2. 接下来是 `SetData()` 方法，它返回类型为 `LineDataSet` 的图表特征，其中图表的打印选项和颜色如列表 4.37 所示。302 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoonon

# 列表 4.37. 设置图表的选项和颜色

```
// 设置打印选项/颜色
private LineDataSet SetDataSet() {
// 创建对象以修改每个数据点:
LineDataSet set = new LineDataSet(null, netparams);
// 设置图表的流向，即从左侧开始的值:
setAxisDependency(AxisDependency.LEFT);
// 设置线条颜色为蓝色:
setsetColor(Color.rgb(0, 0, 215));
// 设置数据点轮廓为黑色:
setCircleColor(Color.BLACK);
// 设置宽度、半径和颜色:
setLineWidth(3f);
setCircleRadius(5f);
setFillAlpha(75);
setFillColor(ColorTemplate.getHoloBlue());
setHighLightColor(Color.rgb(245, 118, 118));
setValueTextColor(Color.BLACK);
setValueSize(10f);
setDrawValues(false);
return set;
}
```

`LineData` 对象 `data` 上的 `addEntry(Entry())` 方法根据以下语法填充参数，下文将进一步解释。

data.addEntry(new Entry(x, y), yourDataSetIndex)

- `newEntry()` 接收要在图表上打印的 x 和 y 值。
- 第二个参数代表数据集的索引。

## 4.3.10. 使用云 Servlet 或本地服务器进行分析

本节描述了用户请求进行预测或分类时发生的过程。如前所述，这通过使用 `prediction.java` 类来实现，基本上，每当用户点击“Predict（预测）”按钮时，首先从 `prediction.xml` 布局中获取预测时间和窗口大小变量，然后创建一个 URL 来查询 servlet。当涉及到“Classify（分类）”按钮时，从 `MainActivity.java` 获取实时值，并通过附加到 servlet 的 URL 来查询 servlet。这发生在用户选择“Cloudant”单选按钮时。

然而，当选择“Local（本地）”选项时，将通过 GUI 上指定的 IP 地址使用 `Socket` 类通过客户端服务器模式连接运行在 NetBeans 上的本地服务器。为了让本地服务器确定 Android 应用请求的是哪种分析，`JSONObject` 变量将填充从一到五的整数，如表 4.3 所示的请求代码。这允许本地服务器执行描述的功能，并向 Android 应用返回相应的响应。

# 表 4.3. 本地 Android 分析的请求代码

| JSONObject requestCode | 功能 |
|---|---|
| 1 | 按样本数下载为 .csv |
| 2 | 按日期下载为 .csv |
| 3 | 预测分析 |
| 4 | 使用 Wi-Fi 参数分类 |
| 5 | 使用 LTE 参数分类 |

根据点击的按钮，采取以下步骤查询云服务器或本地服务器。

- 1. 全局定义的变量在列表 4.38 所示。

# 列表 4.38. Prediction.java 的全局变量

```
package com.example.network_monitor_app;
// 导入 android 库:
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.TextView;
import android.widget.RadioGroup;
import androidx.app.AppCompatActivity;
import org.json.JSONObject;
import org.json.JSONException;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.MalformedURLException;
import java.net.Socket;
import java.net.URLConnection;
import java.net.URL;
```

