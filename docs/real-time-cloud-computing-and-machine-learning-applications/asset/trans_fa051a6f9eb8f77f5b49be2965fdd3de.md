

```java
Socket socket = new Socket(IP_address.getText().toString(), 11111);
// 从 socket 输出流创建一个一个 PrintWriter
PrintWriter out = new PrintWriter(socket.getOutputStreamStream());
// 将请求发送到本地服务器
out.println(request);
//flush();
out.flush();
// 从 socket 输入流创建一个 BufferedReader 对象
InputStream is = socket.getInputStream();
// 将其封装在 InputStreamReader 中
InputStreamReader isr = new InputStreamReader(is);
// 将其封装在 BufferedReader 中
BufferedReader br = new BufferedReader(isr);
// 从 BufferedReader 对象中读取数据
String data = br.readLine();
// 将 String 转换为 JSON 对象
JSONObject CSV_data = new JSONObject(data);
// 存储从服务器获取的 CSV 数据
returned_val = CSV_data.getString("CSV");
// 将 CSV 写入本地存储
writeToStorage(returned_val);
} catch (Exception ex) {
    ex.printStackTrace();
}
return null;

@Override
protected void onPostExecute(Void aVoid) {
    super.onPostExecute(aVoid);
    results.setText(returned_val);
}
```

## 6.3.27. DataRetriever 类

该类负责建立与 Cloudant 平台的连接并从数据库获取适当的数据。列表 6.19 显示了该类的声明。

## 列表 6.19. DataRetriever 类声明

```java
package com.test.weathermonitoring;
import com.cloudant.client.api.Builder;
import com.cloudant.client.api.CloudantClient;
import com.cloudant.client.api.Database;
import com.cloudant.client.api.query.Expression;
import com.cloudant.client.api.query.QueryBuilder;
import com.cloudant.client.api.query.QueryResult;
import com.cloudant.client.api.query.Selector;
import com.cloudant.client.api.query.Sort;
import com.google.gson.internal.LinkedTreeMap;

import java.net.MalformedURLException;
import java.net.URL;
import java.util.List;

import static com.cloudant.client.api.query.Expression.gt;
import static com.cloudant.client.api.query.Expression.regex;

public class DataRetriever {
    // 来自 CloudantClient API 的数据库对象
    private Database db;
    private double row_count;
```

## 6.3.2.1. DataRetriever 构造函数

这是该类的主构造函数。它负责打开到 Cloudant 数据库的连接并获取数据库中记录的总数。使用静态 Builder 类创建 Cloudant 对象以访问 Cloudant API 函数。要连接到 Cloudant API，需要数据库的 URL 端点以及数据库的用户名和密码。使用 CloudantClient 的 `database()` 方法获取数据库实例。该方法的代码在列表 6.20 中。

## 列表 6.20. DataRetriever 构造函数

```java
public DataRetriever() {
    try {
        System.out.println("Connecting to Cloudant database");
        // 来自 Cloudant 库的 Cloudant 对象
        CloudantClient client = ClientBuilder.url(new URL("https://c3e0434f-ab39-4abf-a854-bluemix.cloudant.com/"))
            .username("apikey-ec10b0de78947b57ab516f9ff49965093")
            .password("69383724fb8ec7f098c350328fbcbf7ef4606fb")
            .build();
        db = client.database("weather_data", false);
        row_count = getNoRows();
} catch (MalformedURLException e) {
  e.printStackTrace();
}
```

## 6.3.27.2. getNoRows() 方法

该方法用于查找云数据库中记录的总数。每条记录都包含一个标记为 "idx" 的键，作为主键。每添加新记录时，“idx" 的值就会加 1。为了找到 "idx" 的最后一个值，编写一个查询，选择数据库中的所有数据并按降序排序。该过程的代码在列表 6.21 中。

## 列表 6.21. getNoRows 函数

