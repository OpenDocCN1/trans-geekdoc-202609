

# 云端实时... 服务器与 Servlet 架构 ... 703

## 7.1.5.4. insertIntoDatabase() 方法

该方法用于在本地数据库中插入新记录。它接受一个来自边缘设备的 JSONObject 输入。JSONObject 中的单个参数从插入查询语句中提取。要插入新记录，执行以下步骤：

- 提取天气参数。
- 从 `Connection` 对象创建语句（Statement）。
- 构建插入数据的查询并使用 `executeUpdate()` 方法进行执行。

该方法的代码见列表 7.11。

## 列表 7.11. insertIntoDatabase() 方法

```java
public void insertIntoDatabase(JSONObject data) {
  try {
    // 从 JSONObject 中获取单个读数以构建查询语句
    double temperature = data.getDouble("Temperature");
    double wind_speed = data.getDouble("Wind Speed");
    double wind_direction = data.getDouble("Wind Direction");
    double cloudiness = data.getDouble("Cloudiness");
    double visibility = data.getDouble("Visibility");
    double humidity = data.getDouble("Humidity");
    double pressure = data.getDouble("Pressure");
    String timestamp = data.getString("Time");

    // 创建用于数据库 SQL 语句的 Statement 对象
    Statement st = conn.createStatement();
    // 创建查询以用提取出的值填充表并执行
    st.executeUpdate("INSERT INTO weather_params VALUES ("
      + "'" + timestamp + '\''
```

## 7.1.6. DataRetriever 类

下一节讨论了用于预测的算法细节以及每个算法相关的代码。数据首先从 Cloudant 数据库获取。这是通过“DataRetriever”类完成的。DataRetriever 类的主要功能是建立到 Cloudant 数据库的远程连接，并获取天气读数的最新记录。该类的操作已在 6.3.30 至 6.3.33 节中进行了总结。

## 7.1.7. Regression 类

该类负责创建用于预测的线性回归或多项式回归模型。要使用该类，首先要创建一个 Regression 对象。使用 `setType()` 方法通过字符串指定回归类型。如果需要多项式回归模型，则使用 `setDegree()` 方法指定模型的阶数。然后，使用 `setWindow()` 方法设置窗口大小。最后，使用 `predict()` 方法进行预测。该方法接收两个数组和一个代表预测时间的整数作为输入，然后输出预测值。该类的方法见表 7.7，并附带了它们实现的功能描述。

## 表 7.7. 回归方法

| 方法 | 描述 |
| --- | --- |
| setType (String type) | 根据字符串类型设置所需的回归模型类型。"Polynomial" – 多项式回归模型，“Linear" – 多元线性回归 (MLR) 模型 |
| setDegree (int degree) | 设置回归模型的阶数。 |
| setWindow (int window) | 设置回归模型的窗口大小。 |
| predict(double[] var1,double[] var2,int time) | 使用两个数组作为输入输出数据，预测该时间的下一个值。 |

## 7.1.8. 使用 Regression 类进行预测

本节解释了获取时间 $t = t + n$ 时每个天气参数的预测读数的执行步骤。为了预测未来值，可以使用多元线性回归（MLR）或多项式回归模型。模型矩阵 $X$ 的生成取决于回归模型的类型。

## 7.1.8.1. 用于气象数据的多元线性回归模型

本节讨论了每个待预测变量的 MLR 方程。该方程涉及一个通用变量 $V_1$，在时间 $t + n$ 时预测，相对于时间 $t$ 时之前记录的 $V_1$ 值以及另一个相关参数 $V_x$。方程按照以下通用组合公式：

$V_{t+n} = \beta_0 + \beta_1 V_{t+n-1} + \beta_2 Vx_{t+n-1} \quad (7.1)$

其中，

- $Vx_t$ 表示影响 $V1_t$ 值的另一个相关参数。
- $\beta_0, \beta_1, \beta_2$ 是为大小为 $W$ 的保持 12 小时的训练窗口确定的系数。这些系数每 12 小时计算一次，以通过新记录的值重新校准模型。

使用上述模型，获得了一个七个方程列表。例如，预测时间 $t + n$ 时温度值的 MLR 方程如下：

$T_{t+n} = \beta_0 + \beta_1 H_{t+n-1} + \beta_2 T_{t+n-1} \quad (7.2)$

时间间隔 $t + 1$ 的温度值是根据之前的温度值 $T_t$ 和之前的湿度值 $H_t$ 计算得。系数 $\beta_0, \beta_1 \& \beta_2$ 来自于使用训练窗口 $W$ 的多元线性回归模型。用于表示天气参数的符号见表 7.8 和表 7.9 的详情。

## 表 7.8. 参数符号

| 参数 | 符号 |
| --- | --- |
| 温度 (Temperature) | $T$ |
| 风速 (Wind Speed) | $W^S$ |
| 风向 (Wind Direction) | $W^D$ |
| 压力 (Pressure) | $P$ |
| 能见度 (Visibility) | $V$ |
| 湿度 (Humidity) | $H$ |
| 云量 (Cloudiness) | $C$ |

## 表 7.9. MLR 方程

| 因变量 | 自变量 | 方程 |
| --- | --- | --- |
| 温度 | 温度 | 湿度 | $\beta_0 + \beta_1 T_t + \beta_2 H_t$ |
| 风速 | 风速 | 温度 | $\beta_0 + \beta_1 W_t^S + \beta_2 T_t$ |
| 风向 | 风向 | 温度 | $\beta_0 + \beta_1 W_t^D + \beta_2 T_t$ |
| 压力 | 压力 | 温度 | $\beta_0 + \beta_1 P_t + \beta_2 T_t$ |
| 能见度 | 能见度 | 云 | $\beta_0 + \beta_1 V_t + \beta_2 H_t$ |
| 湿度 | 湿度 | 温度 | $\beta_0 + \beta_1 H_t + \beta_2 T_t$ |
| 云量 | 云量 | |

对于多元线性回归模型，执行以下步骤：

1. 从第二个[列]中创建响应数组 $y$。
2. 设计矩阵 $X$ 为。
3. 使用设计矩阵 $X$ 创建一个 `MultipleLinearRegression` 模型。
4. 使用以下方程计算回归系数：

```
$\beta = (X^T X)^{-1}(X^T y) = ((QR)^T (QR))^{-1}((QR)^T y) = (R^T R)^{-1}Q^T y = R^{-1}Q^T y \quad (7.4)$
```

5. 使用简单回归模型获取时间间隔 $t+1$ 时每个自变量 $Vx_t$ 的值。
6. 使用方程计算预测值：

```
$R\beta = Q^T y \quad (7.5)$

## 7.1.8.2. 用于气象数据的多项式回归模型

当因变量与解释变量之间的关系可以用 $i$ 阶多项式表示时，使用多项式回归模型。图 7.9 显示了黑线表示的小时温度读取，红色虚线表示三次回归线（$i=3$），用于预测下一次温度读取。多项式回归线的方程和决定系数也显示在图 7.9 的图中。

![](img/2b52fde0e707e8c2f05a10309c3f8982_718_0.png)

图 7.9. 温度的多项式回归。

单变量的 $i$ 阶多项式可以表示为：

```
$y = \beta_0 + \beta_1X^1 + \beta_2X^2 + \dots + \beta_iX^i + \epsilon \quad (7.6)$
```

其中，

- $y$ - 因变量的预测值
- $\beta_0$ - y 截距（当所有其他参数设置为零时 $y$ 的值）

