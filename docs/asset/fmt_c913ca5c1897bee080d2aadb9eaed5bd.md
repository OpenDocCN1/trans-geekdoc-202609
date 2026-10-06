
# 基于云的实时服务器和 Servlet 架构

## 表 5.13. 用于回归分析的 streaming 数据示例

| Key | 下载速度 | 上传速度 | 接收包 | 发包 |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 1063 | 16 | 792 | 298 |
| 2 | 1595 | 25 | 1512 | 416 |
| 3 | 1471 | 22 | 1094 | 401 |
| 4 | 1691 | 29 | 1246 | 480 |
| 5 | 1618 | 27 | 1204 | 468 |
| 6 | 1660 | 26 | 1239 | 474 |

### 5.1.12.1. 使用滑动窗口方法

本章中的回归算法围绕滑动窗口方法（也称为滚动窗口）展开。对于短时间序列预测是高效的，因为软件接收用户输入的特定预测时间值。考虑以下场景，它由从`laptopcloudparameters`数据集中提取的`接收包`值组成：

- 窗口大小 = 5
- 预测时间 = 2

滑动窗口如图 5.16 所示。

| (独立变量) | (依赖变量) | (独立变量) | 预测接收包数量 (y) |
| :--- | :--- | :--- | :--- |
| 下载速度 | 接收包 | 上传速度 | |
| n: 1 | x:1063.0 | y: 792.0 | z: 16.0 | 第 7 行的实际值为：1210.0 |
| n: 2 | x:1595.0 | y: 1512.0 | z: 25.0 | 第 7 行的预测值为：1163.6 |
| n: 3 | x:1471.0 | y: 1216.0 | z: 22.0 | |
| n: 4 | x:1691.0 | y: 1216.0 | z: 29.0 | |
| n: 5 | x:1618.0 | y: 1204.0 | z: 27.0 | |
| n: 2 | x:1595.0 | y: 1512.0 | z: 25.0 | 第 8 行的实际值为：1179.0 |
| n: 3 | x:1471.0 | y: 1216.0 | z: 22.0 | 第 8 行的预测值为：1253.0 |
| n: 4 | x:1691.0 | y: 1216.0 | z: 29.0 | |
| n: 5 | x:1618.0 | y: 1204.0 | z: 27.0 | |
| n: 6 | x:1660.0 | y: 1239.0 | z: 26.0 | |
| n: 3 | x:1471.0 | y: 1094.0 | z: 22.0 | 第 9 行的实际值为：1189.0 |
| n: 4 | x:1691.0 | y: 1216.0 | z: 29.0 | 第 9 行的预测值为：1192.2 |
| n: 5 | x:1618.0 | y: 1204.0 | z: 27.0 | |
| n: 6 | x:1660.0 | y: 1239.0 | z: 26.0 | |

图 5.15. 一般概念通过图 5.17 解释得更清楚，该图显示了下载速度和上传速度列中的前五个独立变量被输入算法，同时将预测的（窗口大小+预测时间）值设置为变量。滑动窗口然后

### 5.1.12.2. 填充云数据库

首先使用本地服务器接收来自 PC 和 Android 设备的值，并将默认数据库分别设置为 `laptopparameters` 和 `androidcloudparameters`。如上一节所述，它们都仅包含流值。因此，使用`推送到云端`开关会将值切换到这些数据库中。

### 5.1.12.3. 从 Cloudant 数据库检索流式值

在研究回归分析的编码方面之前，获取过程由表 5.14 汇总的方法执行执行。

#### 表 5.14. 用于获取回归分析参数的方法

| 设备 | 方法 | 获取的参数数量 |
| --- | --- | --- |
| PC | `fetchRegressionValuesPC()` | 4 |
| Android | `fetchRegressionValuesAndroid()` | 7 |

这两个方法均在`预测`按钮中被调用，并如第 5.110 节所示定义在 `LocServer.java` 中。列表 5.16 执行的功能与第 5.112.2 节解释的 `fetchClassificationValues()` 方法相同，但还考虑了 `timestamp[]` 变量，以便值可以按日期排序，然后下载并显示在 GUI 上。

> 列表 5.16. 从 Cloudant 或 localhost 获取 PC 的回归值

```java
public void fetchRegressionValuesPC() {
// 检查 localhost 开关是否启用
if (localhostAnalysis.isSelected() || fetchRegressionPC) {
    fetchRegressionPC = false;
```

