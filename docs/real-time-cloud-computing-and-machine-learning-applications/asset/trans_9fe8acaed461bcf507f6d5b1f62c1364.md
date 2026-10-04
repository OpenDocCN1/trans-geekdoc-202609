
基于云的实时...服务器与 Servlet 架构 ... 737

- - trainModel (int maxEpoch)

该方法使用反向传播技术训练 CNN 模型。CNN 反向传播的超参数总结在表 7.22 中。

# 表 7.22. CNN 超参数

| 超参数 | 数值 |
|---|---|
| 最大误差 | 0.001f |
| 最大迭代次数 | 用户设置 (1000) |
| 学习率 | 0.01f |
| 动量 | 0.5f |

- - predictNext ()

该方法用于预测未来 15 分钟内的所有天气参数。CNN 网络的输入张量通过 `DataSetIterator` 对象的 `getLastTimestampCNN()` 方法获取。该张量对象用于激活网络。然后使用 `getOutput()` 方法获取输出。随后，输出数组中的前七个元素被反归一化并作为预测值返回。

## 7.1.13. Analytics 方法

所有四个机器学习算法都通过 `analytics()` 方法执行预测。窗口大小和预测时间作为参数传递给该方法。检查 `JJComboBox` 的选定值以验证需要从哪个数据源获取数据。从相应的数据源获取数据后，将为每个算法创建一个模型。使用所有四个模型进行预测。每个模型产生的结果数组被格式化为一位小数，然后存储在 `JSONObject` 中。该方法的代码如列表 7.18 所示。

# 列表 7.18. 使用所有算法进行预测

```java
public JSONObject analytics(int r_window, int pred_t) {

  //神经网络的数据窗口
int window = 4 * 24 * 7;
int tf = 1;
double[][] network_data, regress_data;
float[][] converted;
//检查数据源 JComboBox 的值
```

738 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosum 和 M. Indoonoon

```java
String temp = (String) db_src.getSelectedItem();
if (temp.equals("Local Database")) {
//连接到本地数据库获取数据
  myConnector = new SQLConnector();
  //提取数据
  network_data = (double[][])myConnector.fetchLastN(window)[0];
  regress_data = (double[][])myConnector.fetchLastN(r_window)[0];
  //将数组转换为 float
} else {
  //创建一个 DataRetriever 从云端获取数据
  DataRetriever = new DataRetriever();
  //提取数据
  network_data = (double[][])dataRetriever.getDatabaseArray("", window)[0];
  regress_data = (double[][])dataRetriever.getDatabaseArray("", r_window)[0];
  //将数组转换为 float
}
converted = convertToFloat(network_data);
System.out.println("Net data length: " + network_data.length);
///// 使用 ML 和多项式回归进行预测 //////
RegressionRegressor regress = new RegressionRegressor(regress_data);
double[] poly_p = regress_data.polynomialPredict(pred_t, r_window);
double[] mult_p = regress_data.multilinearPredict(pred_t, r_window); //////
///// 使用卷积网络进行预测 //////
CNNRegression conn = new CNNRegression(converted, tf, tn);
CNN.trainModel(100);
float[] cnn_p = CNN.predictNext();
n///// 使用 MLP 网络进行预测 //////
float[] mlp_p = new float[7];
for (int i = 0; i < 7; i++) {
  MLPRegression MLP = new MLPRegression(converted, tf, tn);
  mlp_p[i] = MLP.predictNext(1000, i);
}
//将神经网络输出四舍五入到位小数
roundOutput(mlp_p);
roundOutput(cnn_p);

//创建一个新的 JSON 对象返回
JSONObject output = new JSONObject();
//将结果存储在 JSON 对象中
output.put("Multiple Linear Regression", mult_p);
output.put("Polynomial Regression", poly_p);
output.put("Convolutional Network", cnn_p);
output.put("Multilayer Perceptron", mlp_p);
```

return output;
```

基于云的实时...服务器与 Servlet 架构 ... 739

## 7.1.14. predictActionPerformed () 方法

当点击“预测”按钮时，会调用 `predictActionPerformed()` 方法。创建一个匿名线程，以防止神经网络训练和回归模型创建阻塞主线程。窗口大小和预测时间从适当的 `JTextField` 中获取。调用 `analytics()` 方法以获取预测结果。使用 `formatData()` 方法将 `JSONObject` 格式化为更易读的格式。该方法的代码如列表 7.19 所示。

# 列表 7.19. predictActionPerformed () 方法

```java
private void predictActionPerformed(java.awt.Event event) {
  new Thread(() -> {
    //回归模型的窗口
    int r_window = Integer.parseInt(window_s.getText());
    int pred_t = Integer.parseInt(ptime.getText());
    //使用 analytics() 方法执行分析
    JSONObject analytics = analytics(window, pred);
    //将结果格式化为可读形式
    String formatted = formatData(analytics);
    //显示结果
    result.setText(formatted);
  }).start();
```

## 7.1.15. 将输出四舍五入到位

为了将输出四舍五入到一位小数，使用了 `roundOutput()` 方法。`mlp_p` 和 `cnn_p` 都经过了处理。

## 7.1.16. 将 double 数组转换为 float

由于 `ConvertToFloat` 方法接收 double 类型的数组，因此需要将其转换为 float 数组。

## 7.1.17. 格式化返回的 JSONObject

`analytics()` 方法返回一个包含算法名称的 `JSONObject`。为了显示结果，需要将数据格式化为更易读的格式。
