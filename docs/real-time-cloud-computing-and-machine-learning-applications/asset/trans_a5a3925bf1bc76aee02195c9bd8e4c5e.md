

```
mode: 'scatter', //line display type
name: 'trained set', //line label
line: {
color: 'green', //details of the plot
width: 2,
};
```

// 在同一张图上绘制预测点。

```javascript
var trace2 = {
x: [pred], // 预测所需的时间。
y: [pred], // 给定时间的预测值。

mode: 'markers',
name: 'predicted',
line: {
color: 'red',
size: 8
};
```

// 获取最佳拟合曲线的 y 值。

```javascript
var coeffs=[];
```

// 提取最佳拟合曲线方程的系数。

```javascript
coeffs = regression.coefficients;
var liney = [];
var ycof = coeffs[0];
```

// 根据 coeffs 和 xx 数组生成 y 值：

```javascript
for( var i=0; i<xx.length; i++){
	for( var j = 1; j<coeffs.length; j++){
	ycof = (xx[i]**)*coeffs[j] + ycof;
	}
	liney.push(parseFloat([ycof]));
	ycof = coeffs[0];
}
```

// 在同一张图上绘制最佳拟合曲线。

# 230 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonundon

```javascript
var trace3 = {
  x: xx,
  y: 'lines',
  mode: 'best fit',
  line: {
    color: 'blue',
    width: 2
  },
};

// // 最佳拟合曲线的 y 值
// // 线显示类型
// // 线标签
// // 图表详情

var data = [trace1 ,trace2, trace3];
var layout = {
  title: '直线与散点样式'
};
Plotly.newPlot('chart1', data, layout);
```

7. 生成一个包含随机温度值的数据集并将其存储在 CSV 文件中。生成的数据集快见表 3.23。

## 表 3.23. 温度数据集

| | Temp |
|---|---|
| 1 | 19.73 |
| 2 | 20.4 |
| 3 | 19.71 |
| 4 | 19.98 |
| 5 | 20.32 |
| 6 | 19.74 |
| 7 | 20.48 |
| 8 | 19.79 |
| 9 | 20.09 |
| 10 | 19.68 |
| 11 | 20.02 |
| 12 | 20.46 |
| 13 | 19.96 |
| 14 | 20.51 |
| 15 | 19.98 |
| 16 | 20.37 |
| 17 | 19.79 |
| 18 | 19.54 |
| 19 | 19.64 |
| 20 | 19.81 |

## 机器学习算法

当从主应用程序页面点击“多项式回归预测”（Polynomial-Regression-Prediction）时，将显示图 3.50 所示的窗口。

![](img/2b52fde0e707e8c2f05a10309c3f8982_242_0.png)

图 3.50。多项式回归菜单。

要测试该应用程序，首先需要选择数据集文件，然后由用户输入预测区间和多项式次数。之后按下 PREDICT 按钮。典型的输出如图3.51 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_242_1.png)

图 3.51。测试多项式回归应用。

最后还给出了最佳拟合曲线的方程。显示数据集、预测点和最佳拟合曲线的图表也显示在图 3.52 中。

![](img/2b52fde0e707e8c2f05a10309c3f8982_243_0.png)

### ### 3.7.4. 聚类算法链接

为了开发应用程序的 KMeans 聚类部分，应执行以下步骤：

- 1. 在 public文件夹下创建一个名为“Clustering”的文件夹，如图 3.53 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_243_1.png)

图 3.53。为聚类部分创建文件夹。

## 机器学习算法 233

2. 右键点击 Clustering 文件夹并创建一个名为 KMeans_Image.html 的 HTML 文件。同时，从 https://ml.js 获取 ml.js 文件并将其粘贴到 Clustering 文件夹中，如图 3.54 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_244_0.png)

图 3.54。创建 html 文件并添加外部库。

3. 双击 KMeans_Image.html 文件，并将示例 67 中的代码添加到其中。

## 示例 67. 用于聚类的 KMeans_Image.html 文件