```java
ResultSet resultSet = null;
try {
    Class.forName("com.mysql.jdbc.Driver");
    // 通过指定数据库、用户名和密码创建到 localhost 的连接
    Connection m_Connection = (Connection);
    DriverManager.getConnection("jdbc:mysql://localhost:3306/network", "root");
    // 使用 Statement 类创建一个用于查询的对象
    Statement m_Statement = (Statement) m_Connection.createStatement();
    // 创建类型查询对象
    String query = "SELECT * FROM laptopression";
    // 执行查询并获取结果
    ResultSet resultSet = m_Statement.executeQuery(query);
} catch (ClassException | SQLException ex) {
    Logger.getLogger(LogServer.class.getName()).log(Level.SEVERE, null, ex);
}
// 确定获取的结果集大小
if (resultSet != null) {
    resultSet.last();
    numitems = resultSet.getRow(); // 获取数据的大小
    resultSet.absolute(0); // 将光标移动到集合开始处
} catch (SQLException ex) {
    Logger.getLogger(LogServer.class.getName()).log(Level.SEVERE, null, ex);
}
// 根据获取的项目数量初始化数组
keys = new double[(int) numitems];
downspeed = new double[(int) numitems];
upspeed = new double[(int) numitems];
pacRec = new double[(int) numitems];
pacSent = new double[(int) numitems];
testamp = new String[(int) numitems];
int count = 0; // 用于遍历数据集的计数
try {
    while (resultSet != null && resultSet.next()) {
        // 填充相应的值
        keys[count] = Double.parseDouble(resultSet.getString(1));
        downspeed[count] = Double.parseDouble(resultSet.getString(2));
        upspeed[count] = Double.parseDouble(resultSet.getString(3));
        pacRec[count] = Double.parseDouble(resultSet.getString(4));
```

```java
pacSent[count] = Double.parseDouble(resultSet.getString(5));
testamp[count] = resultSet.getString(6);
// 遍历整个数据集
count = count + 1;
}
System.out.println("Arrays filled from localhost - PC.");
} catch (SQLException ex) {
    Logger.getLogger(logServer.class.getName()).log(Level.SEVERE, null, ex);
} else {
// 连接到云凭据
try {
    client = ClientBuilder.url(new URL("https://8118bf82-4f01-4173-be30-7fe6ff8e7d7-bleuemix.cloud.com/"))
        .username("apikey-5c53-2ef26874d46facab6a91ca3507c1a5")
        .password("a8ec2648edef2d97774e07402f86bddc9a6")
        .build();
    System.out.println("Successful connection to cloud...");
} catch (IOException e) {
    System.out.println("Error accessing cloud: " + e);
}
// 获取数据库中的项目数量以便初始化数组ntry {
    Database db = client.database("laptopcloudparameters", false);
    System.out.println("Trying to read all records from database...");
    String query = "{\$select{\"Key\":\$gte:0\},\"fields\":{\"Key\":},"sort{\"Key\":\$desc\"}}\}";

    QueryResult<LinkedTreeMap> queryResult = queryResult.query(query);
    List<LinkedTreeMap> list = queryResult.getDocs();
    if (list.size() > 0) {
        numitems = (double)list.get(0).get("Key");
        System.out.println("Number of documents: " + numitems);
    }
} catch (Exception e) {
    System.out.println("Problem fetching: " + e);
}
// 根据获取的项目初始化数组
keys = new double[(int) numitems];
downspeed = new double[(int) numitems];
upspeed = new double[(int) numitems];
pacRec = new double[(int) numitems];
pacSent = new double[(int) numitems];
```

系数 `β0`, `β1` 和 `β2` 是通过使用训练窗口 `W` 的 MLR（多元线性回归）模型得到的。因此，第 5.1.12.5 节 `Regression()` 方法中的循环包含了整个数据集的滑动窗口机制。

### 5.1.12.5. 执行多元线性回归 (MLR)

使用第 5.1.12.1 节解释的滑动窗口原理，`Regression()` 方法执行以下步骤。同时也使用了上一节解释的逻辑。

- 从 GUI `int` 对象中获取`窗口大小`和`预测时间`的值。
- 初始化数组以存储 SLR 和 MLR 的各自误差。
- 创建一个 `int` 变量，每次迭代滑动窗口移动 1。
- 使用计数器 `i` 创建滑动窗口。
- 在 `x`, `y` 和 `z []` 对象中填充 SLR 的数组。
- 填充 MLR 数组，将独立变量存储在三列数组中。
- 初始化数值之和以及平均窗口的变量。
- 计算每个变量以及时间的每个窗口之和。
- 计算每个变量的相应平均值。
- 初始化用于计算 `Xi` 值平方差和的变量。
- 初始化用于皮尔逊积差相关系数 `r` 的变量。
- 使用平方差和公式计算每个变量的后者。
- 计算 SLR 和 MLR 的系数。
- 使用创建的计数器通过比较预测值与实际值来寻找个体误差。
- 利用最后一个可能的预测窗口来获取用户的预测值。这利用了上述提到的所有步骤，但没有用于遍历整个数据集的 `for` 循环，即仅使用最后一个可能的窗口。

该方法根据代码列表 5.17 实现，其中注释描述了每个代码块的功能。

#### 代码列表 5.17. 使用滑动窗口执行 MLR

```java
public void Regression() {
  // 初始化方法中使用的变量
  int pvalue = 0;
  int window = 0;
  // 填充从边缘设备获取的值
```
