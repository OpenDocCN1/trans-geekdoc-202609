

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