```java
private double getNoOfRow() {
// 使用 CloudantClient 的表达式来表示评估 (idx > 0)
Expression selector = gt("idx", 0);
// 使用表达式构建查询并按降序排序
QueryBuilder query = new QueryBuilder(selector).sort(Sort.desc("idx"));
// 使用构建的 QueryBuilder 查询数据库
QueryResult<LinkedTreeMap> result = db.query(query.build());
LinkedTreeMap class;
// 获取匹配搜索的文档列表
List<LinkedTreeMap> resultList = result.getDocs();
// 返回 idx 的最大值 -> 第一个结果
return (resultList.size() > 0) ? (double) resultList.get(0).get("idx") : 0;
}
```

## 6.3.27.3. getDataArray() 方法

该方法用于从云数据库获取特定日期的记录。为了获取最后 N 条记录，使用了 `getNoOfRows()` 方法返回的整数，可以使用以下公式确定获取最后 N 条记录需要开始的索引：

```
Start_index = total_records - N
```

将构建一个新请求来获取 idx 大于 "start_index" 的值，从而获取最后 N 条记录。要获取特定日期的数据，则使用正则表达式来查找所有匹配给定日期的记录。

# 云端实时...数据捕获与客户端架构 635

根据所需的数据，创建适当的 `Selector` 对象。使用 `QueryBuilder` 对象创建适当的查询。该查询通过 `Database` 实例的 `query ( )` 方法执行。该方法接收查询的字符串表示和查询返回的对象的类。在这种情况下，返回的数据类型是 `LinkedTreeMap`，它是一个从可比较键到值的映射。`query ( )` 方法返回一个 `QueryResult` 对象，其中包含查询结果的详细信息，表现为匹配查询标准的记录列表、警告、书签和执行统计。

通过 `QueryResult` 对象的 `getDocs()` 方法获取记录列表并将其存储在 `List` 中。

## 列表 6.2. getDatabaseArray 方法

```java
public Object[] getDatabaseArray(String date, int size) {
    // 构建 Selector 和 QueryBuilder 请求
    Selector selector;
    // 检查我们需要的是特定日期还是 N 条样本
    if (date.length() < 1) {
        // 需要 N 条样本 (大于)
        selector = gt("idx", row_count - size);
    } else {
        // 需要特定日期，使用正则表达式匹配
        selector = regex("Time", date);
    }
    // 构建查询
    QueryBuilder query = new QueryBuilder(selector).sort(Sort.asc("idx"));
    QueryResult<LinkedTreeMap> result = db.query(query.build(), LinkedTreeMap.class);
    List<LinkedTreeMap> resultList = result.getDocs();
    double[][] db_data = new double[resultList.size()][7];
    String[] timestamps = new String[resultList.size()];
    for (int i = 0; i < resultList.size(); i++) {
        LinkedTreeMap result = resultList.get(i);
        double temperature = (double)result.get("Temperature");
        double wind_speed = (double)result.get("WindSpeed");
        double wind_direction = (double)result.get("WindDirection");
        double pressure = (double)result.get("Pressure");
        double visibility = (double)result.get("Visibility");
        double humidity = (double)result.get("Humidity");
        double cloudiness = (double) result.get("Cloudiness");
        timestamps[i] = (String) result.get("Time");
        db_data[i][0] = temperature;
        db_data[i][1] = wind_speed;
        db_data[i][2] = wind_direction;
        db_data[i][3] = pressure;
        db_data[i][4] = visibility;
        db_data[i][5] = humidity;
        db_data[i][6] = cloudiness;
    }
    return new Object[][]{db_data, timestamps};
}
```

## 6.3.28. 测试移动应用程序

此部分展示了 Android 应用程序（即边缘设备）的预期操作截图。

### 6.3.28.1. 实时监控

- 1. 启动应用程序时向用户显示的图形用户界面（GUI）如图 6.21 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_647_0.png)

图 6.21. 天气监控应用的主界面。

