
```xml
<!-- 表示第一行的 LinearLayout -->
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="3sp"
    android:background="#E3F2FD"
    android:orientation="horizontal"
    android:padding="3sp">
    <!-- TextView - IP地址的标签 -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_gravity="center"
        android:layout_margin="5sp"
        android:layout_weight="0.3"
        android:foregroundGravity="center_vertical"
        android:gravity="center|end"
        android:padding="5sp"
        android:text="Local Server"
        android:textColor="@android:color/background_dark" />
    <!-- EditText 显示IP地址 -->
    <EditText
        android:id="@+id/IP_address"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_gravity="center"
        android:layout_margin="5sp"
        android:layout_weight="0.3"
        android:ems="10"
        android:foregroundGravity="center_vertical"
        android:gravity="center"
        android:inputType="none"
        android:padding="5sp"
        android:text="192.168.100.3" />
    <!-- Switch 表示从本地服务器还是云端下载 -->
    <Switch
        android:id="@+id/use_local"
        android:layout_width="match_parent">
```

```xml
        android:layout_height="match_parent"
        android:layout_margin="5sp"
        android:layout_weight="0.3"
        android:padding="5sp"
        android:text="Cloud"/>
</LinearLayout>

<!-- 表示第二行的 LinearLayout布局 -->
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="3sp"
    android:background="#E3F2FD"
    android:orientation="horizontal"
    android:padding="3sp">
    <!--TextView - 窗口大小标签 -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="40sp"
        android:layout_gravity="center"
        android:layout_margin="3sp"
        android:layout_weight="0.3"
        android:foregroundGravity="center_vertical"
        android:gravity="center|end"
        android:padding="2sp"
        android:text="Download Last N samples"
        android:textColor="@android/color/background_dark" />
    <!-- 输入窗口大小的 EditText -->
    <EditText
        android:id="@+id/sample_size"
        android:layout_width="match_parent"
        android:layout_height="40sp"
        android:layout_gravity="center"
        android:layout_margin="3sp"
        android:layout_weight="0.3"
        android:ems="10"
        android:foregroundGravity="center_vertical"
        android:gravity="center"
        android:inputType="none|number"
        android:padding="2sp"
        android:text="60" />

    <Button
        android:id="@+id/download_samples"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="3sp"
        android:layout_weight="0.3"
        android:padding="3sp"
        android:text="Download"/>
</LinearLayout>
```

```xml
<!-- 表示第三行的布局 -->
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="3sp"
    android:background="#E3F2FD"
    android:orientation="horizontal"
    android:padding="3sp">
    <!-- 时间视图标签 -->
    <TextView
        android:id="@+id/textView2"
        android:layout_width="match_parent"
        android:layout_height="40sp"
        android:layout_gravity="center"
        android:layout_margin="3sp"
        android:layout_weight="0.3"
        android:foregroundGravity="center_vertical"
        android:gravity="center|end"
        android:padding="2sp"
        android:text="Download for Date :"
        android:textColor="@android/color/background_dark"/>
    <!-- 日期的 EditText -->
    <EditText
        android:id="@+id/date_text"
        android:layout_width="match_parent"
        android:layout_height="40sp"
        android:layout_gravity="center"
        android:layout_margin="3sp"
        android:layout_weight="0.3"
        android:ems="10"
        android:foregroundGravity="center_vertical"
        android:gravity="center"
        android:padding="2sp"
        android:text="29/11/2020"
        tools:ignore="Textfields"/>
    <Button
        android:id="@+id/download_date"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="3sp"
        android:layout_weight="0.3"
        android:padding="3sp"
        android:text="Download" />
</LinearLayout>
<!-- 显示云端结果的 TextView -->
<ScrollView
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/results"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="3sp"
        android:background="@android/color/holo_orange_light"
        android:inputType="textMultiLine"
        android:padding="5sp"
        android:text="Result here."
        android:textColor="@android/color/background_dark"
        android:scrollbars="vertical" />
</ScrollView>
```

## 云端实时...数据采集与客户端架构 ... 623

该类用于执行以下功能：

- 使用 `activity_data` 布局向用户显示 UI。
- 使用内部 `AsyncTask` `QueryCloud` 从云数据库获取数据，在后台线程执行网络操作。
- 使用内部 `AsyncTask` `QueryLocal` 从本地服务器获取数据，在后台线程执行网络操作。
- 从云端获取数据后，将数据转换为 CSV 文件并保存到内部存储。

## 云端实时...数据采集与客户端架构 ... 621

```java
package com.testing;

import android.appcompat.app.AppCompatActivity;
import android.app.Activity;
import android.annotation.SuppressLint;
import android.content.Manifest;
import android.content.pm.PackageManager;
import android.os.AsyncTask;
import android.os.Bundle;
import android.os.Environment;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Switch;
import android.widget.TextView;
import org.json.JSONObject;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.Socket;
import java.util.Date;
import java.util.Locale;
import androidx.core.content.ContextCompat;

@SuppressLint("AllPermissions")
public class DownloadData extends AppCompatActivity {
    private static final int REQUEST_WRITE_STORAGE = 1;
    Button download_sample, download_date;
    EditText sample_size, date_time;
    TextView results;
    Switch use_cloud;
    private EditText ip_address;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_data);

        download_sample = findViewById(R.id.download_samples);
        download_date = findViewById(R.id.download_date);

        sample_size = findViewById(R.id.sample_size);
        date_time = findViewById(R.id.date_text);
        results = findViewById(R.id.results);
        ip_address = findViewById(R.id.IP_address);
        use_cloud = findViewById(R.id.use_local);

        download_date.setOnClickListener(view -> {
            if (use_cloud.isChecked()) {
                new QueryDataCloud(true).execute();
            } else {
                System.out.println("Local server");
                new QueryDataLocal(true).execute();
            }
        });

        download_sample.setOnClickListener(view -> {
            if (use_cloud.isChecked()) {
                new QueryDataCloud(false).execute();
            } else {
                System.out.println("Local server");
                new QueryDataLocal(false).execute();
            }
        });
    }
}
```

### 6.3.24.2. `convertToCSV()` 方法

该方法接受 `DataRetriever` 类返回的对象数组，该数组包含了从 Cloudant 数据库获取的数据。对象数组包含一个字符串数组，用于存储观测的时间戳，以及一个双精度数值二维数组，其中每一行代表七个气象参数的观测值。数据被提取并类型转换为

# 云端实时...数据捕获与客户端架构 627

适当的格式。提取后，通过以下步骤将数据转换为 CSV 文件：

- CSV 文件名根据当前时间戳自动生成，并创建一个带有“CSV”扩展名的新文件。
- 创建一个 `StringBuilder` 对象来构建 CSV 文件的字符串表示。首先追加表头行。
