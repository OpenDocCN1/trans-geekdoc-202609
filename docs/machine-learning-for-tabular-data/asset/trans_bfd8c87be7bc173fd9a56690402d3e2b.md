
[PAGE 376]

## 第 9 章 深度学习实践

训练好的模型，特别是当你正在处理深度学习的需求时。在那个期间，你可能会忘记模型在部署后哪些数据是可用的。通过几个数据点来运行训练好的模型，是揭示项目潜在**数据泄露**的一种简单方法。此的原因是，运行模型将迫使你思考新的数据点看起来像什么样。

- 它提供了一种在测试数数据集上验证模型性能的方法。例如，如果你用来自吉隆坡房地产市场的一些全新数据点来运行模型，你就可以判断模型在测试数据集上的性能与其在处理全新数据点时的性能是否一致。

为了说明在新的几个真实世界示例上运行训练好的模型如何帮助防止数据泄露，让我们来看看如何运行模型来预测一个全新的房源的销售价格是高于还是低于吉隆坡的中位数价格。对于吉隆坡房地产数据集，假设有一列名为 `Weeks on the market`（上市周数）的列，它记录了房产在出售之前上市的周数。如果我们在模型训练中包含了这一列，那么当我们尝试用几个新数据点来运行训练好的模型时会发生什么？图 9.18 展示了我们可能遇到的问题。

## 用于训练模型的特征

## 当前吉隆坡房地产房源

| 分类：# 分类列 |
| :--- | :--- |
| 1 | 'Location'（位置） |
| 2 | 'Property Type'（房产类型） |
| 3 | 'Furnishing'（装修） |
| 4 | 'Size_type_bin'（尺寸分箱） |
| 5 | 'Bathrooms'（浴室数） |
| 6 | 'Car Parks'（停车位） |
| 7 | 'Rooms'（房间数） |
| 8 | 'Size'（面积） |
| 9 | 'Weeks on the market'（上市周数） |

RM 450,000
1 5 4 8
3m 2 950 sqft RM 473.68 psf
预计月供 RM 1,846 检查您的承受能力
酒店列出 卖家
Sentul, Kuala Lumpur
发现更多关于吉隆坡该地区的信息

![](img/def89cc476fa39f4c54bd34e78d91674_376_0.png)

| 细节 |
| :--- |
| 房产类型 面积 |
| 950 sqft |
| 公寓出售 |
| 房产类型 价格 |
| 区分产权 RM 473.68 psf |
| 装修 楼层 |
| 部分装修 高楼层 |
| 土地类型 |
| 非租赁权 |
| 建筑年份 房源 ID |
| 无 |

![](img/def89cc476fa39f4c54bd34e78d91674_376_1.png)

**图 9.18** 使用新数据点验证用于训练模型的特征

[PAGE 377]

## 运行深度学习模型

在 9.18 的左侧，我们有在配置文件中指定的训练模型特征列表，包括 `Weeks on the market`（上市周数）特征。右侧是吉隆坡房地产房源的一个摘录。如果我们想要使用训练好的模型为右侧的所有侧特征找到值。

如 9.18 中的数字所示，对于我们用于训练模型的大多数特征，但有两个特征我们无法从房地产房源中获取值：

- `Car Parks`（停车位）——这个特定的房源提到了整栋建筑有覆盖停车位，但没有包含该特定单元停车位的信息。为了进行快速测试，我们可以假设该房源的 `Car Parks` 值为 0。

- `Weeks on the market`（上市周数）——房源未包含它在出售之前上市的周数，在房源售出之前，我们无法知道这个值。我们不能在训练过程中包含 `Weeks on the market`。

现在我们已经解释了为什么在少数几个真实数据点上运行训练好的模型是重要的，我们我们将在下一个小节中回顾运行模型的代码。

## 9.5.2 在一些新数据点上运行训练好的模型

现在我们已经建立了在新的数据点上运行训练好的模型的益处，让我们查看执行此操作的代码。