```html
<html>
<head>
<title>Means</title>
<script src="ml.js"></script>

<!-- 必须从 ml.js 下载并存储在 Clustering 文件夹中的主机器学习库 -->
<!-- 定义背景和按钮的样式 -->
<style>
body {
  background-color: #0f1724;
  color: #00a8ff;
  font-family: 'Arial';
  font-size: 18px;
}
.btn-primary {
color: #fff;
background-color: #1d2025;
border-color: #ece5;
margin-bottom: 40px;
margin-top: 20px;
font-size: 18px;
}
</style>

<!-- 调用定义 KMeans 算法的 kmeans_image.js 文件 -->
<script src="kmeans_image.js"></script>

</head>

<body>

<h1 style="text-align:center; margin:10px; font-size:20px;">K-MEANS - 聚类</h1>

点击“浏览”按钮将打开文件浏览器并允许一次选择多个图像。点击文件浏览器上的“打开”按钮时，将调用 loadImages() 函数并将选的图像显示在 HTML 页面上。

```html
<div class="col-md-2">
添加图像...<input id="imagefile" type="file" onchange="loadImages(); style="margin-bottom: 10px;font-family: 'Arial';</div>
```

<!-- 添加了调用 kmeans_image.js 文件的聚类函数。聚类函数的作用根据用户指定的数量使用 kmeans 算法将相似图像分组 [63] -->

```html
<div class="col-md-1">
<br>
<button onclick="clusterimages()" style="font-weight:lighter; color:black;">聚类图像</button>
<select id="selectK" onchange="clusterimages();" style="font-weight:bold;">
<option value="2">2</option>
<option value="3">3</option>
```

## 机器学习算法 235

```html
<option value="4">4</option>
<option value="5">5</option>
<option value="6">6</option>
<option value="7">7</option>

</select>

组

<div><br><br>

<!-- 添加了调用 kmeans_image.js 文件 reset() 函数的重置按钮。reset() 函数的作用是清除列表中已添加的图像，以便添加另一个列表进行分析 -->

```html
<div class="btn btn-success">
<button onclick="reset();" style="margin-top: 20px;">重置</button>
</div>
```

<!-- 创建一个显示已添加图像图标 -->

```html
<div id="images" style="position:relative;">
</div>
<br>
<canvas id="canvas" width="4" height="4" style="display:bottom;"></canvas>
<br>
```

```html
</body>
</html>
```

5. 右键点击 Clustering 文件夹并创建一个名为 kmeans_image.js 的新 javascript 文件，如图 3.55 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_246_0.png)

图 3.55。创建 kmeans_image.js 文件。

236 T. P. Fowdar, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonman

6. 双击 kmeans_image.js 文件并将示例 68 中的代码添加到其中。这些代码基于 [63] 中给出的示例。

## 示例 68. 用于聚类的 kmeans_image.js 文件

```javascript
// 用于保存数据集数据的数组变量。
var data = new Array();

// 点击“浏览”按钮将打开文件浏览器并允许一次选择多张图像。当点击文件浏览器上的“打开”按钮时，将调用 loadImages() 函数并将选的图像显示在 HTML 页面上 [63]。

function loadImages() {
  reset();
}
// 该函数遍历所有选中的文件，并顺序在 id 为 'img' 的 <div> 标签中显示图像。

for (var i = 0; i < imagefile.files.length; i++) {
  var fileReader = new FileReader();

  // 为文件读取操作结束的 onload = function(e) 准备回调 [63];

  fileReader.onload = function(e) {
    var imageData = new Uint8Array(e.target.result);
    var blob = new Blob([imageData], {
      type: "image/jpeg"
    });
    var url = URL.createObjectURL(blob);

    var img = new Image();
    img.onload = function() {


// 在画布上绘制图像的同时将其分辨率降低到 4x4 像素 [63]

var context = canvas.getContext("2d");

if (img.width > img.height) {
  context.drawImage(img, 0, 0, img.width, img.height, 0, 0, canvas.width,
```

