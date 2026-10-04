

# 460 T. P. Fowdur, L. Babooram, M. N-U-D-ibn Naz Rosun 和 M. Indoonadon

意味着每次更新时需要进行较小的更改，因此分析需要更长的时间。

- 轮数（Epochs）：PC 的值在较少的轮数下即可产生最佳百分百分率，进一步增加则不会影响准确率。为了节省预测时间，将其保持在较低水平。但 Android 数据库的情况并非如此，它们需要遍历整个数据集进行更多轮循环。
- 动量和隐藏层（Momentum and hidden layers）：动量控制梯度下降更新，这两个超参数都是根据预测的准确率来选择的。

列表 5.15 涉及使用 `dataRaw` 对象对 Android 手机或桌面 PC 的 Wi-Fi 文件进行 MLP 分类。如果用户希望使用 LTE 速度进行分类，则对移动数据遵循相同的流程。这是通过使用 `dataRaw` 对象并调用 `MLPClassification()` 方法实现的。后者的代码在算法超参数方面有所不同，可在书籍网站上提供。

# 列表 5.15 在 PC 和 Android 上执行 MLP 分类

```java
public void MLPClassification() throws Exception {
// 使用 Weka 库创建一个多层感知器对象
MultilayerPerceptron mlp = new MultilayerPerceptron();
// 创建一个 Instance 对象来存储从云端加载的值
Instances train = new Instances(dataRaw);

try {
train.setIndex(train.numAttributes() - 1);
if (analysisDevice.getSelectedItem().toString().equals("PC
```

# 基于云的实时服务器和 Servlet 架构 . 466

```
}
// 使用 Weka 库创建评估对象以检索训练摘要
Evaluation eval = new Evaluation(train);
// Weka 允许通过传递算法和
//训练数据集对模型进行评估：
eval.evaluateModel(mlp, train);
// 打印相关系数、平均绝对误差、均方误差、相对绝对误差、均方误差以及
// 实例总数
System.out.println("Training Summary:");
System.out.println(eval.toSummaryString());

// 比较预测值和实际值
System.out.println("Predicted vs actual");
// 获取分类错误实例数量的变量
double error = 0.0;
// 遍历整个数据集
for (int i = 0; i < dataRaw.numInstances(); i++) {
// 分类行并舍入到最近的整数
double prediction = Math.round(mlp.classify(dataRaw.instance(i)));
double actual = dataRaw.instance(i).getValue();
// 比较预测值与实际值
if (prediction != actual) {
// 预测错误
errorCount = errorCount + 1;
System.out.println("Row " + i + " Actual: " + actual + " Prediction: "
+ prediction + " --- Incorrect prediction");
} else {
// 正确预测
System.out.println("Row " + i + " Actual: " + actual + " Prediction: "
+ prediction);
}

System.out.println("Error Count: " + errorCount);

// 计算准确率
double percentageAccuracy = 100 - (errorCount / dataRaw.numInstances()) * 100;
System.out.println("Accuracy for MLP: " + percentageAccuracy + "%");
// 使用获得的值更新 GUI
accuracy.setText("Accuracy: " +
String.valueOf(ofNumberFormat.format(percentageAccuracy)) + "%");
// 从 GUI 获取用户输入字段的必要值
ddspeed = Double.parseDouble(tdspeed.getText().toString());
uspeed = Double.parseDouble(tspeed.getText().toString());
prec = Double.parseDouble(pacrec.getText().toString());
```

462 T. P. Fowdur, L. Babooram, M. N-U-D-ibn Naz Rosun 和 M. Indoondan

```
sent = Double.parseDouble(pascent.getText().toString());
// 设置一个伪标签类别
double[] values = new double[]{speed, prec, sent, 1};
// 将 double [] 对象传递给 DenseInstance 对象
DenseInstance testInstance = new DenseInstance(1.0, values);
// 分类输入值
classificationMLP = mlp.classifyInstance(testInstance);
System.out.println("Closest classification: " + classificationMLP);

// 使用获得的值更新 GUI
System.out.println("Category for GUI: " + Math.round(classificationMLP));
if (Math.round(classificationMLP) == 1) {
    System.out.println("Client is idle.");
    predictedValue.setText("Prediction: " + "idle.");
}
if (Math.round(classificationMLP) == 2) {
    System.out.println("Client is browsing.");
    predictedValue.setText("Prediction: " + "browsing.");
}
if (Math.round(classificationMLP) == 3) {
    System.out.println("Client is streaming.");
    predictedValue.setText("Prediction: " + "streaming.");
}

## 5.1.12. 回归

本节涉及线性回归 (MLR) 和多层感知器 (MLP) 回归，它们被用于 PC 和 Android 设备。回归的主要目标是使用特定的窗口大小预测特定时间的结果。因此，网络参数在用户执行不同活动期间变化很大。例如，如果用户正在观看 YouTube，缓冲系统的工作方式是视频在几秒钟内下载。随后下载速度急剧下降导致回归算法失败。由于这个原因，选择了“streaming”活动来记录回归参数。结果，云数据库包含了较小范围的值。表 5.13 显示了用于回归分析的典型“streaming”值。

# 基于云的实时服务器和 Servlet 架构 . 463

# 表 5.13. 用于回归分析的 streaming 数据示例

| Key | 下载速度 | 上传速度 | 接收包 | 发包 |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 1063 | 16 | 792 | 298 |
| 2 | 1595 | 25 | 1512 | 416 |
| 3 | 1471 | 22 | 1094 | 401 |
| 4 | 1691 | 29 | 1246 | 480 |
| 5 | 1618 | 27 | 1204 | 468 |
| 6 | 1660 | 26 | 1239 | 474 |

## 5.1.12.1. 使用滑动窗口方法

本章中的回归算法围绕滑动窗口方法（也称为滚动窗口）展开。对于短时间序列预测是高效的，因为软件接收用户输入的特定预测时间值。考虑以下场景，它由从“laptopcloudparameters”数据集中提取的“接收包”值组成：

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

