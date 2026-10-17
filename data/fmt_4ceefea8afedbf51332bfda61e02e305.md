
```css
.btn-primary {
  color: #fff;
  background-color: #1d2025;
  border-color: #fffece5;
  margin-bottom: 20px;
  margin-top: 20px;
  font-size: 30px;
}
tbody {
  font-size: 40px ;
}
</style>
```

# 列表 3.60. 为主应用程序标题创建一个表格行

```html
</head>
<body>
<!-- 创建一个包含单行的主表格，并包含一个描述应用程序目的的主标题 -->
<div class="table-responsive">
<table class="table">
<tbody>
<div id="Dataset" class="container">
<table width="100%">
<tr>
<td></td>
```
```html
<table width="100%">
<tr>
<td width="100%" align="left">
<table width="100%">
<hr/>
<tr>
<td width="150px" height="50px" align="center">MACHINE LEARNING ALGORITHMS
</tr>
</table>
<hr/>
</td>
</tr>
</table>
```

# 列表 3.61. 为应用程序中使用的三个算法创建三列

```html
<!-- 添加另一行三列来描述算法的类别 -->
<tr>
<td width="100%" id="dataset">
<table width="100%">
<tr>
<td width="150px" height="100px" align="center">CLASSIFICATION ALGORITHM
<td width="150px" height="100px" align="center">REGRESSION ALGORITHM
<td width="150px" height="100px" align="center">CLUSTER ALGORITHM
</tr>
</table>
<hr/>
</td>
</tr>
```

之后，应用程序的三个主算法链接如列表 3.62 所示：

```html
<!-- 在表格中添加另一行三列以提供 -->
<tr>
<td width="100%" id="dataset">
<table width="100%">
<tr>
<!-- 在 knn.html 中找到 KNN 花卉分类的链接 -->
<td width="150px" height="90px" align="center"><a href="knn.html" class="btn-primary btn-large">KNN-Flower-Classification
</td>
<!-- 在 Polynomial_Regression.html 中找到多项式回归算法的链接 -->
<td width="150px" height="90px" align="center"><a href="Polynomial_Regression.html" class="btn-primary btn-large">Polynomial-Regression-Prediction
</td>
<!-- 在 KMeans_Image.html 中找到 KMeans 图像聚类算法的链接 -->
<td width="150px" height="90px" align="center"><a href="Clustering:KMeans_Image.html" class="btn-primary btn-large">KMeans-Image-Clustering
</td>
</tr>
</table>
<hr/>
</td>
</tr>
</tbody>
</tr>
</table>
</div>
</body>
</html>
```

当运行 `index.html` 文件启动应用程序时，图 3.38 所示的网页将显示在本地主机上。

## 机器学习算法

![](img/2b52fde0e707e8c2f05a10309c3f8982_222_0.png)

图 3.38. 应用程序的主网页。

### 3.7.2. 整合 KNN 花卉分类

为了开发 KNN 分类部分应执行以下步骤：

- 1. 右键点击 `public` 文件夹并创建一个名为 `'knn'` 的文件夹，如下：

![](img/2b52fde0e707e8c2f05a10309c3f8982_222_1.png)

图 3.39. 为 KNN 分类创建文件夹。

- 2. 右键点击 `knn` 文件夹并创建一个名为 `knn.html` 的 HTML 文件，如图 3.40 所示。

212 T. P. Fowdar, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonon

![](img/2b52fde0e707e8c2f05a10309c3f8982_223_0.png)

3.40. 为 KNN 分类部分创建一个 HTML 文件。

- 3. 将 `ml.min.js`、`papaparse.min.js` 和 `plotly_latest.min.js` 文件复制并粘贴到 `knn` 文件夹中，如图 3.41 所示。这些文件可以通过表 3.20 提供的链接获取。

![](img/2b52fde0e707e8c2f05a10309c3f8982_223_1.png)

3.41. 向 `knn` 文件夹添加外部文件。

- 4. 双击 `knn.html` 文件并向其添加列表 3.63 中提供的代码。

