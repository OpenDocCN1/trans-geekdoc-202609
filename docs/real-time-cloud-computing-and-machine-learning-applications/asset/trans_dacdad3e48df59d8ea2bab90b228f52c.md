

# 云计算基础

该应用将作为图 2.123 所示 IBM Bluemix 平台上的部署服务出现。

13. 点击图 2.124 所示的应用 URL，将在图 2.125 所示的浏览器中打开。再次，计算为 1 个参数的区域为空。

![](img/2b52fde0e707e8c2f05a10309c3f8982_128_0.png)

图 2.124。定位应用 URL。

![](img/2b52fde0e707e8c2f05a10309c3f8982_128_1.png)

图 2.125。在浏览器中运行无参数的 CalculateArea servlet。

14. 通过访问以下 URL：https://calculatearea-gb.mybluemix.net/?length=10&width=50 来运行带有参数 length = 10 和 width = 50 的应用；在这种情况下，servlet 将响应图 2.126 所示的面积 500。

![](img/2b52fde0e707e8c2f05a10309c3f8982_128_2.png)

图 2.126。在浏览器中设置两个参数并运行 CalculateArea 应用。

118 T. P. Fowder, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonendam

## 2.8.1. 创建桌面应用程序向 CalculateArea servlet 发送请求

该应用在 Netbeans IDE 中开发，通过创建一个项目 CalculateArea，并在其中添加了一个名为 Calculate_Area.java 的 JFrame 帧。具有典型输出的完整应用如图 2.127 所示。当点击“SEND PARAMETERS TO CLOUD”按钮时，在长度和宽度字段中输入的值将作为 URL 查询发送到 CalculateArea servlet，该 servlet 将返回计算面积的值。

![](img/2b52fde0e707e8c2f05a10309c3f8982_129_0.png)

图 2.127。Calculate_Area.java 的 JFrame。

该项目需要 jsoup-1.13.1.jar 文件，该文件从 [37] 获取。此 jar 文件允许在项目中导入以下两个库：

- 1. org.jsoup.Jsoup：这是一个支持对标准 HTML 文件操作的 Java 库。它为数据提取和处理提供了一个非常方便的 API，使用了多种方法如文档对象模型 (DOM)、CSS 和类似 jquery 的方法。Jsoup 以类似于现代浏览器的方式分析 HTML 文件，使用相同的 DOM [38]。它还实现了 WHATWG HTML5 标准。
- 2. org.jsoup.nodes.Document：Document 类提供了 `connect()` 方法来连接到 URL 主机，或使用 `get()` 方法来从主机获取响应 [39]。

在创建 GUI 帧并将 jar 文件添加到项目句后，主 JFrame（即 Calculate_Area.java）的代码如代码列表 2.10 所示。需要注意的是，只需要添加为 `JButtonActionPerformed()` 方法的代码，因为其他代码在 GUI 组装时会自动生成。

## 代码列表 2.10. Calculate_Area.java 类

```java
import org.jsoup.Jsoup;
//表示一个 HTML 文档。
import org.jsoup.nodes.Document;

public class Calculate_Area extends javax.swing.JFrame {
    /**
     * 自动生成的代码
     */
    private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {

        try {
            //定义连接到 Java Servlet 的 url
            String host = "https://calculatearea.eu-gb.mybluemix.net/?"
                + //解析在 JTextField1 中输入的整数
                + "length=" + Integer.parseInt(jTextField1.getText())
                + //解析在 JTextField2 中输入的整数
                + "width=" + Integer.parseInt(jTextField2.getText())
            //连接到 URL 并获取 html body
            Document doc = Jsoup.connect(host).ignoreContentType(true).get();
            //从 URL 提取文本格式的数据
            //在 jTextField3 中显示结果
            jTextField3.setText(doc.text());
        } catch (Exception ex) {

        }
    }

    /* 自动生成的代码 */
```

## 2.8.2. 创建移动应用程序向 CalculateArea Servlet 发送请求

该应用在 Android Studio IDE 中开发，通过创建一个名为 CalculateArea 的项目。具有典型输出的完整应用如图 2.128 所示。当点击“SEND PARAMETERS TO CLOUD”按钮时，在长度和宽度字段中输入的值将作为 URL 查询发送到 CalculateArea servlet，该 servlet 将返回计算面积的值。

120 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonondon

![](img/2b52fde0e707e8c2f05a10309c3f8982_131_0.png)

图 2.128。CalculateArea 应用程序的布局。

activity_main.xml 文件在代码列表 2.11 所示。CalculateArea 应用程序的 activity_main.xml 文件。

代码列表 2.11. activity_main.xml

```xml
<LinearLayout android:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Length:" />

    <EditText
        android:id="@+id/ED1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="number" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Width:" />

    <EditText
        android:id="@+id/ED2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="number" />

    <Button
        android:id="@+id/B1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="SEND PARAMETERS TO CLOUD" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="RESPONSE FROM CLOUD:" />

    <EditText
        android:id="@+id/ED3"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="text" />

</LinearLayout>
```

CalculateArea 应用程序的 activity_main.xml 文件在代码列表 2.12 所示。CalculateArea 应用程序的 activity_main.xml 文件。

代码列表 2.12. CalculateArea.java 类

```java
package com.example.calculatearea;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.os.AsyncTask;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;

public class MainActivity extends AppCompatActivity {

    EditText ED1,ED2,ED3;

    Button B1;
    String length = "";
    String width = "";
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        ED1 = (EditText)findViewById(R.id.ED1);
        ED2 = (EditText)findViewById(R.id.ED2);
        ED3 = (EditText)findViewById(R.id.ED3);
        B1 = (Button)findViewById(R.id.B1);
        B1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                length = ED1.getText().toString();
                width = ED2.getText().toString();

                //在另一个线程上后台执行查询部分。

                new QueryServer().execute();
            }
        });
    }
}

// 使用 QueryServer 类来扩展 AsyncTask。

```java
public class QueryServer extends AsyncTask<Void, Void, Void> {

    String returnedval = "";
    @Override
```
