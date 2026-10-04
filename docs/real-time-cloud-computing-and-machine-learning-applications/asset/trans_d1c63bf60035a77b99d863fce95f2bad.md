

# 基于云的实时... 服务器与 Servlet 架构 761

`convertToFloat(double[])` 数组方法将二维数组转换为二维 float 数组。该 float 数组随后被用作神经网络的输入。如列表 7.28 所示。

## 列表 7.28. convertToFloat() 方法

```
private static float[][] convertToFloat(double[][] array) {
    int col = array[0].length;
    int row = array.length;
    float[][] data = new float[row][col];
    for (int i = 0; i < row; i++) {
        for (int j = 0; j < col; j++) {
            data[i][j] = (float) array[i][j];
        }
    }
    return data;
}
```

### 7.3.6. "Downloader" Servlet

"Downloader" Servlet 负责响应移动端和电脑用户的查询，提供特定日期的天气观测结果或最后 N 条观测结果。该类实现的功能如下：

- 在 `doPost()` 方法中，使用 `getParameter()` 方法提取用户请求的日期或观测数量 `d_size`。
- 请求中通过 "data_src" 参数包含了获取数据的数据源。
- 如果用户请求最后 N 条观测结果，则将变量 `d_size` 转换为其等效值。
- 调用 `response()` 方法，负责从 Cloudant 数据库或本地数据库获取所需数据。之后，将数据转换为 CSV 字符串。数值数组转换为 CSV 文件的代码已在 6.3.26 节解释过。
- 从 `HttpServletResponse` 获取 `PrintWriter` 对象。
- 创建一个 `JSONObject`并将 CSV 字符串存储其中。
- 最后，将 `JSONObject` 发送给用户并关闭连接。

该 Servlet 的代码见列表 7.29。

## 列表 7.29. Downloader Servlet

```java
import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.json.JSONObject;

import org.database.DataRetriever;
import org.database.SQLConnector;

@WebServlet("Downloader")
public class Downloader extends HttpServlet {
    private static final long serialVersionUID = 1L;

    public Downloader() {
        super();
        // 自动生成的构造函数
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
        doPost(request, response);
    }

    protected void doPost(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
        System.out.println("Data sent");

        // 获取用户请求的日期或观测数量
        String d_time = request.getParameter("date");
        String d_size = request.getParameter("n");
        // 获取使用的数据源
        String source = request.getParameter("data_src");
        int window_size = 0;
        // 如果 d_size 参数存在则转换为整数
        if (d_size != null && d_size.length() > 0) {
            window_size = Integer.parseInt(d_size);
        }

        // 从响应中获取 CSV 字符串
        String CSV = response(d_time, window_size, source);
        // 从 HttpServletResponse 获取 PrintWriter
        PrintWriter out = response.getWriter();
        // 创建一个 JSONObject 来持有数据
        JSONObject result = new JSONObject();
        result.put("CSV", CSV);
        // 将数据发送到客户端
        out.print(result);
        out.flush();
        out.close();
    }

    public String response(String date, int size, String source) throws IOException {
        // 创建 DataRetriever 对象从云端获取数据
        DataRetriever dataRetriever = new DataRetriever();
        // 创建 SQLConnector 对象从云端获取数据
        SQLConnector sqlConn = new SQLConnector();

        // 加载云端数据的数组
        Object[] databaseArray = null;
        // 检查使用云端数据还是本地数据库数据
        if ("cloud".equals(source)) {
            // 如果 size > 0 获取最后 N 个值，否则按日期获取
            if (size > 0) {
                databaseArray = dataRetriever.getDatabaseArray(date, size);
            } else {
                databaseArray = dataRetriever.getDatabaseArray(date, 0);
            }
        } else {
            if (size > 0) {
                databaseArray = sqlConn.fetchLastN(size);
            } else {
                databaseArray = sqlConn.fetchForDate(date);
            }
        }

        // 从对象数组中提取数据
        double[][] readings = (double[][]) databaseArray[0];
        String[] timestamps = (String[]) databaseArray[1];

        // 创建一个新的 StringBuilder 对象
        StringBuilder sb = new StringBuilder();
        // 代表 CSV 文件表头的字符串
        String header = "Time";
        // ... (其余实现部分)
        return ""; 
    }
}
```

### 7.3.7. "graphUpdater" Servlet

"graphUpdater" Servlet 负责从 Cloudant 数据库获取最新的观测结果并将其返回给用户。返回的值用于更新 HTML 页面上的图表。该 Servlet 执行以下功能：

字体 使用 `getParameter()` 函数从 URL 中获取用户请求的天气参数。
- 通过 "source" 参数从请求中获取获取数据源。
- 从 Cloudant 数据库或本地数据库获取最后一次观测结果。
- 使用 switch 语句确定需要发送给用户的哪个参数。
- 创建一个 JSON 对象并存储值。
- 从 `HttpServletResponse` 创建并获取 `PrintWriter` 对象。
- 将内容类型设置为 JSON，因为正在发送 JSON 文件。
- 最后，将 JSON 对象的等效字符串发送给用户并关闭连接。

该 Servlet 的代码见列表 7.30。

## 列表 7.30. 更新图表的 graphUpdater Servlet

```java
import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.json.JSONObject;

import org.database.DataRetriever;
import org.database.SQLConnector;

@WebServlet("/graphUpdater")
public class graphUpdater extends HttpServlet {
    private static final long serialVersionUID = 1L;

    public graphUpdater() {
        super();
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
        doPost(request, response);
    }

    protected void doPost(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
        // 获取用户请求的天气参数
        String parameter = request.getParameter("param");
        // 获取数据源
        String source = request.getParameter("source");

        // 创建 DataRetriever 对象从云端获取数据
        DataRetriever dataRetriever = new DataRetriever();
        // 创建 SQLConnector 对象从云端获取数据
        SQLConnector sqlConn = new SQLConnector();

        // 加载云端数组
        Object[] databaseArray = null;
        // 检查使用云端数据还是本地数据库数据
        if ("cloud".equals(source)) {
            // 如果 size > 0 获取最后 N 个值，否则按日期获取
            // (逻辑类似于 downloader)
        } else {
            // (逻辑类似于 downloader)
        }

        // 提取包含读取数的数组
        double[][] readings = (double[][]) databaseArray[0];
        // 初始化返回的数组
        double value = 0;
        // switch-case 确定所需的参数
        switch (parameter) {
            case "Temperature":
                value = readings[0][0];
                break;
            case "wind speed":
                value = readings[0][1];
                break;
            case "Wind Direction":
                value = readings[0][2];
                break;
            case "Pressure":
                value = readings[0][3];
                break;
            case "Visibility":
                value = readings[0][4];
                break;
            case "Humidity":
                value = readings[0][5];
                break;
            case "Cloudiness":
                value = readings[0][6];
                break;
        }

        // 创建一个新的 JSON 对象并存储要返回的值
        JSONObject res = new JSONObject();
        res.put("value", value);
        // 获取 PrintWriter 并设置内容类型为 JSON
        PrintWriter out = new PrintWriter(response);
        response.setContentType("application/JSON");
        response.setCharacterEncoding("UTF-8");
        // 将 JSON 写入用户并关闭连接
        out.print(res.toString());
        out.flush();
        out.close();
    }
}
```