# 列表 3.63. 用于基于 KNN 的卉分类的 knn.html 文件

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
<meta charset="utf-8">
<!-- 从各自链接下载后必须存储在 knn 文件夹中的 javascript 文件 -->
<script src="ml.min.js"></script>
<script src="papaparse.min.js"></script>
<script src="plotly-latest.min.js"></script>
<!-- 定义背景和按钮的样式 -->
<style>
```
```html
body {
  background-color: #0f1724;
  color: #00a8ff;
  font-family: 'Abel';
  font-size: 20px;
}
.btn-primary {
  color: #fff;
  background-color: #1d2025;
  border-color: #1ece5;
  margin-bottom: 40px;
  margin-top: 20px;
  font-size: 20px;
}
</style>
</head>
<body>
<h1 style="text-align:center;margin:20px">KNN ALGORITHM</h1>
<div class="container-fluid">
<!-- 为分析浏览 csv 格式数据集的空间 -->
<div class="row">
<div class="col-md-12 col-md-offset-1" align="center">
<div class="col-md-4 btn-primary btn-file" align="center">
<input type="file" name="file" class="inputFile" id="txtFileUpload" accept=".csv" align="center" />
</div>
</div>
</div>
</div>
</div>
<!-- 调用定义 KNN 分类算法的 KNN.js 文件 -->
<script src="KNN.js"></script>
<div class="row" id="firstrow" align="center">
<div class="col-md-1" align="center"><br>
</</div>
<!-- 为花卉分类添加花瓣长度的标签 -->
<div class="col-md-1" align="center"><br>
<label for="x">Sepal_Length:</label>
<input type="number" id="sepalLength" class="form-control" align="center"><br>
</</div>
<!-- 为花卉分类添加用于的花瓣宽度的标签 -->
<div class="col-md-1" align="center"><br>
<label for="x">Sepal_Width:</label>
<input type="number" id="sepalWidth" class="form-control" align="center"><br>
</</div>
</div>
```
```html
<input type="number" id="sepalWidth" class="form-control"
align="center"><br>
</div
<!-- 为花卉分类中的花瓣长度创建标签 -->
<div class="col-md-1" align="center"><br>
<label for="x">Petal_Length:</label>
<input type="number" id="petalLength" class="form-control"
align="center"><br>
</div
<!-- 为花卉分类中的花瓣宽度创建标签 -->
<div class="col-md-1" align="center"><br>
<label for="x">Petal_Width:</label>
<input type="number" id="petalWidth" class="form-control"
align="center"><br>
</div
<!-- 创建一个按钮来调用 KNN.js 脚本中定义的 KNN_CLASSIFY 方法 -->
<div class="col-md-1" align="center"><br>
<button type="button" id="prediction" class="btn-warning
onclick='KNN_CLASSIFY()'>分类</button>
</div><div class="col-md-1" align="center"><br>
</div><div class="col-md-1" align="center"><br>
<!-- 创建输出花卉分类结果的标签 -->
<div class="col-md-2" align="center"><br>
<label for="x">该花卉被分类为:</label>
<input type="text" id="KNN_predictedValue" name="x" class="form-control"
align="center"><br>
</div><div class="col-md-1" align="center"><br>
</div></div><br>
<!-- 创建显示图表的空间 -->
<div id="chart1"></div
<br><br><br>
</div>
</body>
</html>
```

## 机器学习算法

5. 对分析中使用的数据集进行格式化非常重要。从以下地址获取的原始 `iris.csv` 数据集的快照：

https://forge.scilab.org/index.php?p/rdataset/source/tree/master/csv/datasets/iris.csv 如表 3.21 所示：

### 表 3.21. 鸢尾花（Iris）数据集快照

| 萼长度 (Sepal.Length) | 萼宽度 (Sepal.Width) | 花瓣长度 (Petal.Length) | 花瓣宽度 (Petal.Width) | 物物种 (Species) |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 5.1 | 3.5 | 1.4 | 0.2 setosa |
| 2 | 4.9 | 3 | 1.4 | 0.2 setosa |
| 3 | 4.7 | 3.2 | 1.3 | 0.2 setosa |
| 4 | 4.6 | 3.1 | 1.5 | 0.2 setosa |
| 5 | 5 | 3.6 | 1.4 | 0.2 setosa |
| 6 | 5.4 | 3.9 | 1.7 | 0.4 setosa |
| 7 | 4.6 | 3.4 | 1.4 | 0.3 setosa |
| 8 | 5 | 3 | 1.5 | 0.2 setosa |
| 9 | 4.4 | 2.9 | 1.4 | 0.1 setosa |
| 10 | 4.9 | 3.7 | 1.5 | 0.2 setosa |
| 11 | 5.4 | 3.4 | 1.6 | 0.2 setosa |
| 12 | 4.8 | 3 | 1.4 | 0.1 setosa |
| 13 | 4.3 | 3 | 1.1 | 0.2 setosa |
| 14 | 5.8 | 4 | 1.2 | 0.4 setosa |
| 15 | 5.7 | 4.4 | 1.5 | 0.4 setosa |
| 16 | 5.4 | 3.9 | 1.3 | 0.4 setosa |
| 17 | 5.1 | 3.5 | 1.4 | 0.3 setosa |
| 18 | 5.7 | 3.8 | 1.7 | 0.3 setosa |
| 19 | 5.1 | 3.8 | 1.5 | 0.2 setosa |

来源：https://forge.scilab.org/index.php?p/rdataset/source/tree/master/csv/datasets/iris.csv。然而，为了在使用后述的 `KNN.js` 访问字段，必须删除 CSV 的第一列并将列重命名为：

```
Sepal.Length -> Sepal_Length
Petal.Length -> Petal_Length
Sepal.Width -> Sepal_Width
Petal.Width -> Petal_Width
```

这是为了使 JavaScript 中的名称有效。更新后的 CSV 快照见表 3.22。

### 表 3.22. 格式化数据集

| 萼长度 (Sepal_Length) | 萼宽度 (Sepal_Width) | 花瓣长度 (Petal_Length) | 花瓣宽度 (Petal_Width) | 物种 (Species) |
| :--- | :--- | :--- | :--- | :--- |
| 5.1 | 3.5 | 1.4 | 0.2 setosa |
| 4.9 | 3 | 1.4 | 0.2 setosa |
| 4.7 | 3.2 | 1.3 | 0.2 setosa |
| 4.6 | 3.1 | 1.5 | 0.2 setosa |
| 5 | 3.6 | 1.4 | 0.2 setosa |
| 5.4 | 3.9 | 1.7 | 0.4 setosa |
| 4.6 | 3.4 | 1.4 | 0.3 setosa |
| 5 | 3.4 | 1.5 | 0.2 setosa |
| 4.4 | 2.9 | 1.4 | 0.1 setosa |
| 4.9 | 3.7 | 1.5 | 0.2 setosa |
| 5.4 | 3.4 | 1.6 | 0.2 setosa |
| 4.8 | 3 | 1.4 | 0.1 setosa |
| 4.3 | 3 | 1.1 | 0.2 setosa |
| 5.8 | 4 | 1.2 | 0.4 setosa |
| 5.7 | 4.4 | 1.5 | 0.4 setosa |
| 5.4 | 3.9 | 1.3 | 0.4 setosa |
| 5.1 | 3.5 | 1.4 | 0.3 setosa |
| 5.7 | 3.8 | 1.7 | 0.3 setosa |
| 5.1 | 3.8 | 1.5 | 0.3 setosa |

此外，必须使用后述 `KNN.js` 文件使用的 `PapParse.js` 脚本将数据从 `csv` 读取并转换为 `json` 格式。

- 6. 右键点击 `knn` 文件夹，创建一个如图 3.42 所示的名为 `KNN.js` 的新 JavaScript 文件。

![](img/2b52fde0e708c2f05a10309cf8982_227_0.png)

图 3.42 创建 `KNN.js` 文件。

- 7. 双击 `KNN.js` 文件并添加列表 3.64 中提供的代码。程序中使用的概念已改编自 [61]。

## 代码 3.64. 基于 KNN 花卉分类的 KNN.js 文件

```javascript
// 声明存储花卉类型特征的变量。
// 存储 setosa 花卉类型特征的变量：
var l_sepal_length_S = [];
var l_petal_length_S = [];
var l_petal_width_S = [];
var l_sepal_width_S = [];
// 存储 versicolor 花卉类型特征的变量：
var l_sepal_length_Ve = [];
var l_petal_length_Ve = [];
```
