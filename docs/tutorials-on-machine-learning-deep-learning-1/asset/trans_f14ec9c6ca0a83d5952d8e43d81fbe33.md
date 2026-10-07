

```python
customers = dataset.iloc[:, 1].values
```

```python
# 创建因变量
is_fraud = np.zeros(len(dataset)) # 创建一个长度为 690 的全零向量
for i in range(len(dataset)):
    if dataset.iloc[i, 0] in fraudDs:
        is_fraud[i]=1
```

```python
# 创建 ANN 模型
from sklearn.preprocessing import StandardScaler
# 因变量不需要进行缩放：分类变量，0 和 1
st_x = StandardScaler()
customers = st_x.fit_transform(customers) # 将 "X_train" 替换为 "customers"
```

# 创建 ANN 模型

```python
# 1. 导入 keras 库和包
# 从 tensorflow import
import keras as tf
from keras.models import Sequential
from keras.layers import Dense
```

```python
# 2. 初始化 ANN
ann_classifier = Sequential()

# 3. 添加“输入层”和“隐藏层”
ann_classifier.add(Dense(units=6, kernel_initializer="uniform", activation="relu", input_dim=11))
ann_classifier.add(Dense(units=2, kernel_initializer="uniform", activation="relu", input_dim=15))
```

```python
# 4. 添加第二个“隐藏层”
ann_classifier.add(Dense(units=6))
```

```python
# 5. 添加“输出层”
ann_classifier.add(Dense(units=1, kernel_initializer="uniform", activation="sigmoid"))
```

```python
# 6. 编译 ANN
ann_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

```python
# 7. 训练模型：将 ANN 拟合训练批大小和轮次
ann_classifier.fit(customers, is_fraud, batch_size=1, epochs=2)
```

# 第 3 部分：预测

```python
# 预测概率
y_prd = ann_classifier.predict(customers)
```

```python
# 合并列以添加 customer_id
y_prd = np.concatenate((dataset.iloc[:, 0:1], y_prd), axis=1)
```

```python
# 排序技巧
y_prd = y_prd[y_prd[:, 1].argsort()] # y_prd[:,1] 选择 y_prd 的第二列
```

```python
# python prctc_mega_Hybrid_ANN.py
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_457_0.png)

# 未排序的 Customer_id & 概率

# 排序后的 Customer_id & 概率

| | | |
|---|---|---|
| 0 | 15776156 | 0.058177352 |
| 1 | 15739548 | 0.060367847 |
| 2 | 15662854 | 0.024292883 |
| 3 | 15687688 | 0.068480803 |
| 4 | 15571750 | 0.067501665 |
| 5 | 15571121 | 0.058102984 |
| 6 | 15726466 | 0.057620336 |
| 7 | 15660390 | 0.024332384 |
| 8 | 15663942 | 0.053759243 |
| 9 | 15638610 | 0.051363118 |
| 10 | 15644446 | 0.019739063 |
| 11 | 15585892 | 0.021267581 |

| | | |
|---|---|---|
| 391 | 15704581 | 0.057776818 |
| 392 | 15578722 | 0.057845513 |
| 393 | 15571221 | 0.058102984 |
| 394 | 15615176 | 0.058177352 |
| 395 | 15745804 | 0.058026234 |
| 396 | 15694666 | 0.058236211 |
| 397 | 15708714 | 0.058270538 |
| 398 | 15788224 | 0.058438948 |
| 399 | 15672357 | 0.058352033 |
| 400 | 15790625 | 0.0585831 |
| 401 | 15723884 | 0.0587722 |
| 402 | 15786539 | 0.0590314 |

