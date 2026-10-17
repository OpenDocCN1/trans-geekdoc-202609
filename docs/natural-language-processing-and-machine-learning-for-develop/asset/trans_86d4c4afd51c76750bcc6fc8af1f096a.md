
IRIS 特征名称：`sepal length (cm)` `sepal width (cm)` `petal length (cm)` `petal width (cm)` 行数：150 列数：4 行和列数：(`150`, 4) 元素总数：600 IRIS 详情：`<class 'pandas.core.frame.DataFrame'>` `RangeIndex: 150 entries, 0 to 149` 数据列（共 4 列）：`sepal length (cm)` 150 个非空 float64 `sepal width (cm)` 150 个非空 float64 `petal length (cm)` 150 个非空 float64 `petal width (cm)` 150 个非空 float64 `dtypes: float64(4)` `memory usage: 4.8 KB` 无 `前五行：sepal length (cm)` `sepal width (cm)` `petal length (cm)` `petal width (cm)` 0 5.1 3.5 1.4 0.2 1 4.9 3.0 1.4 0.2 2 4.7 3.2 1.3 0.2 3 4.6 3.1 1.5 0.2 4 5.0 3.6 1.4 0.2 类标签：[0 1 2]

### `Sklearn and Outlier Detection`

[Listing A.3](#appA.xhtml#listA.3) 展示了 `elliptic_envelope.py` 的内容，说明如何在 Sklearn 中使用 `EllipticEnvelope` 类来检测数据集中的异常值。

***LISTING A.3: elliptic_envelope.py***

```python
import numpy as np
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.covariance import EllipticEnvelope

datapoints = [[-1,1], [1,1], [1,-1], [-1,-1], [2,2]]
columns = ["x", "y"]
index = [0,1,2,3,4]
df = pd.DataFrame(np.array(datapoints),columns=columns,index=index)

# display datapoints in a scatterplot:
plt.scatter(df["x"], df["y"], color = "r")
plt.grid()

data = df[['x', 'y']].values

# the contamination parameter defines the proportion of values
# that will be identified as outliers:
model1 = EllipticEnvelope(contamination = 0.1)
model1.fit(data)

# new data for prediction:
pred_data = [[3,3], [1.5,1.5], [-2,-2], [-3,-3]]
new_data = np.array(pred_data)

#print("new_data[:,0]:", new_data[:,0])
#print("new_data[:,1]:", new_data[:,1])

# display new datapoints in a scatterplot:
plt.scatter(new_data[:,0], new_data[:,1], s=100, color = "b")

# predict on new data:
pred1 = model1.predict(new_data)

# negative values are outliers:
print("negative predicted values are outliers:")
print(pred1)

for i in range(new_data.shape[0]):
    print("new_data[",i,"] = ",new_data[i],"is an outlier:",pred1[i]==-1)
```

[Listing A.3](#appA.xhtml#listA.3) 以多个 import 语句开头，然后初始化变量 `datapoints`，将 2D 点数组赋值，用于定义 Pandas 数据框 `df`。

随后展示了异常点的散点图（红色），并创建 `model1` 实例，调用其 `fit()` 方法对 `datapoints` 进行训练。

接着初始化 `pred_data`，包含一组新数据，用于判断是否为异常值。将 `pred_data` 加入散点图（蓝色），随后调用 `model1.predict()` 对新数据进行预测，结果存入 `pred1`。最后通过循环遍历 `pred1`，值为 -1 表示异常。运行 [Listing A.3](#appA.xhtml#listA.3) 可看到以下输出：

negative predicted values are outliers: [-1  1 -1 -1] new_data[ 0 ] =  [3. 3.] is an outlier: True new_data[ 1 ] =  [1.5 1.5] is an outlier: False new_data[ 2 ] =  [-2. -2.] is an outlier: True 

取消注释 [Listing A.3](#appA.xhtml#listA.3) 中的最后一段代码后，你会看到初始数据点以红色显示，测试点以蓝色显示。

