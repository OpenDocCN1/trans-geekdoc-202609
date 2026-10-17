
Listing A.1 starts with several import statements and then initializes the variable `iris` with the Iris dataset. Next, a loop displays the `keys` in `dataset`, followed by another loop that displays the feature names.

The next portion of Listing A.1 initializes the variable `X` with the feature values in columns 2 and 3, and then initializes the variable `y` with the values of the `target` column. Now launch the code in Listing A.1 and you will see the following output (truncated to save space):

```
Pandas df1: iris keys: data target target_names DESCR feature_names filename iris feature names: sepal length (cm) sepal width (cm) petal length (cm) petal width (cm) Class labels: [0 1 2] target: [ 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0]
```

、思习惯、思考方法, and it is *hard to forget.*

```
if (condVar > someVal) {console.log("xxx")}
```

```
IRIS 特征名称：`sepal length (cm)` `sepal width (cm)` `petal length (cm)` `petal width (cm)` 行数：150 列数：4 行和列数：(`150`, 4) 元素总数：600 IRIS 详情：`<class 'pandas.core.frame.DataFrame'>` `RangeIndex: 150 entries, 0 to 149` 数据列（共 4 列）：`sepal length (cm)` 150 个非空 float64 `sepal width (cm)` 150 个非空 float64 `petal length (cm)` 150 个非空 float64 `petal width (cm)` 150 个非空 float64 `dtypes: float64(4)` `memory usage: 4.8 KB` 无 `前五行：sepal length (cm)` `sepal width (cm)` `petal length (cm)` `petal width (cm)` 0 5.1 3.5 1.4 0.2 1 4.9 3.0 1.4 0.2 2 4.7 3.2 1.3 0.2 3 4.6 3.1 1.5 0.2 4 5.0 3.6 1.4 0.2 类标签：[0 1 2]
```

### `Sklearn and Outlier Detection`

Listing A.3 展示了 `elliptic_envelope.py` 的内容，说明如何在 Sklearn 中使用 `EllipticEnvelope` 类来检测数据集中的异常值。

***LISTING A.3: elliptic_envelope.py***

```python

```