下面的列表显示了将模型保存到文件系统的代码，通过指定所有用于训练和运行模型的特征值来定义一个新的数据点，并在新数据点上运行模型。

> 列表 9.19 在新数据点上运行训练模型的代码

```python
model_file_name = =
s.path.join(get_model_path(), config['file_names']['saved_model'])
model.save(model_file_name)
loaded_model = \
tf.keras.models.load_model(model_file_name)
sample = {
  'location': 'Dutamas, Kuala Lumpur',
  'rooms': 7.0,
  'property_type': 'Serviced Residence (Intermediate',
  'furnishing': 'Partly Furnished',
  'size_type': 'built-up 1',
  'bathrooms': 1.0,
  'car_parks': 1.0,
  'size': 16805.0,
}
input_dict = \
```

将训练好的模型保存到文件系统，通过指定所有用于训练和运行模型的特征值来定义一个新的数据点，并在新数据点上运行模型

[PAGE 378]

```python
input_dict = {k: v for k, v in sample.items()}
predictions = loaded_model.predict(input_dict)
prob = predictions[0]
print(f"This property has {prob*100:.1f}% probability of being above the median")
```

现在我们已经解释了为什么在少数几个真实数据点上运行训练好的模型是重要的，我们将在下一个小节中回顾运行模型的代码。

现在我们已经建立了在新的数据点上运行训练好的模型的益处，让我们查看执行此操作的代码。

下面的列表显示了将模型保存到文件系统的代码，通过指定所有用于训练和运行模型的特征值来定义一个新的数据点，并在新数据点上运行模型。

> 列表 9.19 在新数据点上运行训练模型的代码

```python
model_file_name = =
s.path.join(get_model_path(), config['file_names']['saved_model'])
model.save(model_file_name)
loaded_model = \
tf.keras.models.load_model(model_file_name)
sample = {
  'location': 'Dutamas, Kuala Lumpur',
  'rooms': 7.0,
  'property_type': 'Serviced Residence (Intermediate',
  'furnishing': 'Partly Furnished',
  'size_type': 'built-up 1',
  'bathrooms': 1.0,
  'car_parks': 1.0,
  'size': 16805.0,
}
input_dict = \
```

将训练好的模型保存到文件系统，通过指定所有用于训练和运行模型的特征值来定义一个新的数据点，并在新数据点上运行模型

```python
input_dict = {k: v for k, v in sample.items()}
predictions = loaded_model.predict(input_dict)
prob = predictions[0]
print(f"This property has {prob*100:.1f}% probability of being above the median")
```

现在我们已经解释了为什么在少数几个真实数据点上运行训练好的模型是重要的，我们将在下一个小节中回顾运行模型的代码。

现在我们已经建立了在新的数据点上运行训练好的模型的益处，让我们查看执行此操作的代码。

下面的列表显示了将模型保存到文件系统的代码，通过指定所有用于训练和运行模型的特征值来定义一个新的数据点，并在新数据点上运行模型。

> 列表 9.19 在新数据点上运行训练模型的代码

```python
model_file_name = =
s.path.join(get_model_path(), config['file_names']['saved_model'])
model.save(model_file_name)
loaded_model = \
tf.keras.models.load_model(model_file_name)
sample = {
  'location': 'Dutamas, Kuala Lumpur',
  'rooms': 7.0,
  'property_type': 'Serviced Residence (Intermediate',
  'furnishing': 'Partly Furnished',
  'size_type': 'built-up 1',
  'bathrooms': 1.0,
  'car_parks': 1.0,
  'size': 16805.0,
}
input_dict = \
```

将训练好的模型保存到文件系统，通过指定所有用于训练和运行模型的特征值来定义一个新的数据点，并在新数据点上运行模型

```python
input_dict = {k: v for k, v in sample.items()}
predictions = loaded_model.predict(input_dict)
prob = predictions[0]
print(f"This property has {prob*100:.1f}% probability of being above the median")
```（注：提供的 OCR 文本在中间是重复且混乱的。我将根据前几页提供的唯一内容提供干净版本。）

