
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:context=".MainActivity"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <!-- 输入 IP 地址的输入框 -->
    <EditText
        android:id="@+id/ipAddress"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="20dp"
        android:layout_marginTop="10dp"
        android:ems="10"
        android:hint="Enter address"
        android:inputType="text"
        android:textColor="#3F51B5"
        android:textColorHint="#3F51B5" />

    <!-- 存储 csv 文件的按钮 -->
    <Button
        android:id="@+id/browseButton"
        android:layout_width="140dp"
        android:layout_height="wrap_content"
        android:layout_marginLeft="12dp"
        android:layout_marginTop="12dp"
        android:fontFamily="sans-serif"
        android:text="Browse"
        android:textColor="#3F51B5"
        android:textSize="20sp" />

    <!-- 组件在同一行对齐的单行 -->
    <TableRow
        android:id="@+id/tableRow3"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="3dp">
        <!-- 选择数据的输入框 -->
        <TextView
            android:id="@+id/dataSourceText"
            android:layout_width="111dp"
            android:layout_height="wrap_content"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="10dp"
            android:text="Data Source: "
            android:textColor="#3F51B5"
            android:textSize="18sp" />

        <!-- 单选按钮组，只能勾选一个 -->
        <RadioGroup
            android:id="@+id/dataSource"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_above="@id/view_below"
            android:layout_marginTop="7dp"
            android:orientation="horizontal">
            <!-- Cloudant 选项的单选按钮 -->
            <RadioButton
                android:id="@+id/cloudantSource"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:checked="true"
                android:text="Cloudant" />
            <!-- 本地服务器选项的单选按钮 -->
            <RadioButton
                android:id="@+id/localSource"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:text="Local" />
        </RadioGroup>
    </TableRow>

    <!-- 允许组件均匀分布的单行 -->
    <TableRow
        android:id="@+id/tableRow1"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="3dp">
        <!-- 输入预测时间的输入框 -->
        <EditText
            android:id="@+id/predictionTime"
            android:layout_width="180dp"
            android:layout_height="wrap_content"
            android:layout_marginLeft="20dp"
            android:layout_marginTop="10dp"
            android:ems="10"
            android:hint="Prediction time:"
            android:inputType="number"
            android:textColor="#3F51B5"
            android:textColorHint="#3F51B5" />
        <!-- 输入窗口大小的输入框 -->
        <EditText
            android:id="@+id/windowSize"
            android:layout_width="179dp"
            android:layout_height="wrap_content"
            android:layout_marginLeft="20dp"
            android:layout_marginTop="10dp"
            android:ems="10"
            android:hint="Window size:"
            android:inputType="number"
            android:textColor="#3F51B5"
            android:textColorHint="#3F51B5"
            tools:layout_editor_absoluteX="16dp" />
    </TableRow>

    <!-- 将按钮分组在同一行的单行 -->
    <TableRow
        android:id="@+id/tableRow2"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="3dp">
        <!-- 执行回归分析的按钮 -->
        <Button
            android:id="@+id/predictButton"
            android:layout_width="140dp"
            android:layout_height="wrap_content"
            android:layout_marginLeft="12dp"
            android:layout_marginTop="12dp"
            android:fontFamily="sans-serif"
            android:text="Predict"
            android:textColor="#3F51B5"
            android:textSize="20sp" />
        <!-- 执行分类分析的按钮 -->
        <Button
            android:id="@+id/classifyButton"
            android:layout_width="140dp"
            android:layout_height="wrap_content"
            android:layout_marginLeft="12dp"
            android:layout_marginTop="12dp"
            android:fontFamily="sans-serif"
            android:text="Classify"
            android:textColor="#3F51B5"
            android:textSize="20sp" />
    </TableRow>

    <!-- 显示分析结果的区域 -->
    <TextView
        android:id="@+id/textView1"
        android:layout_width="36dp"
        android:layout_height="300dp"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="24dp"
        android:text="Enter values and click any button to start!"
        android:textColor="#3F51B5"
        android:textColorHint="#3F51B5" />
</LinearLayout>
```

```
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:layout_marginTop="10dp"
android:text="要获取日期"
android:textColor="#3F51B5"
android:textSize="18sp" />
<!-- 用于存储用户输入日期的字段 -->
<EditText
android:id="@+id/date"
android:layout_width="117dp"
android:layout_height="wrap_content"
android:layout_marginLeft="20dp"
android:layout_marginTop="5dp"
android:ems="10"
android:gravity="center"
android:hint="日期"
android:inputType="text"
android:textColor="#3F51B5"
android:textColorHint="#3F51B5"
tools:layout_editor_absoluteX="16dp" />
<!-- 按日期下载样本的按钮 -->
<Button
android:id="@+id/downloadDateButton"
android:layout_width="140dp"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:layout_marginTop="12dp"
android:fontFamily="sans-serif"
android:text="下载"
android:textColor="#3F51B5"
android:textSize="20sp" />
</TableRow>
<!-- 显示获取到的值的区域 -->
<TextView
android:id="@+id/resultArea"
android:layout_width="367dp"
android:layout_height="512dp"
android:layout_marginStart="24dp"
android:layout_marginLeft="24dp"
android:layout_marginTop="20dp"
android:text="按数值数量或日期下载!"
android:textColor="#3F51B5" />
```

```
android:textColor="#3F51B5"
android:textSize="12sp"
android:scrollbars = "vertical"
app:layout_constraintStart_toStartOf="parent" />
</LinearLayout>
```

这产生了图 4.18 中的调色板区域。

![](img/2b52fde0e707e8c2f05a10309c3f8982_290_0.png)

图 4.18. Download.java 的调色板区域。

## 4.3.4. 在 Main Activity 中声明全局变量

在设计完软件前端后，组件现在已准备好与后端连接，即此应用程序的 Java 部分。因此，本节描述了如何在 `MainActivity.java` 类内部定义全局变量以及组件，它们的功能以及它们的使用位置，详见代码旁边的注释。

280 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonadon

1. 由于包含了实时图表，为了主动监听传入的参数，使用了来自第 4.3.2 节中导入库的 `LineChart` 类对象，将实时值打印到图表上。这一过程通过让 `MainActivity.java` 类实现 MPAndroidChart 库中名为 `OnChartValueSelectedListener` 的监听器来实现，该监听器在选择图表上的值时（即点击点击数据点时）注册回调。因此，在代码列表 4.2 中修改了默认的 `MainActivity.java` 类，如列表 4.12 所示。

### 列表 4.12. 实现 OnChartValueSelectedListener

```
public class MainActivity AppCompatActivity implements
OnChartValueSelectedListener {
```

2. 当项目在包含监听器后进行同步时，以下两个方法会被自动调用，如列表 4.12 中的“implements”(`implements`)关键字所示。

- `onValueSelected()`：当图表内部选择了一个值时调用，用于在图表上显示值。
- `onNothingSelected()`：当未选择任何内容或执行“取消选择”操作时调用。

3. 这样做之后，项目会再次同步，上述两个方法会被自动创建。需要注意的是，在这种情况下，`onValueSelected()` 方法被修改过，每当点击数据点时都会调用一个 `Toast`。这段代码返回所选点的坐标，即如列表 4.13 所示相对于时间注册的数据。在这种情况下，`onNothingSelected()` 方法被留空。

### 列表 4.13. 选择值时调用 Toast
