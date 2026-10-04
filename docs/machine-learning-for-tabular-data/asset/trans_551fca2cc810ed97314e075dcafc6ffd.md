
# Listing 10.7 getOption JavaScript 函数

```javascript
function getOption() {
  selectElementlocation = document.querySelector('#location');
  selectElementproperty = document.querySelector('#property-type');
  selectElementfurnishing = document.querySelector('#furnishing');
  selectElementsizetype = document.querySelector('#size-type');
  rooms_value = document.getElementById('rooms').value;
  bathroom_value = document.getElementById('bathrooms').value;
  car_parks_value = document.getElementById('car-parks').value;
  size_value = document.getElementById('size').value;
  location_string = selectElementlocation.selectedIndex;
  property_type_string = selectElementproperty.type;
  options[selectElementproperty.selectedIndex].value;
  furnishing_string = options[selectElementfurnishing.selectedIndex].value;
  size_type = selectElementsizetype.type;
  options[selectElementsizetype.selectedIndex].value;
  prefix = "show-prediction/";
  window.output = prefix.concat("location=",location_string,"&rooms=",rooms_value,"&property_type=",property_type_string,"&furnishing=",furnishing_string,"&size_type=",size_type,"&bathrooms=",bathroom_value,"&car_parks=",car_parks_value,"&size=",size_value);
  document.querySelector('.output').textContent = window.output;
}
```

> 获取位置字段选择列表中选中的条目

> 获取房间字段中输入的值

> 获取位置字段选择列表中选中条目的值

列表 10.7 中的 getOption() JavaScript 函数执行了以下操作：

- 从连续字段加载值：房间（rooms）、浴室（bathrooms）、车位和面积（size）。
- 加载分类字段中的选中条目：位置（location）、属性类型（property-type）、furnishing）和面积类型（size-type）。
- 构建查询字符串。查询字符串格式如下：

`/show-prediction/?location=KLCC, Kuala Lumpur&rooms=1&property_type=Serviced Residence&furnishing=Fully Furnished&size_type=Built-upbedrooms&car_parks=0&size=500`

查询字符串包含：

- URL `/show-prediction/`。注意此 URL 匹配列表 10.3 中 Flask 服务器中为 `show-prediction` 视图函数提供视图的装饰器。

```python
@app.route('/show-prediction/')
```

> 将 window.output 的值设置为查询字符串

## 简单的 Web 部署

- 用 `?` 表示查询字符串的开始。
- 一组参数和值对，用于表示为 `home.html` 中每个字段设置的值，并用 `&` 隔开。例如，参数和值对可能如下所示：

```
location=KLCC, Kuala Lumpur
rooms=1
property_type=Serviced Residence
furnishing=Fully Furnished
size_type=Built-up
bathrooms=1
car_parks=0
size=500
```

查询字符串被传递给 Flask 服务器中的 `show-prediction` 视图函数。如 10.3 所示，在该函数中，查询字符串被解析以获取在 home.html 中为每个特征输入的值，这些值被用于从模型获取预测。

## 10.1.4 show-prediction.html 页面

现在我们已经查看了 Flask 服务器和 home.html，Web 部署中还有一个最后一个组件需要检查：show-prediction.html。此页面显示模型对用户在 home.html 中输入的物业做出的预测，并有一个按钮可以将用户带回 home.html，在那里为另一个物业输入值。

### 列表 10.8 show-prediction.html

```html
<!DOCTYPE html>
<head>
  <title>显示预测的页面</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='main.css') }}">
</head>
<body>
<!-- 显示预测 -->
  <div class="home">
    <h1 style="color:green">这是对该吉隆坡物业的预测：</h1>
    <h1 style="color:green">{{ prediction }}</h1>
  </div>
  <!-- 返回 home.html 为另一个预测输入参数 -->
  <form action="{{ url_for('home') }}">
    <input type="submit" value="Get another prediction" style="font-size: 20px; width: 40%; height: 30px;"/>
  </form>
```

如 10.8 所示，show-prediction.html 不包含任何 JavaScript 函数。页面的 HTML 定义了出现在页面上的文本，而“Get Another Prediction”按钮则将用户返回到 home.html。图 10.4 显示了本节中讨论的元素在 show-prediction.html 中的显示方式。

![](img/def89cc476fa394c54bd34e78d91674_392_0.png)

图 10.4 show-prediction.html 中的关键元素

现在我们已经检查了 Web 部署的所有组件，我们将回顾简单部署我们模型的理由。

## 10.1.5 练习 Web 部署

现在我们已经过过了构成 Web 部署的组件，下一步是查看部署的运行。为了练习 Web 部署：

- 在你的本地系统上创建一个部署并克隆仓库 https://github.com/
