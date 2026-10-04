

# 266 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonundan

![](img/2b52fde0e707e8c2f05a10309c3f8982_277_0.png)

图 4.15. activity_main.xml 添加第一个组件后的调色板区域。

- 3. 同样，从调色板中选择了“按钮（Button）”组中的一个并插入了它。为了对齐，还添加了左边距。

# 列表 4.5 向 XML 文件添加“开关（Switch）”组件

```
<Switch
android:id="@id/cloudSwitch"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="5dp"
android:text="Push directly to cloud"
android:textColor="#3F51B5" />
```

4. 为了水平排列两个按钮，即“监控（Monitor）”和“停止（Stop）”按钮，使用了 TableRow 标签，并添加了轻微的上边距以改善视觉效果。

# 列表 4.6 在 xml 的“TableRow”中组织按钮

```
<TableRow
android:id="@id/tableRow1"
android:layout_width="fill_parent"
android:layout_height="wrap_content"
android:layout_marginTop="8dp">

<Button
android:id="@id/monitorButton"
android:layout_width="141dp"
android:layout_height="wrap_content"
android:layout_marginLeft="65dp"
android:layout_marginTop="12dp"
android:fontFamily="sans-serif"
android:text="MONITOR"
android:textColor="#3F51B5"
android:textSize="20sp" />
```

```
android:id="@id/stopButton"
android:layout_width="129dp"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:layout_marginTop="12dp"
android:fontFamily="sans-serif"
android:text="STOP"
android:textColor="#3F51B5"
android:textSize="20sp" />
```

5. 这一步涉及为图表和参数选择（即下拉选择器 spinner）添加空间。此实时监控图表的目的是为用户提供一个正在计算的参数变化的视图，因为之前的记录也会显示在图表中，而不是在 TextView 字段中更改值。这些值对于已执行的分析至关重要，因为它们显示了用户执行操作后的主要变化。可以使用之前添加的 AndroidChart 库 [10] 中现有的 com.github.mikephil.charting.charts.LineChart 将图表添加到 activity_main.xml 文件中，如节 4.3.2 所示。尺寸和位置也已指定，可以根据喜好进行调整。引入一个 Spinner 对象，它与图表要显示的属性选择有关。布局中添加这些组件的情况见列表 4.7。

# 列表 4.7 在 xml 文件上添加图表组件

```
android:id="@id/chart1"
android:layout_width="408dp"
android:layout_height="283dp"/>/com.github.mikephil.charting.charts.LineChart
```

268 T. P. Fowdur, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoonondan

```
<Spinner
android:id="@id/spinner1"
android:layout_width="249dp"
android:layout_height="24dp"
android:layout_marginLeft="10dp"
android:layout_marginTop="8dp"
android:layout_marginBottom="5dp" />
```

6. 通过 TextView 组件添加打印参数的字段，如列表 4.8 所示。这些字段随后被复制和编辑以容纳共七个参数。

# 列表 4.8 用于存储网络参数的 XML 代码

```
<TextView
android:id="@id/textView1"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="WiFi Download Speed: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView2"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="WiFi Upload Speed: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView6"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="LTE Download Speed: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView7"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="LTE Upload Speed: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView3"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="Packets received: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView4"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="Packets Sent: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView5"
android:layout_width="230dp"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="Wifi Strength: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

7. 最后，相同的方式将“前往分析（Go to Analysis）”和“前往下载（Go to Download）”按钮添加到第 4 步的对齐中。代码见列表 4.9。

# 列表 4.9 用于网络添加按钮

```
<Button
android:id="@id/algoButton"
android:layout_width="250dp"
android:layout_height="wrap_content"
android:gravity="center_horizontal|center_vertical"
android:layout_marginTop="12dp"
android:fontFamily="sans-serif"
android:text="GO TO ANALYSIS"
android:textColor="#3F51B5"
android:textSize="20sp" />
<Button
android:id="@+id/downloadButton"
android:layout_width="250dp"
android:layout_height="wrap_content"
android:gravity="center_horizontal|center_vertical"
android:layout_marginTop="5dp"
android:fontFamily="sans-serif"
android:text="GO TO DOWNLOAD"
android:textColor="#3F51B5"
android:textSize="20sp" />
```

图 4.16 显示了上述组件的布局以及调色板区域。

![](img/2b52fde0e707e8c2f05a10309c3f8982_281_0.png)

图 4.16. Monitor_App 项目的 MainActivity 区域。

## 4.3.3.3. 构建 Prediction.xml 的视觉效果

遵循与上一节相同的原则，此处使用了线性布局。完整代码见列表 4.10，其中包含一个 RadioGroup 组件，可以选择两个按钮，用于指示从云或本地存储的数据库进行选择。

# 列表 4.10. prediction.xml 布局

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">
    <!-- 存储用户输入的 IP 地址的字段 -->
    <EditText
        android:id="@id/editT1"
        android:layout_width="match_content"
        android:layout_height="wrap_content"
        android:hint="Enter IP address"
        android:inputType="textPersonName" />
    <!-- 容纳共三个组件的单行 -->
    <TableRow
        android:id="@id/tableRow3"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="3dp">
        <!-- 指示数据源的标签 -->
        <TextView
            android:id="@id/dataSourceText"
            android:layout_width="111dp"
            android:layout_height="wrap_content"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="10dp"
            android:text="Data Source: "
            android:textColor="#3F51B5"
            android:textSize="18sp" />
        <!-- 包含两个按钮的单选组，一次只能选中一个 -- -->
    </TableRow>
</LinearLayout>
```

